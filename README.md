Notes on using the [Raspberry Pi Debug
Probe](https://www.raspberrypi.com/documentation/microcontrollers/debug-probe.html)
for flashing and debugging ARM processors via SWD.

Raspberry Pi Debug Probe schematic:
    <https://datasheets.raspberrypi.com/debug/raspberry-pi-debug-probe-schematics.pdf>


# Connectors


## Raspberry Pi Debug Probe

The Raspberry Pi Debug Probe uses a compact 3-pin "SH"
connector.

Debug Probe datasheet incl connector:
    <https://datasheets.raspberrypi.com/debug/debug-connector-specification.pdf>


## ARM JTAG/SWD Interface

The standard [ARM debug
interface](https://developer.arm.com/documentation/101636/0100/Debug-and-Trace/JTAG-SWD-Interface)
uses a 2x5 1.27 mm pitch (high density) connector, e.g. HAB-VCR-010-LF.


## Bridging the gap

To connect the Debug Probe to the ARM connector i use the [Olimex ARM JTAG
adapter board](https://www.olimex.com/Products/ARM/JTAG/ARM-JTAG-20-10/).

* use the "SH to 3 male pins" cable of the Debug Probe
* connect to the 2x10 2.54 mm pitch connector of the ARM JTAG adapter board
* Black to any of pins 4, 6, 8, 10, or 12
* Orange (SWDCLK) to pin 9 on the adapter
* Yellow (SWDDIO) to pin 7 on the adapter


# Software

Needs probe-rs 0.26 or newer.
