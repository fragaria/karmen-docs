# Připojení vlastního Octoprintu do Karmen Cloudu

Pokud máte vlastní zařízení s Octoprintem, můžete ho do Karmen Cloudu připojit také.

Níže je uveden návod, jakým způsobem nainstalovat Octoprint a další potřebné knihovny k tomu, aby vaše vlastní zařízení komunikovalo s [Karmen Cloudem](https://next.karmen.tech/).

!> Tento návod je ve stavu "work in progress", což znamená, že ještě není zcela dokončen. Nicméně, uvedený postup je funkční a zkušenější uživatelé by měli být schopni dle tohoto návodu postupovat.

## Přepoklad

Tento návod předpokládá, že:

- Instalace zařízení probíhá od začátku, tj. od čisté instalace Octoprintu. Pokud máte již Octoprint nainstalovaný
a nějakým způsobem nakonfigurovaný, nemusí být uvedený postup funkční.
- Zvládnete nainstalovat na Raspberry systém Octopi/Octoprint.
- Umíte se na zařízení s Octoprintem připojit přes SSH a spouštět v terminálu příkazy.

## Instalace Octoprintu

Začněte tím, že na své zařízení (Raspberry Zero W, Zero 2 W, 3, 4) nainstalujte aktuální verzi Octoprintu, jak je uvedeno na stránce: https://octoprint.org/download/

## Nastavení Wifi

Při instalaci Octoprintu nastavte WIFI, aby bylo možné se na zařízení připojit přes SSH. Jak nastavit Wifi je popsáno v návodu instalace Octoprintu: https://octoprint.org/download/.

## Připojte se na zařízení přes SSH

Spusťte zařízení a připojte se na něj přes SSH - jak nastavit SSH je opět uvedeno v návodu https://octoprint.org/download/.

## Instalace potřebných komponent na zařízení

Nyní byste měli být přihlášeni na zařízení přes SSH. Připravili jsme instalační skript, který nainstaluje vše potřebné. Přdedpokládáme, že všechny níže uvedené příkazy
budete spouštět přímo v terminálu (SSH) na zařízení.

#### Stažení instalačního skriptu

`wget https://raw.githubusercontent.com/fragaria/karmen-gists/main/karmen-pill-init.script`

#### Spuštění instalačního skriptu

?> Pokud by Vás zajímalo, co je přesně součástí instalace, koukněte se na Github: https://github.com/fragaria/karmen-gists/blob/main/karmen-pill-init.script

Během instalace budou provedeny tyto operace:

- proběhne aktualizace systému s Octoprintem
- dojde k instalaci "[karmen websocket proxy](https://github.com/fragaria/websocket-proxy)", což je knihovna starající se o zabezpečenou komunikaci mezi Karmen Cloudem a Octoprintem
- vložení klíče zařízení
- instaluje se "Karmen Pill Led" plugin do Octoprintu, který se stará o rozsvícení/zhasnutí LED světla na Karmen Pillu (pokud LED nemáte, tak to nevadí)
- nastavení větší kvality obrazu z Raspberry kamery, než je výchozí nastavení (pokud kameru nemáte, tak to nevadí)
- úprava výchozího nastavení Octoprintu

Pro spuštění instalace, spusťte na zařízení následující příkaz:

`sudo bash ./karmen-pill-init.script`

Během instalace budete vyzváni k zadání "Karmen klíče (Your Karmen key:)". Tento klíč je unikátní textový řetězec, který slouží k identifikaci zařízení a provázání s Vaším Karmen Cloud účtem. Klíč získáte po přihlášení do Karmen Cloudu na stránce nastavení: https://next.karmen.tech/settings/account - hledejte tlačítko "Create new Device Key" - po kliknutí na toto tlačítko se Vám zobrazí klíč, který zkopírujte a po vyzvání zadejte do SSH terminálu.

!> Karmen Key s nikým nesdílejte. Je to unikátní kód, kterým se zařízení identifikuje na serveru.

### Přidání zařízení do Karmen

Pokud se Vám úšpěšně podařilo spustit instalační skript, tak by mělo být zařízení připravené k přidání do Karmen Cloudu. Pro přidání budete potřebovat dva klíče, které byly během instalace uloženy na SD kartu zařízení do souboru `/boot/KARMEN_KEYS.TXT`. Obsah tohoto souboru si můžete zobrazit přes SSH terminál příkazem `cat /boot/KARMEN_KEYS.TXT` nebo zařízení vypněte, vyndejte z něj SD kartu a obsah souboru `KARMEN_KEYS.TXT` přečtěte v počítači.

Nové zařízení do Karmen Cloudu přidáte po přihlášení na této stránce: https://next.karmen.tech/settings/printers. Klikněte na tlačítko "Add Printer". Zobrazí se Vám formulář, do kterého vyplňte:

`Printer name`: zadejte "libovolný" název pro tiskárnu, například "moje tiskárna :-)"
`Code from the Pill configuration wizard`: zkopírujte hodnotu `DEVICE KEY` z `KARMEN_KEYS.TXT`
`Octoprint API Key`: zkopírujte hodnotu `OCTOPRINT API KEY` z `KARMEN_KEYS.TXT`

Po vyplnění hodnot klikněte na "Save". Nyní se ujistěte, že je zařízení s Octoprintem zapnuté a v Karmen Cloudu přejděte na seznam Vašich tiskáren a vyčkejte, než se spustí Octoprint a připojí ke Karmen Cloudu.

## Přístupové údaje

Uvedený instalační skript nastaví automaticky zabezpečení do Octoprintu. Pokud byste se na Octoprint připojovali v lokální síti přes webový prohlížeč, tak výchozí jméno uživatele je `karmen` a heslo `karmen`. Doporučujeme si toto výchozí heslo změnit, zejména pokud je Vaše zařízení připojeno do veřejné Wifi sítě.

# Konec

Pokud jste došli až sem, tak to je skvělá zpráva. Budeme moc rádi za všechny připomínky nebo dotazy. Ozvěte se nám na email karmen@karmen.tech. Děkujeme za zájem i podporu!
