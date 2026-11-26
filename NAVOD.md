# Web Matěj Vojkůvka — návod na úpravy

Web je jeden soubor: **index.html**. Otevřeš ho dvojklikem v prohlížeči.
Úpravy: otevři index.html v Poznámkovém bloku (nebo VS Code), změň text, ulož (Ctrl+S),
v prohlížeči obnov stránku (F5). Nahrání nové verze: v GitHub Desktop **Commit to main** → **Push origin**, Netlify web do minuty aktualizuje sám.

## Pořadí sekcí

1. Úvod — video na pozadí, „Reality na klíč", nacenění zdarma
2. O mně — fotka č. 1
3. Proč zrovna se mnou — 6 důvodů
4. Oranžový pruh — nacenění zdarma
5. Nemovitosti — V nabídce / Prodáno
6. Reference — karusel po třech + formulář na napsání reference
7. Blog — 3 články, „Číst dál" otevře článek v okně
8. Kontakt — fotka č. 2, formulář, Sleduj mě (IG + FB)

## Kde se co mění

Všechen obsah je v bloku `const DATA = { ... }` pod nadpisem `✏️ EDITOVATELNÁ DATA`.

- **Kontakty, jméno, region, sociální sítě, odkaz na GDPR** — nahoře v DATA.
- **Region** — `regionKratky` ("Ostrava a okolí") jde do štítků, `regionDlouhy`
  ("Ostrava, Karviná a celý Moravskoslezský kraj") do delších textů a SEO popisu.
- **Video na pozadí** — ulož jako `assets/video.mp4` a nastav `video: "assets/video.mp4"`.
  Ideálně 1–2 min sestřih prostřihů z inzercí, bez zvuku, ve smyčce.
  Doporučení: do 8 MB, jinak se to na mobilu načítá pomalu.
- **Fotky** — `assets/o-mne-foto.png` (O mně) a `assets/hero-foto.png` (Kontakt).
  Stačí nahradit soubor stejným názvem.
- **Nemovitosti** — `nemovitosti.seznam`. Nová = zkopírovat blok `{ ... },`.
  `stav: "prodej"` = V nabídce, `stav: "prodano"` = Prodáno.
- **Reference** — pole `reference`. Kolik jich tam je, tolik karusel prolistuje.
  ⚠️ Teď jsou ukázkové — nahradit skutečnými.
- **Blog** — momentálně **vypnutý**: v datech je `zobrazit: false`, takže se sekce
  ani odkaz v menu nezobrazí. Až budou články hotové, přepiš na `zobrazit: true`.
  Články jsou v poli `blog.clanky`, celý text se píše do `text` (každý odstavec
  zvlášť v uvozovkách, oddělené čárkou). Zobrazí se po kliknutí na „Číst dál".

## Formuláře — nastavení na Netlify (jednorázově)

Oba formuláře (poptávka i reference) jedou přes **Netlify Forms**. Fungují automaticky,
jakmile je web nahraný na Netlify — nic se neinstaluje. Aby chodily e-maily:

1. V Netlify otevři projekt → **Forms**
2. Uvidíš formuláře `poptavka` a `reference`
3. **Form notifications → Add notification → Email notification**
4. Zadej `matej.vojkuvka@prosperityfs.cz` a ulož

Od té chvíle přijde po každém odeslání e-mail. Zdarma do 100 odeslání měsíčně.

Pozn.: při otevření souboru z disku (bez Netlify) formulář odeslat nejde — v tom případě
se záložně otevře e-mailový klient. To je normální, na ostrém webu se to nestane.

## Jak fungují reference

Klient klikne na **Napsat referenci**, vyplní formulář, Matějovi přijde e-mail.
Matěj text zkontroluje a vloží ho do pole `reference` v DATA. Tím se zveřejní.

Pro Google je to plnohodnotné — vyhledávač hodnotí text, který na stránce je,
ne to, kdo ho tam vložil. Schvalování navíc chrání před spamem.

## Co je pořád jen „na oko"

- **Blog** — články jsou ukázkové, otevírají se v okně na stránce (nemají vlastní URL).
  Až jich bude víc, dá se přidat samostatná stránka pro každý článek (lepší pro Google).

## Další poznámky

- Web má vlastní identitu (grafit + mosazná zlatá, písmo Manrope, monogram MV) —
  na žádost back office nesmí používat logo ani barvy ProsperityFS.
- Fotky nemovitostí se načítají z realitysnami.cz. Pro ostrý provoz je lepší
  je stáhnout do `assets/` a změnit cesty v DATA.
- Nasazení: Netlify napojené na GitHub repozitář (větev `main`), každý push se nasadí automaticky. Vlastní doména `.cz` cca 150–250 Kč/rok.
