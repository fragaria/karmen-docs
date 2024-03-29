<div style="background: #ea272e; color: #fff; padding: 10px; margin-bottom: 50px; font-size: 20px; text-align: center;">
    Tato stránka již není aktualizována. Prosím navštivte aktuální stránky dokumentace:
    <div style="margin: 20px 0 20px 0;">
        <a href="https://karmen.tech/docs/" style="font-weight: bold; color: #fff;">https://karmen.tech/docs/</a>
    </div>
</div>

# Karmen Pill - nastavení

!> Ujistěte se, jakou verzi Karmen Pillu máte. Tento návod je určen pro verzi Pillu s konfiguračním průvodcem.

## Připojení Pillu k Wifi

Připojte Karmen Pill **(A)** k Vašemu počítači pomocí USB kabelu **(B)**. V tuto chvíli není potřeba, aby byl do Pillu připojen napájecí adaptér - napájení zajistí USB z počítače.

!> Pozor, pokud využijete vlastní kabel, dbejte na to, aby umožňoval přenášet data a nebyl pouze nabíjecí.

Pill začne po připojení k počítači modře blikat (cca 30 vteřin po připojení). V tuto chvíli otevřete v internetovém prohlížeči adresu http://169.254.13.1/.

!> <u>Upozornění pro uživatele **Microsoft Windows**:</u><br>
Pokud se Vám stále nenačítá stránka http://169.254.13.1/, tak:<br>
&#8211; nejspíš budete muset dočasně [vypnout firewall](cs/firewall.md)<br>
&#8211; do Windows [doinstalovat USB ovladač](cs/windows.md)

V konfiguračním průvodci zvolte "nastavení wifi", kde vyplňte údaje o Vašem wifi připojení. Po uložení se Vám zobrazí kód zařízení, který si zkopírujte - budete jej potřebovat pro přidání tiskárny.

<borderedImage>![Pill Wifi Wizard](_media/wizzard-wifi-settings.png ":size=300x300")</borderedImage>

!> Pill je možné připojit pouze na wifi 2.4GHz - 5GHz wifi není podporována.

## Přidání Pillu do Karmen Cloudu

### Začněte tím, že připojíte Pill k tiskárně

- zapojte napájecí adaptér **(C)** do zásuvky a druhý konec do Pillu
- propojte Pill s tiskárnou pomocí kabelů **D** a **E**

### Přidejte Pill do Cloudu

?> Tento krok předpokládá, že již máte účet v Karmen Cloudu. Pokud ho nemáte, můžete si ho jednoduše [vytvořit](https://next.karmen.tech/registration/).

Pokud ještě nemáte žádnou tiskárnu, tak po přihlášení uvidíte tlačítko pro přidání tiskárny. Další tiskárny můžete přidávat nebo upravovat v [nastavení](https://next.karmen.tech/settings/printers).

<borderedImage>![Pill Wifi Wizard](_media/cloud-add-first-printer.png ":size=800x300")</borderedImage>

Do formuláře přidání tiskárny vyplňte název tiskárny a kód zařízení (Pillu), který jste si zkopírovali v předchozím kroku, ve kterém jste nastavovali wifi připojení.

!> Pokud jste si kód zařízení/Pillu nezkopírovali, tak si ho můžete zobrazit opětovným připojením Pillu k počítači a na stejné adrese, jako jste [nastavovali wifi připojení](karmen-pill-zaciname?id=připojení-pillu-k-wifi), tak uvidíte i kód Pillu.

<borderedImage>![Pill Wifi Wizard](_media/cloud-create-printer.png ":size=800x300")</borderedImage>

## Spojení Pillu s tiskárnou

Pokud se Vám podařili všechny předchozí kroky, tak v tuto chvíli máte:

- nastavenou wifi v Pillu - tj. Pill je bezpečně připojen do internetu
- máte vytvořen účet v Karmen Cloudu
- do Karmen Cloudu jste si přidali Pill dle jeho kódu

Na [úvodní stránce](https://next.karmen.tech/) Karmen Cloudu byste měli vidět nově přidanou tiskárnu. Kliknutím přejděte na detail tiskárny. Pokud je Pill online (je zapnutý a připojený k internetu), tak uvidíte obraz z kamery. Vedle obrazu z kamery bude tlačítko "Připojit", na které klikněte, čímž dojde k navázání datové komunikace mezi Pillem a tiskárnou.

<borderedImage>![Karmn Cloud - připojení k tiskárně](_media/cloud-connect-printer.png ":size=800x300")</borderedImage>

Ve chvíli, kdy je navázána komunikace mezi Pillem a tiskánou, zobrazí se Vám základní informace o tiskárně a další možnosti jejího ovládání.

<borderedImage>![Karmn Cloud - tiskárna připojena](_media/cloud-printer-connected.png ":size=800x300")</borderedImage>

Nyní můžete tiskárnu začít používat. V menu aplikace klikněte na "tiskové soubory" (Gcodes), kde můžete přidat soubory do tiskové fronty. Případně [koukněte na návod](prusaslicer-gcode-upload), jak je možné posílat tiskové soubory do Karmen přímo z PrusaSliceru.

## Kontakt a podpora

Kdyby cokoliv nevyšlo, ozvěte se na karmen@karmen.tech a s problémem Vám pomůžeme :)
