<div style="background: #ea272e; color: #fff; padding: 10px; margin-bottom: 50px; font-size: 20px; text-align: center;">
    Tato stránka již není aktualizována. Prosím navštivte aktuální stránky dokumentace:
    <div style="margin: 20px 0 20px 0;">
        <a href="https://karmen.tech/docs/" style="font-weight: bold; color: #fff;">https://karmen.tech/docs/</a>
    </div>
</div>

# Karmen Connector - Klipper (Moonracker)

Pokud máte vlastní zařízení s Klipperem, můžete ho do Karmen Cloudu připojit snadno a rychle.

## Předpoklad
- zařízení s Klipperem - Moonracker
- účet na [next.karmen.tech](https://next.karmen.tech)

## Průvodce nastavením krok za krokem
### Přihlášení přes SSH
Přihlaste se do svého zařízení pomocí SSH.  
![Octoprint](_media/klipper-connector/ssh.png ":size=1024")

### Vytvoření klíče zařízení
Klíč získáte po přihlášení do Karmen Cloudu na stránce nastavení: [https://next.karmen.tech/settings/account](https://next.karmen.tech/settings/account)   
Zde hledejte tlačítko "**Vytvořit nový klíč zařízení**"

![Octoprint](_media/klipper-connector/cloud-new-device-key1.png ":size=1024")

### Zkopírování klíče
Po kliknutí na toto tlačítko se Vám vygeneruje klíč, který si zkopírujte, je potřebný pro instalaci přes SSH skript.

![Octoprint](_media/klipper-connector/cloud-new-device-key2.png ":size=1024")

### Spuštění SSH instalačního skriptu
Nyní zadejte do SSH přikaz skládající se ze dvou částí
- Příkaz na spuštění skriptu instalace `curl -s https://raw.githubusercontent.com/fragaria/karmen-gists/main/ws-install.sh | sudo bash -s `  
- Vytvořený klíč zařízení `eyJhbGciOiJIUzI1NiJ9.AToxNjgxMjk1Mjk5NDMxOmtjZjp2MjpvdjllM293bA.p4uQQJPi_YG_y7FR_wkJX8FvaiZ` 

?> V našem ukázkovém přikladu tedy je `curl -s https://raw.githubusercontent.com/fragaria/karmen-gists/main/ws-install.sh | sudo bash -s eyJhbGciOiJIUzI1NiJ9.AToxNjgxMjk1Mjk5NDMxOmtjZjp2MjpvdjllM293bA.p4uQQJPi_YG_y7FR_wkJX8FvaiZ`

![Octoprint](_media/klipper-connector/ssh-script.png ":size=1024")

**Takto připravený skript spustíme**.

### Přidání tiskárny do pracovní skupiny v Karmen
Pokud nemáte ještě přidánu tiskárnu, Karmen Vás k tomu na hlavní stránce [next.karmen.tech](https://next.karmen.tech) vyzve.  
![Octoprint](_media/klipper-connector/workspace-empty.png ":size=1024")

Další tiskárnu přidáte v záložce [Tiskárny](https://next.karmen.tech/printers) stiskem tlačítka **Přidat tiskárnu**.  
![Octoprint](_media/klipper-connector/workspace-one-printer.png ":size=1024")

#### Výběr typu zařízení - Klipper  
V dalším kroku zvolte typ zařízení, v tomto případě **Klipper**.
![Octoprint](_media/klipper-connector/printer-type-klipper.png ":size=1024")

#### A vyplňte několik údajů:  
`Název tiskárny` název, pod kterým se vám tiskárna bude zobrazovat.  
`Device key` klíč zařízení jsme vytvářeli v druhém kroku.  
![Octoprint](_media/klipper-connector/create-new-printer.png ":size=1024")

## Dohledání Karmen klíče zařízení
Device key máte uložen pro Vaše potřeby v Klipperu i do budoucna. Najdete jej v souboru `karmen-key.txt` v sekci **Configuration**.
![Octoprint](_media/klipper-connector/fluid-config.png ":size=1024")

# Kontakt a podpora
Budeme moc rádi za všechny připomínky nebo dotazy. Ozvěte se nám na email [karmen@karmen.tech](mailto:karmen@karmen.tech). Děkujeme za zájem i podporu!
