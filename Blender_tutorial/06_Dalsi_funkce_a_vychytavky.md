# Lekce 6 – Další funkce a vychytávky (závěrečná lekce)

> **Délka lekce:** cca 60–90 minut
> **Cíl:** Studenti se seznámí s užitečnými addons, naučí se exportovat modely do různých formátů, osvojí si pokročilé zkratky pro rychlejší práci a získají přehled o zdrojích pro další učení. V závěrečném projektu využijí vše, co se naučili v lekcích 1–6.

---

## Přehled lekce

| Fáze | Obsah | Čas |
|------|-------|-----|
| 1 | Kde stahovat modely zdarma | 10 min |
| 2 | Užitečné addons – Node Wrangler, BlenderKit, Bool Tool | 15 min |
| 3 | Zkratky pro rychlejší práci | 10 min |
| 4 | Export – formáty a jejich využití | 10 min |
| 5 | Společný projekt – Node Wrangler + BlenderKit + export | 15–20 min |
| 6 | Samostatný/závěrečný projekt – kompletní mini-scéna | 25–35 min |
| 7 | Shrnutí celého kurzu a tipy na další učení | 5 min |

---

## Fáze 1 – Kde stahovat modely zdarma (10 min)

### Hlavní zdroje 3D modelů

| Zdroj | URL | Popis | Formáty |
|-------|-----|-------|---------|
| **Sketchfab** | [sketchfab.com](https://sketchfab.com) | Tisíce free modelů, filtr „Downloadable" | .blend, .fbx, .obj, .gltf |
| **TurboSquid** | [turbosquid.com](https://www.turbosquid.com) | Profesionální knihovna, filtr „Free" | .fbx, .obj, .max, .blend |
| **BlenderKit** | addon přímo v Blenderu | Materiály, modely, HDR – přímo z Blenderu | .blend (nativní) |
| **Poly Haven** | [polyhaven.com](https://polyhaven.com) | HDRI, textury, modely – vše CC0 (zdarma) | .blend, .fbx, .gltf |
| **Mixamo** | [mixamo.com](https://www.mixamo.com) | Animované postavy a animace | .fbx |
| **Free3D** | [free3d.com](https://free3d.com) | Různé modely s filtrem „Free" | .blend, .obj, .fbx |

### Jak stáhnout model ze Sketchfab

1. Jděte na [sketchfab.com](https://sketchfab.com) a vytvořte si účet (zdarma)
2. V hledání napište, co hledáte (např. „medieval sword")
3. V filtrech zvolte **Downloadable** a **Price: Free**
4. Klikněte na model → **Download 3D Model** → zvolte formát (ideálně **.gltf** nebo **.fbx**)
5. V Blenderu: **File → Import → glTF 2.0** (nebo FBX)

> **Tip pro výuku:** Ukažte studentům naživo, jak stáhnout model ze Sketchfab. Nechte je najít jeden model, který by se hodil do jejich scény. Upozorněte na licenci – většina free modelů na Sketchfab je CC BY (nutno uvést autora).

---

- Vyhledávací pole s dotazem
- Zaškrtnutý filtr „Downloadable" a „Free"
- Náhledy 3D modelů v mřížce
- Informace o licenci u modelů

---

- BlenderKit panel otevřený v pravé části viewportu
- Vyhledávací pole s kategoriemi (Models, Materials, Brushes)
- Náhledy modelů – rozlišení free vs. placené
- Tlačítko pro drag & drop modelu do scény

---

## Fáze 2 – Užitečné addons (15 min)

### Co jsou addons?

Addons (doplňky) rozšiřují funkce Blenderu. Některé jsou již součástí Blenderu (stačí je zapnout), jiné se stahují externě.

**Jak zapnout addon:**
1. **Edit → Preferences → Add-ons**
2. Vyhledejte název addonu
3. Zaškrtněte checkbox vedle názvu
4. Klikněte **Save Preferences** (nebo zapněte auto-save)

---

- Okno Preferences s kartou Add-ons
- Vyhledávací pole s textem „Node Wrangler"
- Zaškrtnutý checkbox u Node Wrangler
- Tlačítko Save Preferences dole

---

### Addon 1 – Node Wrangler (vestavěný)

**Co dělá:** Zrychluje práci v Shader Editoru – automaticky propojuje textury, přidává uzly, umožňuje rychlý náhled.

**Zapnutí:** Edit → Preferences → Add-ons → vyhledat „Node Wrangler" → zaškrtnout

**Nejdůležitější funkce:**

| Zkratka | Funkce | Popis |
|---------|--------|-------|
| **Ctrl + T** | Add Texture Setup | Na vybraný Image Texture uzel automaticky přidá Texture Coordinate + Mapping uzly |
| **Ctrl + Shift + klik** | Viewer Node | Přidá Viewer uzel – uvidíte výstup konkrétního uzlu přímo ve viewportu |
| **Alt + pravý klik + tah** | Cut Links | Přeřízne spoje mezi uzly tažením čáry |
| **Ctrl + Shift + D** | Duplicate with Links | Zduplikuje uzel i se spoji |

> **Tip pro výuku:** Ctrl + T je nejužitečnější zkratka – bez Node Wrangleru musíte Texture Coordinate a Mapping uzly přidávat a propojovat ručně (3 kroky místo jednoho). Ukažte rozdíl naživo.

---

- Shader Editor s Principled BSDF uzlem
- Image Texture uzel s načtenou texturou
- Automaticky přidané uzly Texture Coordinate a Mapping (po Ctrl+T)
- Propojení všech uzlů barevnými čarami (noodles)

---

### Addon 2 – BlenderKit (externí / vestavěný od 3.0+)

**Co dělá:** Knihovna modelů, materiálů, textur a HDR přímo v Blenderu. Stačí vyhledat a přetáhnout do scény.

**Zapnutí:**
1. Edit → Preferences → Add-ons → vyhledat „BlenderKit"
2. Zaškrtnout → vytvořit si účet na [blenderkit.com](https://www.blenderkit.com)
3. Přihlásit se v addonu (API key nebo přihlášení v prohlížeči)

**Použití:**
1. V pravém panelu viewportu (N-panel) se objeví záložka **BlenderKit**
2. Vyhledejte materiál/model (např. „wood floor", „brick wall")
3. **Drag & drop** materiálu přímo na objekt = okamžitě se aplikuje
4. **Drag & drop** modelu do scény = přidá se hotový objekt

---

- Domeček z předchozích lekcí ve viewportu
- BlenderKit panel s výsledky hledání materiálu „brick wall"
- Kurzor přetahující materiál na stěnu domečku
- Výsledek – cihlová textura na části domečku

---

### Addon 3 – Bool Tool (vestavěný)

**Co dělá:** Zjednodušuje Boolean operace – místo přidávání modifikátoru stačí vybrat dva objekty a stisknout zkratku.

**Zapnutí:** Edit → Preferences → Add-ons → vyhledat „Bool Tool" → zaškrtnout

**Použití:**
1. Vyberte **oba objekty** (nejprve „nůž", pak Shift+klik na cílový objekt)
2. **Ctrl + Shift + B** → menu Bool Tool:
   - **Difference** – odřízne (nůž vyřeže díru)
   - **Union** – sloučí oba objekty
   - **Intersect** – ponechá jen průnik
3. Volba **Brush** = nedestruktivní (zůstane jako modifikátor), **Auto** = okamžitá aplikace

---

- Dva objekty před operací (kvádr + válec)
- Menu Bool Tool s možnostmi Difference/Union/Intersect
- Výsledek Difference – kulatá díra v kvádru
- Čistý viewport bez původního válce

---

## Fáze 3 – Zkratky pro rychlejší práci (10 min)

### Pokročilé zkratky, které šetří čas

| Zkratka | Funkce | Vysvětlení |
|---------|--------|------------|
| **Shift + A** | Add menu | Přidá nový objekt/světlo/kameru – nejpoužívanější zkratka vůbec |
| **Ctrl + Z** | Undo (zpět) | Vrátí poslední krok. Funguje víckrát za sebou (až 32 kroků ve výchozím nastavení) |
| **Ctrl + Shift + Z** | Redo (vpřed) | Znovu provede krok, který jste vrátili |
| **. (tečka na numpadu)** | Focus / Zaměření | Zaměří viewport na vybraný objekt – neocenitelné, když se „ztratíte" |
| **H** | Hide (skrýt) | Skryje vybraný objekt – neruší při práci na jiných částech scény |
| **Alt + H** | Unhide (odkrýt) | Odkryje všechny skryté objekty |
| **Shift + H** | Hide Others | Skryje vše **kromě** vybraného objektu |
| **Shift + D** | Duplicate (duplikovat) | Vytvoří kopii vybraného objektu (nezávislou) |
| **Alt + D** | Linked Duplicate | Vytvoří propojenou kopii – změna jednoho změní všechny |
| **Ctrl + J** | Join | Spojí vybrané objekty do jednoho |
| **P** (v Edit Mode) | Separate | Oddělí vybranou geometrii do nového objektu |
| **Ctrl + P** | Parent | Nastaví rodičovský vztah (pohyb rodiče = pohyb potomka) |
| **N** | Toggle N-panel | Zobrazí/skryje boční panel s přesnými hodnotami |
| **T** | Toggle Toolbar | Zobrazí/skryje levý panel s nástroji |
| **Z** | Shading Pie Menu | Rychlé přepínání mezi Wireframe, Solid, Material Preview, Rendered |
| **Numpad 0** | Camera View | Přepne do pohledu kamery |
| **Ctrl + Alt + Numpad 0** | Snap Camera to View | Přesune kameru na aktuální pohled |
| **F12** | Render Image | Spustí render aktuálního snímku |
| **Ctrl + S** | Save | Uloží soubor – **ukládejte často!** |

> **Tip pro výuku:** Vypište 5 nejdůležitějších zkratek na tabuli a nechte studenty je 2 minuty procvičovat. Doporučte: Shift+A, Ctrl+Z, numpad tečka, H/Alt+H, Shift+D. To jsou zkratky, které budou používat v každém projektu.

---

- Add menu (Shift+A) s kategoriemi Mesh, Light, Camera
- Z-pie menu se 4 režimy (Wireframe, Solid, Material Preview, Rendered)
- Příklad skrytého objektu (H) – šedá ikona v Outlineru
- Duplikovaný objekt (Shift+D) vedle originálu

---

## Fáze 4 – Export – formáty a jejich využití (10 min)

### Hlavní exportní formáty

| Formát | Přípona | Využití | Zachovává |
|--------|---------|---------|-----------|
| **FBX** | .fbx | Herní enginy (Unity, Unreal), animace | Geometrii, materiály, animace, rigging |
| **OBJ** | .obj | Univerzální výměna, starší software | Geometrii, UV, materiály (základní) |
| **STL** | .stl | **3D tisk** | Pouze geometrii (bez barev, textur) |
| **glTF / GLB** | .gltf / .glb | **Web**, AR/VR, Sketchfab | Geometrii, materiály (PBR), animace |
| **DAE (Collada)** | .dae | Starší herní enginy, výměna | Geometrii, materiály, animace |
| **USD** | .usd / .usdc | Filmový průmysl, Pixar pipeline | Vše (nejnovější standard) |

### Jak exportovat

1. Vyberte objekt(y) k exportu (nebo exportujte celou scénu)
2. **File → Export → [formát]**
3. V exportním dialogu nastavte:
   - **Selection Only** – exportuje jen vybrané objekty
   - **Apply Modifiers** – aplikuje modifikátory (subdivision apod.)
   - **Scale** – měřítko (důležité pro herní enginy a 3D tisk)
   - **Forward / Up axis** – orientace os (Unity: Forward = -Z, Up = Y)

---

- Menu File → Export s výčtem formátů
- Zvýrazněné 3 nejčastější formáty (FBX, STL, glTF)
- Krátký popisek u každého formátu

---

### Export pro 3D tisk (.stl)

**Důležité nastavení pro 3D tisk:**
1. Objekt musí být **watertight** (vodotěsný) – žádné díry v geometrii
2. **Apply Scale** (Ctrl + A → Scale) před exportem
3. Zkontrolujte jednotky: **Scene Properties → Units → Metric** a nastavte měřítko
4. Export: File → Export → STL → zaškrtněte **Selection Only**
5. Výsledný .stl soubor otevřete v sliceru (Cura, PrusaSlicer)

### Export pro web (.gltf)

**Proč glTF?**
- Otevřený standard podporovaný všemi moderními prohlížeči
- Zachovává PBR materiály, textury, animace
- Dva varianty: **.gltf** (textový + externí soubory) a **.glb** (vše v jednom binárním souboru)

---

- Export dialog s cestou k souboru
- Zaškrtnuté „Selection Only"
- Nastavení měřítka (Scale)
- Volba ASCII/Binary
- Tlačítko Export STL

---

- FBX: plná kvalita s materiály
- STL: pouze geometrie (šedá/bílá)
- glTF: zobrazení ve webovém prohlížeči
- Velikosti souborů pro srovnání (FBX > glTF > STL typicky)

---

## Fáze 5 – Společný projekt: Node Wrangler + BlenderKit + Export (15–20 min)

> **Poznámka pro učitele:** V tomto projektu studenti prakticky využijí addons z fáze 2 a export z fáze 4. Použijte model domečku z lekce 1 – pokud ho studenti nemají, připravte .blend soubor ke stažení.

### Krok 1 – Zapnutí addonů

1. **Edit → Preferences → Add-ons**
2. Vyhledejte a zapněte:
   - **Node Wrangler** (hledejte „Node Wrangler")
   - **BlenderKit** (hledejte „BlenderKit") – pokud je k dispozici
3. Klikněte **Save Preferences**
4. Zavřete Preferences

### Krok 2 – Otevření modelu domečku

1. **File → Open** → otevřete svůj uložený domeček z lekce 1
2. Pokud nemáte, rychle vytvořte kostku se střechou (viz lekce 1, kroky 1–2)
3. Ujistěte se, že jste v **Object Mode**

### Krok 3 – Texturování pomocí BlenderKit

1. V N-panelu (klávesa **N**) otevřete záložku **BlenderKit**
2. V kategorii **Materials** vyhledejte „brick" (cihla)
3. Přetáhněte materiál na stěny domečku
4. Vyhledejte „roof tiles" nebo „wood" a přetáhněte na střechu
5. Vyhledejte „wood door" a přetáhněte na dveře (pokud máte oddělený objekt)

> **Alternativa bez BlenderKit:** Pokud BlenderKit nefunguje (potřeba internet + účet), stáhněte textury z [polyhaven.com/textures](https://polyhaven.com/textures) a aplikujte ručně přes Shader Editor (viz lekce 4).

### Krok 4 – Node Wrangler v praxi

1. Vyberte domeček a otevřete **Shader Editor** (přepněte editor dole nebo Shift + F3)
2. Podívejte se na uzlové zapojení – BlenderKit již vytvořil uzly
3. Přidejte nový Image Texture uzel: **Shift + A → Texture → Image Texture**
4. Načtěte texturu (Open Image → vyberte staženou texturu)
5. Vyberte Image Texture uzel a stiskněte **Ctrl + T**
6. Automaticky se přidají uzly **Texture Coordinate** a **Mapping**
7. Zkuste **Ctrl + Shift + klik** na různé uzly – uvidíte jejich výstup ve viewportu

---

- Domeček s realistickými materiály (cihly, dřevo/tašky)
- Material Preview režim (Z-pie menu viditelné nebo ikona v headeru)
- BlenderKit panel s použitými materiály
- Rozdíl oproti šedému modelu bez materiálů

---

### Krok 5 – Export do FBX

1. Vyberte domeček (klik)
2. **File → Export → FBX (.fbx)**
3. V nastavení exportu:
   - Zaškrtněte **Selected Objects**
   - **Apply Modifiers** = zaškrtnuto
   - **Path Mode** = Copy (a klikněte ikonu krabičky vedle = Embed Textures)
   - Pojmenujte soubor: `domecek_export.fbx`
4. Klikněte **Export FBX**

### Krok 6 – Export do STL (pro 3D tisk)

1. Vyberte domeček
2. **File → Export → Stl (.stl)**
3. Zaškrtněte **Selection Only**
4. Pojmenujte soubor: `domecek_3dtisk.stl`
5. Klikněte **Export STL**

### Krok 7 – Porovnání výsledků

1. **File → Import → FBX** → načtěte zpět `domecek_export.fbx` – materiály by měly být zachovány
2. **File → Import → STL** → načtěte zpět `domecek_3dtisk.stl` – **pouze geometrie, žádné materiály**
3. Porovnejte oba importy vedle sebe – studenti uvidí rozdíl mezi formáty

> **Tip pro výuku:** Toto porovnání je klíčové. Studenti musí pochopit, že STL je „hloupý" formát – jen trojúhelníky, žádné barvy. FBX je „chytrý" – nese materiály, animace, kosti. Každý formát má své místo.

---

- FBX import: plné materiály, textury, barvy
- STL import: šedý model bez materiálů
- Oba modely vedle sebe pro jasné srovnání
- Případně informace o velikosti souborů v Properties

---

## Fáze 6 – Závěrečný projekt: Kompletní mini-scéna (25–35 min)

> **Zadání:** Toto je váš závěrečný projekt celého kurzu (lekce 1–6). Vyberte si jednu ze tří možností a vytvořte kompletní scénu, která ukáže vše, co jste se naučili: modelování, texturování, osvětlení, kamera, rendering a export.

### Společné požadavky pro všechny projekty

| Požadavek | Lekce | Body |
|-----------|-------|------|
| Minimálně 3 vlastní vymodelované objekty | Lekce 1 | 4 |
| Materiály/textury na všech objektech | Lekce 4 | 4 |
| Správné nasvícení scény (min. 2 světla) | Lekce 2 | 3 |
| Nastavená kamera s dobrým záběrem | Lekce 3 | 2 |
| Finální render (F12) v rozlišení min. 1920x1080 | Lekce 3 | 3 |
| Export do FBX nebo glTF | Lekce 6 | 2 |
| Celkový dojem a kreativita | Všechny | 2 |
| **Celkem** | | **20** |

---

### Projekt A – Útulný pokoj (interiér) 🏠

**Obtížnost:** ⭐⭐ (střední)

**Co vytvořit:**
- Místnost (kvádr s odstraněnou jednou stěnou nebo ceiling pro kameru)
- Nábytek: stůl, židle, skříňka nebo postel
- Dekorace: lampa, knihy, hrnek, obraz na stěně, koberec
- Okno s průhledným sklem (shader z lekce 4)

**Tipy:**
1. Místnost: kostka → **S** zvětšit → Edit Mode → smazat horní a jednu boční plochu (kamera uvidí dovnitř)
2. Podlaha: materiál dřevěné podlahy (BlenderKit: „wood floor")
3. Stěny: materiál omítky nebo tapety
4. Osvětlení: Area Light jako hlavní světlo shora + Point Light do lampy
5. Kamera: záběr z rohu místnosti, mírně shora

**Postup (nápověda):**
1. Začněte místností – kostka 5×4×3 m, smažte přední stěnu a strop
2. Přidejte podlahu s dřevěným materiálem
3. Vymodelujte jednoduchý stůl (viz lekce 1 – deska + 4 nohy)
4. Přidejte židli nebo poličku
5. Dekorace: hrnek na stole (válec + Inset + Extrude dovnitř)
6. Lampa: válec (noha) + UV Sphere (stínítko) + Point Light uvnitř
7. Nasvětlete: hlavní Area Light simulující okno, teplé Point Light v lampě
8. Nastavte kameru, render

### Projekt B – Středověká výstava zbraní ⚔️

**Obtížnost:** ⭐⭐⭐ (těžší)

**Co vytvořit:**
- Výstavní stěna nebo stojan (rack) na zbraně
- Minimálně 3 zbraně: meč, sekera, štít (nebo dýka, kopí, palcát)
- Podstavec nebo pódium
- Dramatické nasvícení (spot lights)

**Tipy:**
1. Meč: viz lekce 1, objekt C (čepel + záštita + rukojeť + hlavice)
2. Sekera: kostka → Edit Mode → vertexy přetáhnout do tvaru čepele + válec jako topůrko
3. Štít: UV Sphere → zploštit (S → Y → 0.3) → Boolean pro výřezy nebo Inset pro dekor
4. Kovové materiály: Principled BSDF → Metallic = 1.0, Roughness = 0.2–0.4
5. Dřevo: textura dřeva na rukojeti
6. Osvětlení: tmavé pozadí + Spot Lights mířící na každou zbraň

**Postup (nápověda):**
1. Vytvořte zadní stěnu (kvádr) s tmavým materiálem
2. Přidejte držáky na stěnu (malé kvádry nebo válce)
3. Vymodelujte meč, sekeru a štít
4. Umístěte zbraně na držáky
5. Přidejte podlahu s kamenným materiálem
6. 3 Spot Lights mířící na zbraně (teplá barva, úzký úhel)
7. Kamera: čelní záběr nebo mírně z boku

### Projekt C – Produktová showcase scéna 📦

**Obtížnost:** ⭐⭐ (střední)

**Co vytvořit:**
- Produkt na podstavci (hodinky, parfém, telefon, nebo jakýkoliv předmět)
- Stylový podstavec (válec nebo kvádr se zaoblenými hranami)
- Pozadí (backdrop – zakřivená plocha)
- Studiové osvětlení (3-point lighting z lekce 2)

**Tipy:**
1. Podstavec: válec → Bevel horních hran → lesklý materiál (Metallic = 0.8, Roughness = 0.1)
2. Backdrop: plocha → Edit Mode → zadní hranu Extrude nahoru → Subdivision Surface pro hladké zakřivení
3. Produkt: jednoduchý tvar (válec pro parfém, kvádr pro telefon)
4. 3-point lighting: Key Light (Area, silné), Fill Light (Area, slabší), Rim Light (za objektem)
5. Render: Cycles pro nejlepší kvalitu odlesků

**Postup (nápověda):**
1. Vytvořte backdrop – plocha → extrude zadní hranu nahoru → Subdivision Surface (level 2)
2. Materiál backdrop: čistě bílý nebo jemně šedý (Roughness = 0.8)
3. Podstavec: válec zúžený nahoru, lesklý materiál
4. Produkt: vymodelujte jednoduchý předmět (nebo stáhněte ze Sketchfab)
5. 3-point lighting setup
6. Kamera: mírně shora, mělká hloubka ostrosti (Camera → Depth of Field → F-Stop = 2.8)

---

- Projekt A: útulný pokoj s nábytkem, osvětlením, materiály
- Projekt B: středověké zbraně na tmavé stěně se spot lights
- Projekt C: produkt na podstavci se studiovým osvětlením
- Všechny tři scény vypadají jako finální rendery

---

## Kompletní tahák klávesových zkratek – všechny lekce (1–6)

### Navigace ve viewportu

| Zkratka | Funkce | Lekce |
|---------|--------|-------|
| Prostřední tlačítko myši (držet) | Otáčení pohledu | 1 |
| Shift + prostřední tlačítko | Posun pohledu | 1 |
| Scroll kolečkem | Přiblížení / oddálení | 1 |
| Numpad 1 | Přední pohled | 1 |
| Numpad 3 | Boční pohled | 1 |
| Numpad 7 | Pohled shora | 1 |
| Numpad 5 | Perspektiva / Ortho | 1 |
| Numpad . (tečka) | Zaměření na vybraný objekt | 1 |
| Numpad 0 | Pohled kamery | 3 |
| Ctrl + Alt + Numpad 0 | Přesunout kameru na aktuální pohled | 3 |
| Z | Shading Pie Menu (Wireframe/Solid/Material/Rendered) | 6 |
| N | Toggle N-panel (boční panel) | 6 |
| T | Toggle Toolbar (levý panel) | 6 |

### Transformace (Object Mode i Edit Mode)

| Zkratka | Funkce | Lekce |
|---------|--------|-------|
| G | Grab / Posun | 1 |
| R | Rotate / Otočení | 1 |
| S | Scale / Změna velikosti | 1 |
| X / Y / Z (po G/R/S) | Omezení na osu | 1 |
| Shift + X/Y/Z (po G/R/S) | Omezení na rovinu (všechno kromě dané osy) | 1 |
| Enter | Potvrzení | 1 |
| Esc / pravý klik | Zrušení | 1 |
| Ctrl + A | Apply (Scale/Rotation/Location) | 1 |

### Režimy a výběr

| Zkratka | Funkce | Lekce |
|---------|--------|-------|
| Tab | Přepnutí Object / Edit Mode | 1 |
| 1 / 2 / 3 (v Edit Mode) | Vertex / Edge / Face select | 1 |
| A | Vybrat vše | 1 |
| Alt + A | Zrušit výběr | 1 |
| B | Box Select | 1 |
| Alt + klik (na hranu) | Loop Select | 1 |
| Shift + klik | Přidat do výběru | 1 |
| L | Select Linked (vybere propojené) | 1 |
| Ctrl + L | Select Linked (v Object Mode: link data) | 4 |

### Modelování (Edit Mode)

| Zkratka | Funkce | Lekce |
|---------|--------|-------|
| E | Extrude | 1 |
| Alt + E | Extrude menu (Along Normals aj.) | 1 |
| I | Inset Faces | 1 |
| Ctrl + R | Loop Cut | 1 |
| Ctrl + B | Bevel | 1 |
| Ctrl + Shift + B | Vertex Bevel | 1 |
| K | Knife Tool | 1 |
| F | Fill (vyplní plochou) | 1 |
| M | Merge (sloučí vertexy) | 1 |
| P | Separate (oddělí geometrii) | 6 |
| X / Delete | Smazat | 1 |

### Objekty a scéna

| Zkratka | Funkce | Lekce |
|---------|--------|-------|
| Shift + A | Add menu (přidat objekt) | 1 |
| Shift + D | Duplicate (duplikovat) | 6 |
| Alt + D | Linked Duplicate | 6 |
| Ctrl + J | Join (spojit objekty) | 6 |
| H | Hide (skrýt) | 6 |
| Alt + H | Unhide (odkrýt vše) | 6 |
| Shift + H | Hide Others (skrýt ostatní) | 6 |
| Ctrl + P | Parent (nastavit rodiče) | 6 |
| Ctrl + Z | Undo (zpět) | 6 |
| Ctrl + Shift + Z | Redo (vpřed) | 6 |
| Ctrl + S | Save (uložit) | 6 |

### Osvětlení a rendering

| Zkratka | Funkce | Lekce |
|---------|--------|-------|
| Shift + A → Light | Přidání světla | 2 |
| F12 | Render Image | 3 |
| F11 | Zobrazit poslední render | 3 |
| Ctrl + F12 | Render Animation | 3 |

### Shader Editor (materiály)

| Zkratka | Funkce | Lekce |
|---------|--------|-------|
| Shift + A (v Shader Editoru) | Přidat uzel | 4 |
| Ctrl + T (Node Wrangler) | Add Texture Setup (Tex Coord + Mapping) | 6 |
| Ctrl + Shift + klik (NW) | Viewer Node (náhled uzlu) | 6 |
| Alt + pravý klik + tah (NW) | Cut Links (přeříznout spoje) | 6 |

### Bool Tool

| Zkratka | Funkce | Lekce |
|---------|--------|-------|
| Ctrl + Shift + B | Bool Tool menu (Difference/Union/Intersect) | 6 |

---

## Fáze 7 – Shrnutí celého kurzu a tipy na další učení (5 min)

### Co jsme se naučili v 6 lekcích

| Lekce | Téma | Klíčové dovednosti |
|-------|------|---------------------|
| **1** | Základy modelování | Rozhraní, transformace, Edit Mode, Extrude, Bevel, Inset, Loop Cut, Boolean |
| **2** | Světla a scéna | Typy světel (Point, Sun, Spot, Area), 3-point lighting, stíny, HDRI prostředí |
| **3** | Kamera a rendering | Nastavení kamery, kompozice, render enginy (Eevee/Cycles), výstupní formáty |
| **4** | Materiály a textury | Principled BSDF, PBR workflow, UV unwrapping, Shader Editor, procedurální textury |
| **5** | Animace | Keyframes, timeline, Graph Editor, pohyb kamery, interpolace, render animace |
| **6** | Další funkce a vychytávky | Addons, export formáty, zdroje modelů, pokročilé zkratky, závěrečný projekt |

### Co dál? Tipy na YouTube kanály a tutoriály

#### Pro začátečníky

| Kanál / Zdroj | Odkaz | Co nabízí |
|----------------|-------|-----------|
| **Blender Guru** (Andrew Price) | [youtube.com/@blenderguru](https://www.youtube.com/@blenderguru) | Slavný **Donut Tutorial** – nejlepší úvod do Blenderu vůbec. Krok za krokem, skvěle vysvětleno. |
| **Grant Abbitt** | [youtube.com/@grabbitt](https://www.youtube.com/@grabbitt) | Skvělé tutoriály pro úplné začátečníky. Série „Get Good at Blender" a „Low Poly" projekty. |
| **CG Cookie** | [youtube.com/@CGCookie](https://www.youtube.com/@CGCookie) | Strukturované kurzy, od základů po pokročilé. Část zdarma, část placená. |
| **Ducky 3D** | [youtube.com/@TheDucky3D](https://www.youtube.com/@TheDucky3D) | Efektní abstraktní scény, animace, procedurální materiály – inspirace pro pokročilejší. |
| **Default Cube** | [youtube.com/@DefaultCube](https://www.youtube.com/@DefaultCube) | Krátká videa s tipy a triky, jak pracovat rychleji v Blenderu. |

#### Doporučené tutoriály pro první kroky po kurzu

1. **Blender Guru – Donut Tutorial** (cca 10 dílů, zdarma)
   - Kompletní projekt od modelování přes textury po rendering
   - Naučíte se sculpting, particles (sypání posypky), volumetric osvětlení
   - [youtube.com/playlist?list=PLjEaoINr3zgFX8ZsChQVQsuDSjEqdWMAD](https://www.youtube.com/playlist?list=PLjEaoINr3zgFX8ZsChQVQsuDSjEqdWMAD)

2. **Grant Abbitt – Low Poly Well** (1 video, 30 min)
   - Jednoduchý low-poly projekt, ideální po dokončení tohoto kurzu
   - Naučíte se low-poly stylizaci

3. **Grant Abbitt – Complete Beginner Series** (série videí)
   - Systematický průchod všemi základními funkcemi
   - Podobný obsah jako tento kurz, ale s videem

---

- Kanál Blender Guru s Donut Tutorialem
- Kanál Grant Abbitt s beginner tutoriály
- URL adresy obou kanálů
- Náhledy videí jako inspirace

---

### Další zdroje pro učení

| Zdroj | Typ | Odkaz | Popis |
|-------|-----|-------|-------|
| Blender Manual | Dokumentace | [docs.blender.org](https://docs.blender.org) | Oficiální dokumentace – reference pro všechny funkce |
| Blender Artists Forum | Komunita | [blenderartists.org](https://www.blenderartists.org) | Fórum – otázky, WIP, galerie |
| r/blender | Komunita | [reddit.com/r/blender](https://www.reddit.com/r/blender) | Reddit komunita – inspirace, feedback, tipy |
| Blender Stack Exchange | Q&A | [blender.stackexchange.com](https://blender.stackexchange.com) | Otázky a odpovědi – řešení konkrétních problémů |
| Poly Haven | Zdroje | [polyhaven.com](https://polyhaven.com) | HDRI, textury, modely – vše CC0 zdarma |
| AmbientCG | Textury | [ambientcg.com](https://ambientcg.com) | PBR textury zdarma (CC0) |
| Texture Ninja | Textury | [textures.com](https://www.textures.com) | Fotoskeny textur (část zdarma) |

---

## Poznámky pro učitele

### Příprava před lekcí

- [ ] Ověřit, že Node Wrangler addon je dostupný na všech počítačích (je vestavěný, stačí zapnout)
- [ ] Pokud plánujete BlenderKit – ověřit internetové připojení, případně vytvořit sdílený účet pro třídu
- [ ] Alternativa k BlenderKit: stáhnout předem 3–5 PBR textur z Poly Haven (brick, wood, metal, fabric, stone)
- [ ] Připravit .blend soubor s domečkem z lekce 1 pro studenty, kteří ho nemají
- [ ] Připravit referenční obrázky pro závěrečné projekty (rendery z internetu jako inspirace)
- [ ] Ověřit, že studenti mají dostatek místa na disku pro export (FBX může být 10–50 MB s texturami)
- [ ] Vytisknout tahák klávesových zkratek pro každého studenta (viz sekce výše)
- [ ] Připravit hodnotící arch pro závěrečný projekt (20 bodů)

### Tipy pro průběh výuky

- **Fáze 1 (zdroje modelů):** Ukažte na projektoru živou ukázku stažení modelu ze Sketchfab. Nechte studenty zkusit najít jeden model, ale hlídejte čas – je snadné se v tom ztratit.
- **Fáze 2 (addons):** Node Wrangler je klíčový – ujistěte se, že ho všichni zapnuli. BlenderKit je bonus – pokud nefunguje internet, přeskočte a použijte stažené textury.
- **Fáze 3 (zkratky):** Nepokoušejte se naučit všechny najednou. Vyberte 5 nejdůležitějších, zbytek je v taháku k nahlédnutí.
- **Fáze 4 (export):** Nechte každého studenta exportovat alespoň do dvou formátů a porovnat – osobní zkušenost je víc než vysvětlování.
- **Fáze 5 (společný projekt):** Budujte krok po kroku. Počkejte na pomalejší studenty po každém kroku.
- **Fáze 6 (závěrečný projekt):** Pokud nestíháte v jedné hodině – zadejte jako domácí projekt. Studenti mohou pracovat doma (Blender je zdarma).

### Nejčastější problémy v této lekci

| Problém | Řešení |
|---------|--------|
| Node Wrangler nefunguje (Ctrl+T nic nedělá) | Zkontrolujte, že je addon zapnutý v Preferences. Pokud ano, restartujte Blender. |
| BlenderKit se nenačítá | Potřeba internet + přihlášení. Alternativa: ruční textury z Poly Haven. |
| Export FBX bez textur | V export dialogu: Path Mode = Copy + kliknout ikonu „Embed Textures" (krabička). |
| STL je příliš malý/velký v sliceru | Zkontrolujte jednotky v Blenderu (Scene Properties → Units). Apply Scale (Ctrl+A) před exportem. |
| Bool Tool nefunguje | Ověřte, že addon je zapnutý. Objekty musí být mesh (ne křivky). Zkontrolujte topologii. |
| Ctrl+T přidá uzly, ale nejsou propojené | Ujistěte se, že je vybraný Image Texture uzel (ne jiný). Node Wrangler funguje jen na texture uzlech. |

### Hodnocení závěrečného projektu (20 bodů)

> **Poznámka:** Tento projekt je hodnocen přísněji než předchozí, protože pokrývá dovednosti ze všech 6 lekcí.

| Kritérium | Popis | Body |
|-----------|-------|------|
| **Modelování** | Min. 3 vlastní objekty, použití různých nástrojů (Extrude, Bevel, Inset, Loop Cut, Boolean) | 4 |
| **Materiály a textury** | Každý objekt má materiál, rozumné PBR hodnoty, použití textur nebo procedurálních materiálů | 4 |
| **Osvětlení** | Min. 2 světla, smysluplné nasvícení scény, správný kontrast světla a stínu | 3 |
| **Kamera a kompozice** | Dobrý záběr, zajímavý úhel, kamera nastavena správně (rozlišení, ohnisková vzdálenost) | 2 |
| **Render** | Finální render v min. 1920×1080, čistý obraz bez artefaktů (šum u Cycles = zvýšit samples) | 3 |
| **Export** | Funkční export do min. 1 formátu (FBX nebo glTF), soubor jde importovat zpět | 2 |
| **Kreativita a celkový dojem** | Originální nápad, pozornost k detailu, vizuální kvalita scény | 2 |
| **Celkem** | | **20** |

### Stupnice hodnocení

| Body | Známka | Popis |
|------|--------|-------|
| 18–20 | 1 (výborně) | Výjimečná scéna, vše splněno, viditelná kreativita a pozornost k detailu |
| 14–17 | 2 (chvalitebně) | Kvalitní scéna, drobné nedostatky v jedné oblasti |
| 10–13 | 3 (dobře) | Scéna splňuje základní požadavky, ale chybí některé prvky |
| 6–9 | 4 (dostatečně) | Základní scéna, chybí více prvků (osvětlení, materiály nebo export) |
| 0–5 | 5 (nedostatečně) | Scéna neúplná nebo nesplňuje většinu požadavků |

---

## Zdroje a odkazy – souhrn

### Stahování modelů zdarma

- [Sketchfab](https://sketchfab.com) – filtr „Downloadable" + „Free"
- [TurboSquid](https://www.turbosquid.com) – filtr „Free"
- [Poly Haven](https://polyhaven.com) – modely, HDRI, textury (CC0)
- [Free3D](https://free3d.com) – různé free modely
- [Mixamo](https://www.mixamo.com) – animované postavy

### Textury a materiály zdarma

- [Poly Haven / Textures](https://polyhaven.com/textures) – PBR textury, CC0
- [AmbientCG](https://ambientcg.com) – PBR textury, CC0
- [Textures.com](https://www.textures.com) – fotoskeny textur (část free)
- [BlenderKit](https://www.blenderkit.com) – materiály přímo v Blenderu

### HDRI prostředí

- [Poly Haven / HDRIs](https://polyhaven.com/hdris) – stovky HDR map, CC0
- [HDRI Haven](https://hdrihaven.com) (přesměruje na Poly Haven)

### Tutoriály a vzdělávání

- [Blender Guru – YouTube](https://www.youtube.com/@blenderguru) – Donut Tutorial a další
- [Grant Abbitt – YouTube](https://www.youtube.com/@grabbitt) – Beginner series, Low Poly
- [Ducky 3D – YouTube](https://www.youtube.com/@TheDucky3D) – Efektní scény a animace
- [Default Cube – YouTube](https://www.youtube.com/@DefaultCube) – Tipy a triky
- [CG Cookie – YouTube](https://www.youtube.com/@CGCookie) – Strukturované kurzy
- [Blender Manual](https://docs.blender.org) – Oficiální dokumentace

### Komunita

- [Blender Artists Forum](https://www.blenderartists.org) – Fórum pro tvůrce
- [r/blender (Reddit)](https://www.reddit.com/r/blender) – Komunita, feedback, inspirace
- [Blender Stack Exchange](https://blender.stackexchange.com) – Q&A, řešení problémů
- [Blender Discord](https://discord.gg/blender) – Chat komunita

---

> **Gratulujeme k dokončení kurzu!** Nyní máte základy 3D grafiky v Blenderu – modelování, texturování, osvětlení, animace, rendering a export. Blender je nástroj, který se neustále vyvíjí a nabízí nekonečné možnosti. Nejdůležitější rada: **tvořte, experimentujte a nebojte se chyb** – Ctrl+Z vás vždy zachrání. 🎉

