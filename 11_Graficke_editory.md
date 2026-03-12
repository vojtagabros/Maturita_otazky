# 11. Grafické editory

> Souvisí s: [[12_Problematika_3D]] | [[13_Virtualni_realita]]

---

## a) Princip vektorové a rastrové grafiky

### Rastrová grafika (Bitmap)
- Obraz je tvořen **mřížkou pixelů (picture elements)** uspořádaných do řádků a sloupců.
- Každý pixel má přiřazenu barvu (RGB hodnoty, 8 bitů na kanál = 16,7 mil. barev; 16 bitů = HDR).
- **Rozlišení:** počet pixelů (šířka × výška). Příklad: 1920 × 1080 (Full HD), 3840 × 2160 (4K UHD).
- **DPI (Dots Per Inch):** hustota pixelů. 72 DPI = obrazovka, 300 DPI = tisk, 600+ DPI = prémiový tisk.
- **Škálování:**
  - Zvětšení → **degradace kvality** (pixelizace) – algoritmy: Nearest Neighbor (hranaté), Bilinear, Bicubic, Lanczos.
  - Zmenšení → ztráta detailů, ale bez artefaktů.
  - **AI upscaling** (Topaz, ESRGAN) – rekonstrukce detailů při zvětšení pomocí neuronových sítí.
- **Alfa kanál (transparence):** 4. kanál (RGBA) definuje průhlednost pixelů (0 = transparentní, 255 = plná barva).
- **Barevné modely:**
  - **RGB:** pro obrazovky (aditivní míchání světla).
  - **CMYK:** pro tisk (subtraktivní míchání inkoustu: Cyan, Magenta, Yellow, Key/Black).
  - **HSL/HSV:** pro intuitivní výběr barev (Hue/Saturation/Lightness).
  - **LAB:** perceptuálně uniformní, standard pro profesionální zpracování barev.

**Vhodné pro:** fotografie, digitální malba, textury, záběry z kamer.

---

### Vektorová grafika
- Obraz je popsán **matematickými objekty** – body, křivky (Bézierovy křivky), tvary, cesty (paths).
- Data = instrukce pro kreslení, ne pixely.
- **Škálování bez ztráty kvality** – obraz je vždy vygenerován pro aktuální rozlišení výstupu.
- Soubory jsou většinou menší než rastrové (pro jednoduché grafiky).
- **Nevýhody:** nevhodná pro fotorealistické obrazy, fotografie – příliš složitá na popis křivkami.
- **Bézierovy křivky:** definovány řídícími body (kotvy + rukojetě) – základ vektorové grafiky.
- **Vhodné pro:** loga, ikony, ilustrace, typografie, technické výkresy, mapy, SVG animace.

### Porovnání

| Vlastnost | Rastrová | Vektorová |
|---|---|---|
| Základ | Pixely | Matematické objekty |
| Škálování | Ztráta kvality | Bez ztráty |
| Fotografie | Ano | Ne |
| Soubory | Větší | Menší (pro jednoduché) |
| Editace | Pixel-by-pixel | Objekty a cesty |
| Příklady | JPEG, PNG, TIFF, PSD | SVG, AI, EPS, CDR |

---

## b) Formáty a SW nástroje

### Rastrové formáty

| Formát | Komprese | Průhlednost | Použití |
|---|---|---|---|
| **JPEG/JPG** | Ztrátová (DCT) | Ne | Fotografie na webu, sdílení |
| **PNG** | Bezztrátová (LZW) | Ano (alfa) | Webová grafika, screenshoty, ikony |
| **WebP** | Ztrátová + bezztrátová | Ano | Moderní web (Google) – nahrazuje JPEG/PNG |
| **AVIF** | Ztrátová (AV1) | Ano | Nejmodernější webový formát, vyšší komprese |
| **GIF** | Bezztrátová, 256 barev | Jednoduchá | Animace, memy |
| **TIFF** | Bezztrátová | Ano | Profesionální tisk, archivace |
| **RAW** | Bezztrátová (syrová data) | — | Fotografie z DSLR/mirrorless |
| **PSD** | Bezztrátová | Ano | Photoshop pracovní formát (vrstvy) |
| **HEIC/HEIF** | Ztrátová (HEVC) | Ano | Apple zařízení, moderní fotoaparáty |

### Vektorové formáty

| Formát | Popis |
|---|---|
| **SVG** | Scalable Vector Graphics – webový standard (XML), animovatelný |
| **AI** | Adobe Illustrator nativní formát |
| **EPS** | Encapsulated PostScript – tiskové workflow |
| **PDF** | Kombinace vektoru i rastru, přenosový formát |
| **CDR** | CorelDRAW nativní formát |

### Softwarové nástroje

**Rastrové editory:**
- **Adobe Photoshop:** průmyslový standard. Retušování fotek, digitální malba, kompoziting, efekty.
- **GIMP (GNU Image Manipulation Program):** open-source alternativa, plnohodnotný, zdarma.
- **Affinity Photo:** cenová alternativa k Photoshopu, jednorázová platba (vs. subscription).
- **Procreate (iPad):** digitální malba, intuitivní, populární mezi ilustrátory.
- **Lightroom / Capture One:** správa a nedestruktivní úprava fotografií (RAW).

