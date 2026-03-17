The Temika microscope is a brightfield and epi-fluorescent microscope designed for automated imaging. It combines motorized XY stage motion, motorized focus (`Z`), motorized condenser height, programmable illumination, temperature control, and an optical autofocus system similar in operation to the Nikon PFS.

## Core capabilities

- Imaging modes: brightfield and epi-fluorescence (each with 4 illumination channels)
- Motion axes: motorized `X`, `Y`, `Z`, and condenser
- Stage accessories: interchangeable inserts for cover slides, multiwell plates, and custom sample holders
- Temperature module: controllable from the GUI or through automation
- Autofocus: optical lever with offset and PID-style control parameters

## Optical and illumination specification

The microscope comes with the following illumination channels:

| Channel | Mode | Nominal LED Wavelength | 
|---|---|---|
| Ch0 | Brightfield | 475 nm | 
| Ch1 | Brightfield | 528 nm | 
| Ch2 | Brightfield | 625 nm | 
| Ch3 | Brightfield | 655 nm | 
| Ch4 | Epi | 385 nm | 
| Ch5 | Epi | 475 nm | 
| Ch6 | Epi | 528 nm | 
| Ch7 | Epi | 625 nm | 

The integrated chip LEDs can be changed if required. The microscope is shipped with a single filter cube using notch filters in both the excitation and emission paths.

## Motion and sample handling

| Subsystem | Description | Notes |
|---|---|---|
| XY stage | Motorized stage for sample positioning | Used for manual movement and scripted scans |
| Focus (`Z`) | Motorized objective/sample focus axis | Works with autofocus system |
| Condenser | Motorized condenser height | Can be zeroed relative to focus for repeatable setup |
| Inserts | Cover slide, multiwell plate, and other holders | Confirm insert list and part numbers when available |

## Temperature control

The microscope includes a temperature control module with monitored sensors and controllable power channels. The GUI exposes temperature plots, readback values, and feedback enable controls. Programmatic control is also available through XML commands.

## Autofocus

Temika provides an optical autofocus subsystem that behaves like a hardware lock rather than a software image-sharpness search. 

## Camera
The microscope comes with a Teledyne monochromatic 7.1 MP camera.  Full specification can be found [on the Teledyne site](https://www.teledynevisionsolutions.com/en-gb/products/blackfly-s-usb3/?model=BFS-U3-70S7M-C&segment=iis&vertical=machine+vision). Other cameras with a C-mount adapter can be fitted to the camera port.

## Hardware overview
The system comprises three separate interconnected parts.  A dedicated unix computer provides a user interface and programatic control of the microscope.  The computer is connected via USB cable to a controller unit that provides power to, and feedabck and data back from, the microscope.

### Microscope front view
![Front view of the Temika microscope](assets/images/microscope/front-view.jpg)

### Microscope rear view

![Rear view of the Temika microscope](assets/images/microscope/rear-view.jpg)

### Electronics connections

![Microscope controller back panel](assets/images/microscope/back-panel.jpg)

![Microscope controller front panel](assets/images/microscope/front-panel.jpg)
