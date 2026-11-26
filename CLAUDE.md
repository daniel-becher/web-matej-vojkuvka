# Pokyny pro Claude — web matejvojkuvka.cz

Tento soubor čti na začátku každé práce na webu. Popisuje, jak web funguje a co se nesmí měnit.

## Jak web funguje

- Čistý statický web, žádný build. Hlavní stránka je `index.html`, zásady ochrany osobních údajů jsou v `zasady.html`, obrázky a videa ve složce `assets/`.
- Hosting je Netlify, napojený na tento GitHub repozitář (větev `main`). **Každý push do `main` jde automaticky rovnou na ostrý web.** Nastavení pro Netlify je v `netlify.toml` (publish = ".", bez build příkazu), neměň ho.
- Podrobnější lidský návod je v `NAVOD.md`.

## Kde se mění obsah

- Veškerý obsah je v `index.html` v bloku `const DATA = { ... }` pod komentářem `✏️ EDITOVATELNÁ DATA`.
- Obsah měň **jen v tomto bloku**. HTML, CSS a JavaScript mimo něj neupravuj, pokud o to uživatel výslovně nepožádá.
- Po úpravě zkontroluj, že blok DATA je dál platný JavaScript (čárky mezi položkami, uzavřené uvozovky a závorky). Jedna chybějící čárka rozbije celý web.

## Pravidla, která se nesmí porušit

1. **Žádné logo ani barvy ProsperityFS.** Na žádost back office má web vlastní identitu: grafit + mosazná zlatá, písmo Manrope, monogram MV. Nepřidávej logo PFS, jejich barvy ani firemní grafiku.
2. **Název firmy** se píše přesně `Prosperity Financial Services a.s.` (je v patičce, `paticka` v DATA).
3. **Text o financování neměň.** Položka „Pomoc kupujícím s financováním“ v `naKlic.body` má formulaci schválenou back office (vázaný zástupce, dobrovolnost, žádný vliv na podmínky prodeje). Nepřepisuj ji, nezkracuj ani nepřidávej další sliby o hypotékách či financování.
4. **Videa musí být malá.** `assets/video.mp4` (na šířku) ideálně do ~8–11 MB, `assets/video-mobil.mp4` (na výšku) do ~8 MB, bez zvuku. Větší video před nahráním zmenši (ffmpeg). GitHub nepustí soubor nad 100 MB a velká videa zpomalují web na mobilu.
5. **Formulář** `poptavka` jede přes Netlify Forms. Neměň jeho atributy `name`, `data-netlify`, `netlify-honeypot` ani skryté pole `form-name`, jinak přestanou chodit poptávky e-mailem.

## Nemovitosti

- Jsou v `DATA.nemovitosti.seznam`. Zdroj je profil makléře na realitysnami.cz: https://realitysnami.cz/nasi-makleri/matej-vojkuvka/
- Nová nemovitost = zkopírovat celý blok `{ ... },` a upravit `stav`, `nazev`, `lokalita`, `dispozice`, `plocha`, `cena`, `foto`, `odkaz`.
- `stav: "prodej"` = V nabídce, `stav: "prodano"` = Prodáno. Prodanou nemovitost nemaž, jen přepni stav.
- `foto` a `odkaz` ber přímo z inzerátu na realitysnami.cz. Údaje (cena, plocha, dispozice) nevymýšlej, opiš je z inzerátu.
- Pokud se mění celková hodnota prodejů v `nemovitosti.lead`, nech čísla upravit uživatele, nepočítej je sám bez potvrzení.

## Reference a blog

- Reference v poli `reference` vkládej jen skutečné, od klientů (přijdou e-mailem přes formulář). Nevymýšlej je.
- Blog je vypnutý (`zobrazit: false`). Zapni ho, až budou skutečné články.

## Postup při změně

1. Uprav soubory.
2. Řekni uživateli, co jsi změnil, ať si to může zkontrolovat (otevřít `index.html` v prohlížeči).
3. Uživatel změnu odešle přes GitHub Desktop: **Commit to main** → **Push origin**. Do minuty je na webu.
4. Když se web rozbije: v Netlify → Deploys → klikni na poslední funkční verzi → **Publish deploy**. Web je zpátky během pár vteřin, pak chybu oprav v souborech.
