# Connecting your devices

Printer connection will depend on your 3D printer brand and type. Most printers
come with an **USB interface** that allows you to connect a controller that will handle
the printing instructions and basically remove the need for SD cards to transfer
your gcode files.

!> Karmen currently supports Karmen Pill and OctoPrint. We definitely plan to
extend the list of options and support smart printers in the future, too.

## Connecting Karmen Pill

The easiest option to connect your printer is using our **Karmen Pill**
companion box. See [Getting started with Karmen Pill](pill-getting-started.md) guide that will
lead you through it.

## Connecting OctoPrint-enabled devices

For hobbyists, the de-facto standard for making your 3D printer accessible over the network
is [OctoPrint](https://octoprint.org). Its installation can be greatly
simplified by using a Raspbian-derived image with a pre-configured installation
called [OctoPi](https://github.com/guysoft/OctoPi) that is designed for Raspberry Pi
microcomputers. Of course, in order for things to work, you will need to make sure your
OctoPrint instance is **accessible over the network** and **write down its IP address**. To connect your OctoPrint
device, see [Adding OctoPrint devices](printers.md?id=adding-octoprint-devices) section in the [Managing printers docs](printers.md).

!> OctoPrint is currently supported only when running Karmen on your [own
server](on-premise.md) without the [cloud mode](on-premise.md?id=configuration)
enabled. The reason behind this is *networking*. In order to avoid complicated
settings on you router, the Karmen SaaS needs a special [web socket
proxy](https://github.com/fragaria/websocket-proxy) to be running on the
controller device. We plan to describe how to setup this in near future so that
you will be able to connect your existing devices, too.

