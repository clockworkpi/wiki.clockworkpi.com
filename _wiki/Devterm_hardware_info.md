---
layout: simple
title: Devterm_hardware_info
revisions:
- author: Cuu 
  date: 2024-02-22
  comment: First version
---
The Devterm hardware is highly configurable, offering swappable CPU
cores and an extension module through which any kind of custom device
can be connected.

## Mainboard

**Tech Specs**

- CPI v3.14 uses a compact design, the size is reduced to 95x77mm.
- PMU chip which supports reliable and complete lithium battery charge
  and discharge management
- Integrated 5G-WIFI (802.11ac) + Bluetooth 5.0
- High-gain antenna
- Standard USB-A 2.0 interface x 3 and, an internal contact interface
  for the Keyboard module
- USB-C\* charging port
- TF card (Micro SD card) slot\*\*
- 40 Pins MIPI screen interface
- Micro-HDMI interface
- 3.5 headphone jack, supports microphone input
- Onboard stereo audio power amplifier chip
- 40 Pins GPIOs expansion interface (using standard 0.5mm FPC connector)
- 52 Pins extension module interface (using standard Mini PCI-E
  connector) for the “EXT. module”
- Standard DDR2-SODIMM 200 Pins interface: connects CPI v3.14 to the
  "Core module"

The schematics and related design materials are released under the GPL
v3 license, and you can find them on our
[Github](https://github.com/clockworkpi/DevTerm/blob/main/Schematics/clockwork_Mainboard_V3.14_Schematic.pdf).

## Screen

**Ultrawide 6.8-inch IPS screen**

This ultrawide 6.8-inch IPS screen with a full viewing angle has been
carefully selected for you. Its aspect ratio has reached an astonishing
16:6 (a typical retro-style proportion). The resolution is 1280x480,
which is precisely equal to dual VGA. We hope this screen can bring you
a vintage-feeling, focused, and immersive experience.

### Adjusting Brightness

*from DrRacoon on the [clockwork
forums](https://forum.clockworkpi.com/t/changing-brightness-terminal/7070)*

You can change the brightness of your DevTerm in the terminal. To do so,
just echo a new value into the brightness file which lives @
/sys/class/backlight/backlight@0. In this folder, you’ll find some
useful files, such as: actual_brightness, brightness & max_brightness.

This was tested and accomplished on the DevTerm running raspbian.

**How**

To change brightness, you can change brightness to anything between 0
and 9. 0 being backlight off, and 9 being brightest. The device defaults
to 5.

To change brightness, type in (changing N for brightness 0 thru 9):

`   echo N > /sys/class/backlight/backlight@0/brightness`

**Take Note**

For quicker access to changing brightness, see @guu’s solution for
adjustment via FN keys. Setting brightness to 0 turns off the backlight
and makes the display near impossible to view. This command may require
you to elevate your terminal session to root using su, or

`   sudo bash -c "echo 5 > /sys/class/backlight/backlight@0/brightness"`

#### guu's solution for adjusting brightness

This was made after the CM3 shipped so is not installed by default

`   sudo apt update && sudo apt install devterm-backlight-rpi `
`   sudo reboot`

then we can use FN+\< \> to adjust the backlight

[Source code](https://github.com/cuu/rpi-backlight)

## Battery

We carefully designed the battery holder to make it more compatible with
various 18650 battery sizes: Φ18±0.5mm diameter, 65-69mm length. The
battery module has "Short Circuit and Reverse Polarity Protection"
features, but you are still advised to purchase\* the batteries from a
reliable distributor and install them correctly.

Theoretically, you could use a single 18650 battery to power the system
or replace the batteries one by one even when the system is in use.
These actions can still cause system instability, and we strongly
recommend replacing the batteries after the system is powered down.
Please remove the battery if you do not use the device for a long time.
Please consult the battery supplier for detailed 18650 safe usage rules,
and please strictly follow them.

[Battery
Schematic](https://github.com/clockworkpi/DevTerm/blob/main/Schematics/clockwork_DevTerm_Battery_Schematic.pdf)

## Keyboard

We are very excited to bring you a classical layout keyboard with 67
keys. A physical mini trackball with OK function and three mouse
buttons, the trackball uses four high-sensitivity and high-reliability
designs based on Hall-effect sensors. A set of retro-style gamepad arrow
keys and four buttons included; these eight keys all use independent IO
design to ensure minimal delay in response.

The keyboard central control unit adopts the Arm® Cortex-M3
architecture, which is fully compatible with the Arduino STM32
development environment. A Micro USB-UART programming port allows you to
reprogram and customize the keyboard firmware easily.

The USB POGO Pin on the back of the keyboard is naturally connected to
the mainboard, saving you the tedious operation of cable connection.

The firmware source code, schematic, and related design materials are
released under the GPL v3 license, and you can find them on our
[GitHub](https://github.com/clockworkpi/DevTerm).

​

## Speaker modules