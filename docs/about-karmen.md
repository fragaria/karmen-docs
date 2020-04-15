# What is Karmen?

Karmen is a web service that allows you to manage your 3D printers remotely
and effortlessly. Using it, you will be able to:

* **Manage multiple printers** in a single web interface
* **See how your print is progressing** using live video stream
* **Enqueue print jobs** without ever touching SD cards again
* **Divide your printing workload** to multiple printers
* **Display print history**
* **Perform start-pause-stop** commands on your printers

Each of those features is available anywhere you go. You can connect to Karmen
using your web browser either on your computer or on your mobile device. Karmen,
unlike Octoprint, is fully responsive.

While existing solutions such as [OctoPrint](https://octoprint.org>) excel in
controlling a single printer, multi-printer setup is still an issue and Karmen
is here to fill the gap. Karmen is a perfect fit for a shared makerspaces, small batch
part factories or a public schools that offer multiple printers to various
users.

**Future-proof:** The way Karmen is designed makes future integrations with smart printers
(i.e. those with network connectivity) simple.

**Open-source:** Karmen is fully open-source, the code [lives on GitHub](https://github.com/fragaria/karmen).

**Hosted or on-premise:** You can take advantage of our hosted option if you want the easiest option. You can also install Karmen
on your own server and expose it yourself. See [Installing on-premise](on-premise.md) for more details.

## How does it work? {docsify-ignore}

Karmen works on client-server principle. Indivudal 3D printers are connected to
a network-enabled controllers. Those then connect to Karmen, a cloud service
which provides the management facilities and gives commands to the 3D printers
via the controllers.

![Karmen](_media/karmen-schema.png ':size=600')

Controllers are usually connected to the printers using the USB interface.
However, Karmen design does not enforce a specific controller to be used. Currently,
there are two options:

* **Simple connection using Karmen Pill**

    Karmen comes together with the [Karmen Pill](pill-getting-started.md), a
    plug-n-play device that allows you to get started in a matter of minutes. It
    requires no advanced knowledge of computers and/or networking.

* **Use OctoPrint box**

    Karmen was made with vast numbers of OctoPrint users in mind. If you are in
    possession of one or multiple OctoPrint boxes and would like to connect to Karmen to
    have a single interface to manage them, see [Connecting your
    devices](connecting-your-devices.md#connecting-octoprint-enabled-device).
