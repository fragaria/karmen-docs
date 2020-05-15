# Connecting your devices

Printer connection will depend on your 3D printer brand and type. Most printers
come with an **USB interface** that allows you to connect a controller that will handle
the printing instructions and basically removes the need for SD cards to transfer
your G-code files.

!> Karmen currently supports **Karmen Pill** and **OctoPrint**. We definitely plan to
extend the list of options and support smart printers in the future, too.

## Connecting Karmen Pill

The easiest option to connect your printer is using our **Karmen Pill**
companion box. See [Getting started with Karmen Pill](pill-getting-started.md) guide that will
lead you through it.

## Connecting OctoPrint-enabled devices

For hobbyists, the de-facto standard for making your 3D printer accessible over
the network is the [OctoPrint](https://octoprint.org). Installing it securely
and reliably is not as easy as it might seem (that's why we suggest you might
wanna go with **Karmen Pill** to save you from headaches) and thorough
description of the process is out of scope of this docs site. However, we will
give you few tips anyway to get you started.

OctoPrint installation can be greatly simplified by using a Raspbian-derived
image with a pre-configured installation called
[OctoPi](https://github.com/guysoft/OctoPi) that is designed for Raspberry Pi
microcomputers. See [Adding
OctoPrint devices](printers.md?id=adding-octoprint-devices) section in the
[Managing printers docs](printers.md?id=adding-new-printers) for more details on
how to connect it once you have it up and running.
