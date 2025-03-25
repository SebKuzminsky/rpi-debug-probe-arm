Notes on using the [Raspberry Pi Debug
Probe](https://www.raspberrypi.com/documentation/microcontrollers/debug-probe.html)
for flashing and debugging ARM processors via SWD.

Raspberry Pi Debug Probe schematic:
<https://datasheets.raspberrypi.com/debug/raspberry-pi-debug-probe-schematics.pdf>

Raspberry Pi Debug Probe mechanical drawing:
<https://datasheets.raspberrypi.com/debug/raspberry-pi-debug-probe-mechanical-drawing.pdf>


# Connectors


## Raspberry Pi Debug Probe

The Raspberry Pi Debug Probe uses a compact 3-pin "JST SH" connector.

Debug Probe datasheet incl connector:
    <https://datasheets.raspberrypi.com/debug/debug-connector-specification.pdf>


## ARM JTAG/SWD Interface

The standard [ARM debug
interface](https://developer.arm.com/documentation/101636/0100/Debug-and-Trace/JTAG-SWD-Interface)
uses a 2x5 1.27 mm pitch (high density) connector, e.g. HAB-VCR-010-LF.


## Bridging the gap

To connect the Debug Probe to the ARM connector i use the [Olimex ARM JTAG
adapter board](https://www.olimex.com/Products/ARM/JTAG/ARM-JTAG-20-10/).

Use the "JST SH to 3 male pins" cable that comes with the Debug Probe.
Connect the pins to the 2x10 2.54 mm pitch connector of the ARM JTAG
adapter board:

| Signal | Debug Probe | Olimex ARM JTAG adapter |
| ------ | ----------- | ----------------------- |
| SWDCLK | Orange      | pin 9                   |
| SWDDIO | Yellow      | pin 7                   |
| Ground | Black       | any of pins 4, 6, 8, 10, or 12 |


# Firmware

As of March 2025, Raspberry Pi Debug Probe ships
with old firmware with some known bugs, e.g.
<https://github.com/probe-rs/probe-rs/issues/2950#issuecomment-2613812040>.

The firmware upgrade procedure is:

- Check that it has the old version: `lsusb -v -d 2e8a:000c | grep bcdDevice`

- Download the latest Raspberry Pi Debug Probe `debugprobe.uf2` file
  from here: <https://github.com/raspberrypi/debugprobe/releases/latest>

- Hold the Raspberry Pi Debug Probe "BOOTSEL" button while plugging in the USB.

- Copy the `debugprobe.uf2` file to the Debug Probe.

- Verify the new version: `lsusb -v -d 2e8a:000c | grep bcdDevice`


# Software

Needs probe-rs 0.26 or newer.


# Enclosure

Assemble the enclosure using two M3 heat-set threaded inserts and
two button-head M3 screws.  I prefer to use nylon screws so that the
outside of the enclosure is electrically non-conductive, but the screw
holes are countersunk so that the heads are recessed below the surface,
so you do you.