**Vektorové editory:**
- **Adobe Illustrator:** průmyslový standard pro vektorovou grafiku. Loga, ilustrace, typografie.
- **Inkscape:** open-source, SVG nativní, zdarma. Dobrá alternativa pro jednodušší projekty.
- **Affinity Designer:** moderní alternativa k Illustratoru, vektorový + rastrový v jednom.
- **CorelDRAW:** populární v tiskárnách a reklamních studiích, zejména v ČR/SR.
- **Figma:** UI/UX design, kolaborativní v prohlížeči, standard pro webdesign a mobilní aplikace.
- **Sketch:** macOS, UI design, populární alternativa Figmy.

---

## c) Příklady použití v praxi

### Grafický design a branding
- Tvorba log, vizuálního stylu firmy (brand identity) – **Illustrator, CorelDRAW**.
- Reklamní materiály: letáky, bannery, billboardy – vektorové + rastrové.
- Obalový design, tiskoviny, knihy – **InDesign** (DTP – Desktop Publishing).

### Webdesign a UI/UX
- Návrh rozhraní aplikací a webů – **Figma** (wireframy, prototypy, design systémy).
- SVG ikony, animované grafiky na web – **Illustrator + SVG export**.
- Optimalizace obrázků pro web (WebP, AVIF) – rychlost načítání.

### Fotografie a retušování
- Retušování fotek, korekce barev, HDR – **Photoshop, Lightroom**.
- Kompoziting – kombinace více fotografií (záběry na green screen, filmová postprodukce).
- AI nástroje: **Adobe Firefly** (generativní AI fill), **Midjourney, DALL-E, Stable Diffusion** – generování obrazu z textu.

### Herní průmysl a 3D grafika
- Texturování 3D modelů – **Photoshop, Substance Painter**.
- Koncept art, environment design.
- Viz [[12_Problematika_3D]] pro 3D modelování.

### Věda a technické aplikace
- Technické výkresy, mapy, infografiky – vektorová grafika.
- Medicínská vizualizace, vědecké ilustrace.

---

## d) Textové a tabulkové editory

### Textové editory (Word Processing)

**Princip:** zpracování textového obsahu s formátováním (fonty, odstavce, styly, tabulky, objekty). Výstup: dokument určený k tisku nebo digitální distribuci.

**WYSIWYG** (What You See Is What You Get) – zobrazení odpovídá výstupu.

**Funkce:**
- Formátování textu (fonty, velikosti, styly – tučné/kurzíva/podtržení).
- Odstavcové styly, automatické nadpisy, obsah dokumentu.
- Práce s obrázky, tabulkami, grafy.
- Revize a sledování změn (track changes) – spolupráce.
- Makra (VBA v Microsoft Office), šablony.
- Exporty: DOCX, PDF, ODT, HTML.

**Příklady:**
- **Microsoft Word:** průmyslový standard, formát DOCX.
- **Google Docs:** cloudový, real-time spolupráce, zdarma.
- **LibreOffice Writer:** open-source, formát ODT, kompatibilní s DOCX.
- **Apple Pages:** macOS/iOS ekosystém.

### Tabulkové procesory (Spreadsheets)

**Princip:** data organizovaná do buněk (mřížka řádků a sloupců). Každá buňka může obsahovat hodnotu, text nebo vzorec. Vzorce odkazují na jiné buňky → automatické přepočítání.

**Funkce:**
- Matematické, statistické, textové, datové a logické funkce (SUMA, PRŮMĚR, SVYHLEDAT/VLOOKUP, KDYŽ/IF, COUNTIF).
- Grafy a vizualizace (sloupcové, čárové, koláčové, scatter plot).
- Kontingenční tabulky (Pivot Tables) – agregace a analýza dat.
- Podmíněné formátování – vizuální zvýraznění dat.
- Makra (VBA, Google Apps Script) – automatizace.
- Power Query (Excel) – ETL pro analytické účely.
- Power Pivot / Power BI integrace – viz [[10_Firemni_IS]].

**Příklady:**
- **Microsoft Excel:** průmyslový standard, pokročilá analytika, Power BI integrace.
- **Google Sheets:** cloudový, kolaborativní, integrace s Google Workspace.
- **LibreOffice Calc:** open-source alternativa.

### DTP – Desktop Publishing
- **Adobe InDesign:** sazba knih, časopisů, katalogů, výročních zpráv.
- **Canva:** online drag-and-drop pro prezentace, sociální sítě, jednoduché grafiky.
- **Microsoft Publisher:** jednodušší DTP pro Windows.

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(3 min)** Rastrová grafika – pixely, DPI, barevné modely (RGB/CMYK), škálování; formáty (JPEG/PNG/WebP)
2. **(2 min)** Vektorová grafika – matematické objekty, Bézierovy křivky, škálování; formáty (SVG, AI)
3. **(1 min)** Srovnání rastr vs. vektor – tabulka
4. **(2 min)** SW nástroje – Photoshop, Illustrator, GIMP, Inkscape, Figma; opensource alternativy
5. **(3 min)** Použití v praxi – branding, webdesign, fotografie, hry; AI generativní nástroje
6. **(2 min)** Textové editory – Word, Google Docs; funkce
7. **(2 min)** Tabulkové procesory – Excel, Google Sheets; vzorce, pivot tables, BI integrace
