# Software

Temika can also be controlled over TCP by sending XML command fragments directly to the local Temika server. This is the better option for plate scanning, long-running experiments, retries, and workflows that need logic based on data or hardware state.  Any setting or operation available via the GUI can be accessed via an XML command.

## Simple control model

The basic pattern is shown in the full example file [temika_jurij.py](../assets/templates/temika_jurij.py):

1. Open a TCP socket to `127.0.0.1:60000`.
2. Send `<temika>` to open a session.
3. Send XML command fragments.
4. Read replies until the terminator is reached.
5. Send `</temika>` to close the session.

Minimal example:

```python
import socket

sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
sock.connect(("127.0.0.1", 60000))
sock.settimeout(1.0)
sock.recv(1024)

sock.sendall(b"<temika>")
sock.sendall(b'<microscopeone><stepper axis="x"><status></status></stepper></microscopeone>')
reply = sock.recv(1024)
sock.sendall(b"</temika>")
```

This works, but it is fragile unless you add timeout handling, reply validation, and state cleanup.

## A more robust pattern

The more advanced code in [temika_comms.py](../assets/templates/temika_comms.py) is more robust:

- open the TCP connection once and keep it alive
- reconnect when the socket becomes invalid
- clear stale data from the receive buffer before sending a new command
- wait for an expected token such as `Done` or `status`
- abort on timeout
- treat `ERROR` in the reply as a failed command

This communication code can then be re-used by function specific wrappers:

- [stage_controller.py](../assets/templates/stage_controller.py)
- [illumination_controller.py](../assets/templates/illumination_controller.py)
- [focus_controller.py](../assets/templates/focus_controller.py)
- [camera_controller.py](../assets/templates/camera_controller.py)

Each controller builds a small XML fragment for one subsystem and delegates sending and reply handling to a single comms class.

## Example command patterns

### Move the stage

Derived from `stage_controller.py`:

```python
command = (
    '<microscopeone>'
    '<stepper axis="x">'
    '<move_absolute>12000 1000</move_absolute>'
    '<wait_moving_end></wait_moving_end>'
    '</stepper>'
    '</microscopeone>'
)
reply = temika.send_command(command, wait_for="Done")
```

### Enable autofocus

Derived from `focus_controller.py`:

```python
command = (
    '<microscopeone>'
    '<afocus>'
    '<enable>ON</enable>'
    '<wait_lock>0.2 10.3</wait_lock>'
    '</afocus>'
    '</microscopeone>'
)
reply = temika.send_command(command, wait_for="Done")
```

### Set illumination and trigger the camera

Derived from `illumination_controller.py` and `camera_controller.py`:

```python
temika.send_command(
    '<microscopeone><illumination><enable>0x20</enable></illumination></microscopeone>'
)
temika.send_command(
    '<camera name="Genicam FLIR Blackfly S BFS-U3-70S7M 0159F410">'
    '<send_trigger></send_trigger>'
    '</camera>',
    wait_for="Done",
)
```

## Best practice

### Treat every command as fallible

Do not assume motion, autofocus, or camera triggering succeeded just because the socket write succeeded. Check the reply and fail fast on timeout or `ERROR`.

### Wait explicitly for motion and lock

The XML examples repeatedly use `<wait_moving_end></wait_moving_end>` and `<wait_lock>...</wait_lock>`. Keep those waits in software-driven runs as well. Without them, later commands can execute against a still-moving stage or unlocked focus system.

### Keep hardware state transitions visible

When you switch illumination, filter position, autofocus state, or recording state, log it in software. Long unattended runs are much easier to debug when the command sequence is mirrored in human-readable logs.

### Keep a single source of connection handling

`temika_comms.py` centralizes retries, timeout handling, and stale-buffer clearing. This is good practice, even if the implementation is later simplified.

## Common software-side failure modes

| Failure mode | What it looks like | Mitigation |
|---|---|---|
| Socket dropped | No reply or invalid file descriptor | Reconnect and reopen session |
| Stale reply in buffer | Reply appears unrelated to current command | Clear receive buffer before sending |
| Stage command returns no status | Position parse fails or returns `0.0` | Check for `status` token and reject bad replies |
| Autofocus never locks | Wait times out | Disable autofocus, inspect optical path, re-home and retry |
| Camera trigger returns no image | Trigger mode or illumination state wrong | Confirm camera trigger configuration and LED enable bitmask |
