# Nastavení PrusaSliceru s Karmen

Pokud používáte ke slicování [PrusaSlicer](https://www.prusa3d.com/prusaslicer/), určitě Vás bude zajímat,
že můžete posílat své tiskové soubory (Gcodes) z PrusaSliceru přímo do Karmen.

!> Tento návod je vytvořen pro PrusaSlicer ve verzi [2.3.3](https://github.com/prusa3d/PrusaSlicer/releases/tag/version_2.3.3). Pokud máte jinou verzi, některé kroky mohou být odlišné.

> Tip: Karmen umí komunikovat i s dalšími slicery (Cura...). Nastavení je obdobné jako níže - pokud by se Vám to nedařilo, ozvěte se nám.

## Adresa Octoprint serveru

Aby mohl PrusaSlicer nahrávat soubory přímo do Karmen, budeme v dalších částech návodu potřebovat adresu serveru. Adresu serveru si zobrazíte v nastavení Vašeho účtu.

<borderedImage>![Create API token](_media/prusaslicer-octoprint-upload-url.png ":size=600x295")</borderedImage>

## Vytvoření API klíče

Aby mohl PrusaSlicer komunikovat s Karmen (odesílat Gcody), musíte si nejdříve vygenerovat API klíč.
API klíč si vytvoříte v nastavení v Karmen Cloud na stránce [Settings > API tokens](https://next.karmen.tech/settings/api-tokens).

> Tip: Do políčka s názvem klíče zadejte takový text, ze kterého i v budoucnu poznáte, k čemu se daný klíč používá.

<borderedImage>![Create API token](_media/account-create-api-token.png ":size=600x295")</borderedImage>

Následně se zobrazí stránka s klíčem, který budeme potřebovat později.

<borderedImage>![Copy API token](_media/account-copy-api-token.png ":size=600x295")</borderedImage>

> Tip: Zatím si nechejte stránku se zobrazným API klíčem otevřenou - po přechodu na jinou stránku nebo zavření internetového prohlížeče, již nelze klíč znovu zobrazit. Můžete si však případně vytvořit API klíč nový.

## Nastavení PrusaSliceru

V záložce "Printer Settings" klikněte na ikonku nastavení tiskárny:

<borderedImage>![Prusaslicer Print Host Upload Settings 1](_media/prusaslicer-print-host-upload-settings-1.png ":size=600x295")</borderedImage>

V okně s nastavením tiskárny pak zadejte:

- Host Type: ```OctoPrint ```
- Hostname: ```viz "Octoprint Upload Url" v návodu výše ``` - [Adresa Octoprint Serveru](prusaslicer-gcode-upload?id=adresa-octoprint-serveru)
- API Key: ```klíč, který jste si vytvořili v jednom z předchozích kroků``` - [Vytvoření API klíče](prusaslicer-gcode-upload?id=vytvoření-api-klíče)

<borderedImage>![Prusaslicer Print Host Upload Settings 2](_media/prusaslicer-print-host-upload-settings-2.png ":size=600x295")</borderedImage>

> Tip: Pro ověření správné komunikace mezi PrusaSlicerem a Karmen, klikněte v nastavovacím dialogu na tlačítko test.

## Odeslání Gcodu do Karmen

V tuto chvíli byste měli mít nastaven PrusaSlicer tak, že je schopen komunikovat s Karmen. Ve chvíli, kdy máte připraven model pro tisk, tak se v pravém dolním rohu PrusaSliceru objeví nové tlačítko, pro nahrání Gcodu přímo do Karmen.

<borderedImage>![Prusaslicer Send To Karmen Button](_media/prusaslicer-send-to-karmen-button.png ":size=600x295")</borderedImage>


