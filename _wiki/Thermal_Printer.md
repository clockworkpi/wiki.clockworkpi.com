---
layout: simple
title: Thermal_Printer
revisions:
- author: Cuu 
  date: 2024-02-22
  comment: First version
---
## Thermal Printer Components

<figure>
<img src="img/1b657e92d8f8e6320eda52241d138634f269e4a2_2_589x500.png"
title="1b657e92d8f8e6320eda52241d138634f269e4a2_2_589x500.png" />
<figcaption>1b657e92d8f8e6320eda52241d138634f269e4a2_2_589x500.png</figcaption>
</figure>

We provide you a vintage-feeling but practical expansion module - the
thermal printer. It uses a standard 58mm thermal paper and has an
easy-to-load design. With the open-source standard CUPS print driver
provided by the [clockworkOS](clockworkOS "wikilink"), you can print
various monochrome fonts, symbols, graphics, and even complete A4 size
output through collage. You can also buy thermal printing paper\* with
adhesive backing or different colors, plan your work and life, mark key
points, and give notes, anytime, anywhere. The sturdy “input tray”
provides a storage function, allowing you to carry it freely.

The CUPS print driver is released under the GPL v3 license, and you can
find it on our
[GitHub](https://github.com/clockworkpi/DevTerm/tree/main/Code/devterm_thermal_printer_cups).

- Safety reminder: It is recommended to use BPA-free thermal papers.

## Paper Dimensions

The printer uses standard 58 mm thermal paper. [Based on the published
3D
models](https://forum.clockworkpi.com/t/devterm-thermal-paper-size-limit/6896/5),
the maximum diameter for a roll is about 42mm.

## Printer Commands

The following examples are from the [thermal printer driver readme.md on
github](https://github.com/clockworkpi/DevTerm/tree/main/Code/thermal_printer).

### Console commands example

echo "Hello DevTerm" \> /tmp/DEVTERM_PRINTER_IN

echo -e "Hello DevTerm\n\n\n\n\n\n" \> /tmp/DEVTERM_PRINTER_IN

cat file.txt \> /tmp/DEVTERM_PRINTER_IN

ncal -hb \| tee \> /tmp/DEVTERM_PRINTER_IN

### Eos/Pos commands example

**ESC ! n**

set printer font index,n:0-4

`   echo -en "\x1b\x0" > /tmp/DEVTERM_PRINTER_IN`

**DC2 \# n**

n:0-F, set printer printing density

`   echo -en "\x12\x23\x8" > /tmp/DEVTERM_PRINTER_IN`

**DC2 T**

print the test page

`   echo -en "\x12\x54" > /tmp/DEVTERM_PRINTER_IN`

## Thermal Printer Spec Sheet

The printer is a Xiamin liyin MTP02-I. The spec sheet is available on
[github](https://github.com/clockworkpi/DevTerm/blob/main/Schematics/Spec_MTP02-I.pdf).
