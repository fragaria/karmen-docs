# Managing G-codes

Karmen has G-code managent built-in. It allows you to upload new G-codes either
*directly via web browser* or *right from your slicer*. It also serves as the
*G-code library*: the gcode list is searchable and Karmen also reads gcode
metadata like filament type or estimated print time.

G-codes are scoped to [organizations](access.md), each organization has its own
G-code library.

## Uploading gcodes using your slicer

Are you used to sending your G-codes into your printer directly from your slicer
of choice like [PrusaSlicer](https://www.prusa3d.com/prusaslicer/),
[Slic3r](https://slic3r.org/) or [with appropriate Cura
plugin](https://ultimaker.com/software/ultimaker-cura)? You can use your slicer
with Karmen as well, as long as your slicer integrates with
[OctoPrint](https://octoprint.org>).

Karmen mimicks OctoPrint's API that the slicers use. By setting up the address
of the printer in the slicer to `http://<karmen IP
address>/api/octoprint-emulator`, you can send your G-codes directly to Karmen.
You might need to experiment with omitting the `http://` part or adding a `/` to
the end of the address. Every slicer expects a slightly different format.

Instead of the *App key* that you would copy over from OctoPrint, you should
create Karmen [API token](api-tokens.md) that can be safely stored in the Slicer
configuration. Remember that Karmen API tokens are always scoped to a certain
organization and your G-code will be available only there.

In Karmen, you can then easily choose the printer which should handle the job.
Since Karmen has no knowledge of the printer's properties such as filament
material or a heatbed size at the time of this writing, the G-codes cannot be
sent to a printer right away and you always need to go to Karmen to start the
print.

## Uploading new gcodes directly

Besides exporting G-codes from your slicing software, you can of course upload
the G-code files manually using **Upload a G-code** button in the G-code listing.
