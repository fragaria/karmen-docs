# Printing with Karmen

## Starting new prints

What purpose would Karmen have if you couldn't start your *prints* using it? To
start with your first print, make sure you've [uploaded the G-code](old/codes.md) file
you would like to work with.

Then, using the app menu, navigate to G-codes listing to locate your G-code
file. You can use the search bar along with the sorting switch to avoid browsing
through a long list in case you've been using Karmen for some time already. Once
you locate the record you would like to start printing, enqueue the printing
job using the context menu right of the G-code name.

Assuming you have some printers connected, a dialog will be displayed asking you
to select the printer you would like to use. The job will be started once you
confirm your selection.

!> Missing a printer you have registered in the printer selection? Make sure its
connected and inactive. Busy printers won't appear in the list.

## Pausing and resuming ongoing prints

Sometimes, it's necessary to *pause the printer* to fix something we don't like
about current print (i.e. getting rid of a plastic blob that formed on the
heatbed) or merely to pause the job to avoid running out of the filament (in
case of older printers without a filament sensor). In such situation, you can
tell Karmen to pause the print for the printer in question on it's [status
page](old/printers.md?id=displaying-printer-status). Look for the **Pause print**
button under the **Controls** tab and hit it. Once the problem is resolved, you
can simply *resume the print* from the same printer status page you've
previously paused the print on.

## Cancelling prints

An ongoing print can be *cancelled* from the [printer status
page](old/printers.md?id=displaying-printer-status). Before cancelling the print,
make sure it's really what you want as there is no way to resume a print after
it's been cancelled. A confirmation dialog will be displayed to verify your intention.

## Manual controls

Karmen allows you to manually trigger some actions on the printer both during
the print and when it's inactive. Those actions include:

- Toggling the LED lighting of Karmen Pill on/off
- *Moving the printer head (X/Y/Z axes)*
- *Controlling the extrusion: enforce extrusion or retraction of some amount of material*
- *Adjusting current temperature of both the extruder and the heatbed*
- *Toggling the printer head fan on/off*
- *Toggling the printer motors on/off*

You can trigger those actions on the [printer status
page](old/printers.md?id=displaying-printer-status) under **Controls** tab.

?> **Note:** Support for actions written in *italics* is coming soon.
