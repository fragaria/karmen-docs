<div style="background: #ea272e; color: #fff; padding: 10px; margin-bottom: 50px; font-size: 20px; text-align: center;">
    Tato stránka již není aktualizována. Prosím navštivte aktuální stránky dokumentace:
    <div style="margin: 20px 0 20px 0;">
        <a href="https://karmen.tech/docs/" style="font-weight: bold; color: #fff;">https://karmen.tech/docs/</a>
    </div>
</div>

# Často kladené otázky

---

?> **Mohu si do Octoprintu v Pillu doinstalovat další pluginy?**

Ne, v tuto chvíli to není možné. Resp. nedokážeme zaručit, že se přidáním pluginu něco "nerozbije". Pokud přesto zkusíte nějaké pluginy přidat a něco se pokazí, můžete vždy uvést Pill do továrního nastavení a začít znovu.

---

?> **Je možné provést úvodní konfiguraci Pillu přes nějakou Linux Live Distribuci, například Ubuntu?**

Ano, je to možné. Tato varianta se může hodit někomu, kdo si nechce do Windows instalovat USB ovladač - stačí nabootovat linux/Ubuntu z USB a provést úvodní konfiguraci tímto způsobem.

---

?> **Jaký je rozdíl mezi Karmen a vlastním řešením nad Octoprintem?**

- Karmen nabízí lepší zabezpečení a ochranu vašich dat.
- Karmen nabízí vzdálený přístup odkudkoliv a zároveň možnost ovládat v jednom rozhraní více tiskáren.
- I když je softwarová část Karmen zadarmo, nabízíme uživatelům online podporu, průběžné aktualizace a neustále přidáváme nové prvky.
- Karmen je optimalizovaná pro použití na mobilním telefonu.

Karmen Pill je hotové řešení pro školy, firmy i jednotlivce, pokud nechcete nastavovat Octoprint a jiné alternativy.

---

?> **V čem je Karmen bezpečnější než Octoprint?**

Hlavní rozdíl mezi bezpecnosti Octoprintu a Karmen je ten, že v případě Karmen dochází k navázání spojení z Pillu na server (Pill není reálně přístupný z internetu).
V případě standardního Octoprintu dochází k přímému připojení na Octoprint.

---

?> **Je bezpečne používat Cloudové služby?**

Ano, používání cloudových služeb určitě není pro každého. Snažíme se data našich uživatelů maximálně zabezpečit a samozřejmě je s nikým dalším nesdílíme.
Zároveň je Karmen publikována jako opensource, takže pokud ji budete chtít používat, můžete si ji nainstalovat i na svůj počítač nebo server a dle potřeby si vše zabezpečit.

---

?> **Můžu použít jeden Pill na více tiskáren?**

Teoreticky můžete, ale samozřejmě nikoliv v jednu chvíli. Pill potřebuje fyzické spojení s tiskárnou a sledovat může v každou chvíli také jen jednu tiskárnu. Můžete ho mezi tiskárnami střídat nebo si pořídit pro každou tiskránu jeden Pill.

---

?> **Mám vlastní monitoring tisku**

Do Karmen Cloud se můžete připojit a zdarma ho používat, i když máte vlastní zařízení na monitoring tisku. Tady je návod, jak to udělat: https://docs.karmen.tech/#/pripojeni-octoprintu-do-karmen-cloudu

---

?> **Má Ethernet nebo 5 GHz WiFi?**

Pill lze zatím připojit jen přes 2,4 GHz Wifi. Ethernet zatím nenabízí, ale je to jedno z vylepšení, na kterých pracujeme a snad se ho dočkáte v příští verzi.

---

?> **Proč je Karmen Cloud zdarma?**

Karmen jsme vytvořili jako svého druhu “firemní hobby” a bereme jí také jako způsob, jak prostřednictvím open source software přispět komunitě kolem 3D tisku. Jako firmu nás živí jiné věci a nikdy nebylo naším hlavním cílem na Karmen vydělávat.

---

?> **Jaké je rozlišení kamery?**

Rozlišení kamery Pillu je HD.

---

?> **Jak připevnit Pill k tiskárně?**

Podívejte se na držáky, které vyrobili ostatní uživatelé Karmen a vyberte si z nich. Nebo navrhněte vlastní a pošlete nám ho, viz kapitola Návody: https://docs.karmen.tech/#/pripojeni-octoprintu-do-karmen-cloudu

---

?> **Jak na prvotní konfiguraci Karmen Pill po rozbalení?**

Kompletní návod jak postupovat naleznete v kapitole Základy: https://docs.karmen.tech/#/karmen-pill-zaciname

---

?> **Chcete posílat G-cody do Karmen rovnou ze Sliceru?**

Postupujte podle návodu https://docs.karmen.tech/#/cs/prusaslicer-gcode-upload

---

?> **Pill jste připojili, blikal a pak zhasl, ale stránka http://169.254.13.1/ nebo pill.karmen.tech se nenačítá. Při pokusu kontaktovat server vypršel časový limit.**

Pravděpodobně jste Pill připojili k počítači s Windows 10, potom bude potřeba do počítače stáhnout chybějící ovladač, jak na to najdete v návodu: https://docs.karmen.tech/#/windows

---

?> **Nevidíte Porty (COM a LPT) při stahování chybějícího ovladače na WIN 10**

Zkontrolujte, jestli je váš Pill připojený k počítači. Pokud ano, Pill modře bliká a PORTY (COM A LPT) nevidíte, zkontrolujte, jakým kabelem Pill připojujete – kabel musí být schopen přenášet data, ne pouze nabíjet. Ideálně použijte přiložené kabely, které jste dostali spolu s Karmen Pill.

---

?> **Podporuje Karmen Prusa MMU?**

Ne, v tuto chvíli Karmen MMU nepodporuje. V případě tisku z Karmen na Prusa MMU tiskárně, je nutné zvolit výběr filamentu fyzicky na tiskárně.

---
