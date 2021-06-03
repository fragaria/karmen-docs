# Prvotní zapojení Karmen Pill na zařízení s Windows

Pokud používáte zařízení s operačním systémem Windows, bude nejprve nutné stáhnout ovladač, který na tomto operačním systému chybí. 

## Spojení Pillu s počítačem

Začněte tím, že připojíte svůj Pill k počítači dodaným USB kabelem (v případě použití vlastního kabelu dbejte na to, aby použitý kabel uměl přenášet data a nebyl pouze nabíjecí). 
Počkejte než se Pill modře rozsvítí a následně zhasne. 
Potom přejděte na URL pro [stažení ovladače](https://www.catalog.update.microsoft.com/Search.aspx?q=usb%20vid_0525%20pid_a4a2).

<borderedImage>![download-driver-1](_media/download-driver-1.jpg ":size=1200x590")</borderedImage>

Následně se zobrazí stránka pro stažení ovladače. Ovladač stáhněte a zapamatujte si místo, kam ho ukládáte.

<borderedImage>![Copy API token](_media/dowload-driver-3.png ":size=600x295")</borderedImage>

## Instalace ovladače

Klikněte pravým tlačítkem na Start a vyberte ```Správce zařízení```


<borderedImage>![spravce-zarizeni](_media/spravce-zarizeni.png ":size=600x295")</borderedImage>

Pod možností ```Síťové adaptéry``` se podívejte, že nevidíte "USB Ethernet/RNDIS Gadget". To je ovladač, který musíme nainstalovat.

<borderedImage>![sitove-adaptery](_media/sitove-adaptery.png ":size=600x295")</borderedImage>

Nyní rozklinete ```PORTY (COM A LPT)``` a kliknete pravým tlačítkem na ```Sériové zařízení USB``` a dáte aktualizovat.

<borderedImage>![Ports-com-and-lpt-2](_media/Ports-com-and-lpt-2.png ":size=600x295")</borderedImage>




!> Nevidíte PORTY (COM A LPT)? [Podívejte se sem](cs/porty.md).


Potom z nabízených možností zvolíte ```Vyhledat ovladače na mém počítači```.

<borderedImage>![ports-com-and-lpt-3](_media/ports-com-and-lpt-3.png ":size=600x295")</borderedImage>

A pomocí tlačítka ```Procházet``` najdete složku, kam jste stažený ovladač uložili (předtím bude nejspíš potřeba ho rozbalit) 


<borderedImage>![Ports-com-and-lpt-4](_media/Ports-com-and-lpt-4.png ":size=600x295")</borderedImage>

<borderedImage>![porty-com-and-lpt-5](_media/porty-com-and-lpt-5.png ":size=600x295")</borderedImage>

Nyní Pill odpojte a znovu připojte k počítači a ověřte si, že je vidět ```USB Ethernet/RNDIS Gadget``` v ```Síťových adaptérech```.

<borderedImage>![porty-com-and-lpt-6](_media/porty-com-and-lpt-6.png ":size=600x295")</borderedImage>


## Připojení Pillu k Wifi

Potom co se Pill opět rozvítí a následně zhasne přejděte v prohlížeči na stránku [pill.karmen.tech](http://pill.karmen.tech/) a zde nastavíte název pillu, dále potom jméno a heslo Vaší wifi, na kterou se má Pill připojit (použijte wifi 2.4GHz, ne 5GHZ).
V dalším kroku zkopírujete dlouhý kód, který se vam objeví. Budete ho potřebovat pro přidání tiskárny.

!> Stránka pill.karmen.tech se Vám stále nenačítá? Nejspíš budet muset dočasně **vypnout firewall**. [Podívejte se sem](cs/firewall.md).

<borderedImage>![wifi-1](_media/wifi-1.png ":size=1200x590")</borderedImage>


## Spojení Pillu s tiskárnou

Nyní Pill odpojte od počítače a připojte k tiskárně. Zadejte adresu [cloud.karmen.tech] (https://cloud.karmen.tech/) a klikněte na ```add a printer```.

<borderedImage>![printer-1](_media/printer-1.png ":size=1200x590")</borderedImage>

Poté zvolte název tiskárny a vložte kód, který jste zkopirovali v [pill.karmen.tech](http://pill.karmen.tech/).
Nyní můžete připojit Pill k tiskárně, počkejte, až se rozsvítí a zhasne.
Pak stále na [cloud.karmen.tech] (https://cloud.karmen.tech/) v menu ```Printers``` vyberte nově přidanou tiskárnu a rozkliknete ji. Pár minut počkejte a pak zkuste refreshnout stránku. Měli byste vidět obraz na kameře a následující obrazovku. 

<borderedImage>![printer-3](_media/printer-3.png ":size=1200x590")</borderedImage>

Nahoře pod názvem tiskárny uvidíte ```Connect``` klikněte sem a nějakou dobu čekejte (může to trvat i pár minut). Pokud neuvidíte obraz na kameře, zkuste po chvíli refreshnout stránku obraz by se měl objevit. Stav tiskárny by měl být ```Connected and Operational```

<borderedImage>![printer-4](_media/printer-4.png ":size=1200x590")</borderedImage>

!> Pokud obraz stále i po několika refreshích nevidíte a chybí Vám tlačítko CONNECT a obrazovka vypadá i po pár minutách a refreshi jako níže, Pill není připojen na wifi. Zkuste proto zkontrolovat kroky pro připojení na wifi.  

<borderedImage>![printer-2](_media/printer-2.png ":size=1200x590")</borderedImage>


## Kompletní dokumentace Karmen Pill a Cloud

Odkaz na kompletní [návod ke Karmen Pillu a Cloudu a dokumentaci](https://docs.karmen.tech/#/pill-getting-started) najdete zatím pouze v angličtině. 

## Držáky na Pill k tisku

Pokud si budete na Pill chtít pořídit držák, mrkněte do knihovny, kterou vyrobili naši klienti.  

https://www.thingiverse.com/thing:4764591

https://www.thingiverse.com/thing:4267454

https://www.thingiverse.com/thing:4741938

https://www.thingiverse.com/thing:4361559

https://www.thingiverse.com/thing:4342073

## Kontakt

Kdyby cokoliv nevyšlo, ozvěte se na karmen@karmen.tech a s problémem Vám pomůžeme :)