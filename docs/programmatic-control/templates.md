# Templates

Use these as starting points rather than as drop-in production code.

## XML template: single-position capture

```xml
<temika>
  <save>
    <basename>example_capture</basename>
    <append>DATE</append>
  </save>

  <camera name="YOUR_CAMERA_NAME">
    <record>ON</record>
  </camera>

  <microscopeone>
    <stepper axis="x">
      <move_absolute>0 100</move_absolute>
      <wait_moving_end></wait_moving_end>
    </stepper>
    <stepper axis="y">
      <move_absolute>0 100</move_absolute>
      <wait_moving_end></wait_moving_end>
    </stepper>
    <afocus>
      <enable>ON</enable>
      <wait_lock>0.2 10.3</wait_lock>
    </afocus>
    <illumination>
      <enable>0x20</enable>
    </illumination>
  </microscopeone>

  <camera name="YOUR_CAMERA_NAME">
    <genicam>
      <float feature="ExposureTime">10000</float>
    </genicam>
    <send_trigger></send_trigger>
    <record>OFF</record>
  </camera>
</temika>
```

## XML template: repeated time point

```xml
<temika>
  <timestamp>0</timestamp>

  <save>
    <basename>timecourse_t0</basename>
    <append>DATE</append>
  </save>

  <!-- acquisition block here -->

  <sleep timestamp="0">0:05:00</sleep>
</temika>
```

## Python template: simple TCP wrapper

```python
import socket
import time


class SimpleTemika:
    def __init__(self, host="127.0.0.1", port=60000, timeout=2.0):
        self.sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        self.sock.settimeout(timeout)
        self.sock.connect((host, port))
        self.sock.recv(1024)
        self.sock.sendall(b"<temika>")

    def send(self, xml, wait_for=None):
        self.sock.sendall(xml.encode())
        if wait_for is None:
            return None
        data = b""
        deadline = time.time() + 2.0
        while time.time() < deadline:
            part = self.sock.recv(4096)
            if not part:
                break
            data += part
            if wait_for.encode() in data:
                return data.decode(errors="replace")
        raise TimeoutError(f"Did not receive {wait_for!r}")

    def close(self):
        self.sock.sendall(b"</temika>")
        self.sock.close()
```

## Python template: recommended command helpers

```python
def move_axis(temika, axis, position_um, speed_um_s):
    xml = (
        f'<microscopeone><stepper axis="{axis}">'
        f'<move_absolute>{position_um} {speed_um_s}</move_absolute>'
        '<wait_moving_end></wait_moving_end>'
        '</stepper></microscopeone>'
    )
    return temika.send(xml, wait_for="Done")


def set_illumination(temika, enable_mask):
    xml = (
        '<microscopeone><illumination>'
        f'<enable>{enable_mask}</enable>'
        '</illumination></microscopeone>'
    )
    return temika.send(xml)


def trigger_camera(temika, camera_name, exposure_us):
    xml = (
        f'<camera name="{camera_name}"><genicam>'
        f'<float feature="ExposureTime">{exposure_us}</float>'
        '</genicam><send_trigger></send_trigger></camera>'
    )
    return temika.send(xml, wait_for="Done")
```

## Template guidance

- Keep hardware names in configuration, not hard-coded throughout the run logic.
- Put retry and timeout handling in one comms layer.
- Log every motion, autofocus, illumination, and trigger operation.
- For long runs, write metadata alongside image output, not just in terminal logs.
