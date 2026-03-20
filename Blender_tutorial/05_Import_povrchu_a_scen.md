# Lekce 5 – Import stažených povrchů a scén

> **Délka lekce:** cca 60–90 minut
> **Cíl:** Studenti se naučí, kde najít kvalitní bezplatné textury, HDRIs a 3D modely, jak je importovat do Blenderu a správně napojit v Shader Editoru. Společně aplikují PBR texturu na model domečku a importují strom ze Sketchfabu. Poté samostatně pracují na jednom ze tří projektů.

---

## Přehled lekce

| Fáze | Obsah | Čas |
|------|-------|-----|
| 1 | Kde hledat povrchy a assety – přehled zdrojů | 10 min |
| 2 | Import textur do Blenderu – Shader Editor a Principled BSDF | 15 min |
| 3 | Import hotových 3D modelů (.fbx, .obj, .gltf) | 10 min |
| 4 | Append vs Link – import celých scén | 10 min |
| 5 | Společný projekt – PBR textura na domeček + import stromu | 20–30 min |
| 6 | Samostatný projekt (výběr ze 3 zadání) | 15–25 min |
| 7 | Shrnutí a ukázání prací | 5 min |

---

## Fáze 1 – Kde hledat povrchy a assety (10 min)

### Přehled bezplatných zdrojů

| Zdroj | URL | Co nabízí | Licence |
|-------|-----|-----------|---------|
| **Fab (Epic Games / Quixel)** | [fab.com](https://www.fab.com) | Textury, 3D modely, megascany, celé scény | Zdarma s účtem Epic Games |
| **Poly Haven** | [polyhaven.com](https://polyhaven.com) | HDRIs, textury, 3D modely | CC0 (zcela zdarma, bez omezení) |
| **AmbientCG** | [ambientcg.com](https://ambientcg.com) | PBR textury (cihly, dřevo, kámen, kov…) | CC0 (zcela zdarma) |
| **Sketchfab** | [sketchfab.com](https://sketchfab.com) | 3D modely (mnoho zdarma ke stažení) | Různé – vždy zkontrolovat |
| **Textures.com** | [textures.com](https://www.textures.com) | Fotografie textur, PBR mapy | Zdarma omezený počet denně |

### Quixel / Fab (Epic Games)

1. Přejděte na [fab.com](https://www.fab.com)
2. Klikněte **Sign In** → přihlaste se účtem Epic Games (nebo vytvořte nový – zdarma)
3. V horním menu vyberte **Quixel Megascans** nebo hledejte přímo (např. „brick wall", „wood planks")
4. U vybraného assetu klikněte **Add to My Library** (ikona +)
5. Stáhněte textury ve formátu, který potřebujete – typicky **2K** nebo **4K** rozlišení
6. Stažený ZIP rozbalte – uvnitř najdete jednotlivé mapy (Albedo/Base Color, Roughness, Normal, Displacement)

> **Tip pro výuku:** Účty Epic Games je dobré vytvořit předem, aby se studenti nezdržovali registrací během hodiny. Alternativně mohou sdílet jeden učitelský účet pro ukázku.

---

- Hlavní navigace Fab.com
- Kategorie assetů (Megascans, Environment, Characters…)
- Filtr „Free" / „Price: Free"
- Tlačítko přihlášení přes Epic Games

---

### Poly Haven

1. Přejděte na [polyhaven.com](https://polyhaven.com)
2. V horním menu vyberte kategorii: **Textures**, **HDRIs** nebo **Models**
3. Klikněte na vybranou texturu – zobrazí se náhled se všemi mapami
4. Vyberte rozlišení (1K, 2K, 4K) a formát (PNG nebo EXR pro HDRIs)
5. Klikněte **Download** – stáhne se ZIP se všemi mapami

> **Tip pro výuku:** Poly Haven je ideální pro výuku – žádná registrace, žádné omezení, všechno CC0. Doporučuji začít právě zde.

---

- Přehled textur s náhledy (grid view)
- Kategorie textur vlevo (Brick, Wood, Stone, Ground…)
- Filtr rozlišení
- Ukázka jedné otevřené textury s náhledem všech map

---

### AmbientCG

1. Přejděte na [ambientcg.com](https://ambientcg.com)
2. Prohlédněte si kategorie: **Wood**, **Brick**, **Concrete**, **Metal**, **Ground**…
3. Klikněte na texturu → vyberte rozlišení (2K doporučeno)
4. Klikněte **Download** → stáhne se ZIP s mapami (JPG nebo PNG)

> **Tip pro výuku:** AmbientCG má velmi přehledné rozhraní a rychlé stahování. Studenti si zde mohou vybrat texturu pro samostatný projekt.

---

- Náhled textury (např. cihlová zeď nebo dřevěné prkna)
- Jednotlivé mapy vedle sebe: Color, Normal, Roughness, Displacement
- Výběr rozlišení (1K / 2K / 4K / 8K)
- Tlačítko Download

---

### Co je PBR textura a jaké mapy obsahuje

| Mapa | Anglický název | Funkce |
|------|---------------|--------|
| **Base Color** (Albedo) | Diffuse / Color | Základní barva povrchu bez stínů a odlesků |
| **Roughness** | Roughness | Jak drsný/lesklý je povrch (bílá = drsný, černá = lesklý) |
| **Normal** | Normal Map | Simuluje drobné nerovnosti povrchu bez přidání geometrie |
| **Displacement** | Displacement / Height | Skutečně deformuje geometrii podle mapy výšek |
| **Ambient Occlusion** | AO | Jemné stíny v záhybech a spárách (volitelné) |
| **Metallic** | Metallic | Určuje, zda je povrch kovový (bílá = kov, černá = nekov) |

> **Tip pro výuku:** Ukažte studentům rozdíl – zobrazte jednotlivé mapy vedle sebe a vysvětlete, co každá dělá. Normal mapa je „fialová" – to studenty často zaujme.

---

## Fáze 2 – Import textur do Blenderu – Shader Editor (15 min)

### Otevření Shader Editoru

1. V hlavním okně Blenderu přepněte spodní panel na **Shader Editor**:
   - Klikněte na ikonu editoru vlevo dole → vyberte **Shader Editor**
   - Nebo: v horní liště vyberte workspace **Shading** (záložka nahoře)
2. Vyberte objekt, na který chcete texturu aplikovat
3. V Shader Editoru se zobrazí strom materiálu – výchozí je **Principled BSDF** napojený na **Material Output**

---

- Shader Editor ve spodní polovině
- Node Principled BSDF s jeho vstupy (Base Color, Metallic, Roughness…)
- Propojení na Material Output
- Viewport nahoře s vybraným objektem
- Záložka „Shading" workspace zvýrazněná nahoře

---

### Principled BSDF – přehled vstupů

| Vstup na nodu | Kam napojit | Popis |
|---------------|-------------|-------|
| **Base Color** | Image Texture (Color mapa) | Základní barva materiálu |
| **Metallic** | Image Texture (Metallic mapa) | Kovovost povrchu |
| **Roughness** | Image Texture (Roughness mapa) | Drsnost povrchu |
| **Normal** | Normal Map node → Image Texture (Normal mapa) | Drobné nerovnosti |
| **Displacement** | Material Output (Displacement vstup) přes Displacement node | Deformace geometrie |

### Přidání Image Texture nodu

1. V Shader Editoru: **Shift + A → Texture → Image Texture**
2. Na novém nodu klikněte **Open** → najděte staženou mapu (např. `brick_wall_Color.png`)
3. Propojte **Color** výstup do příslušného vstupu na Principled BSDF
4. Opakujte pro každou mapu

### Napojení Base Color mapy

1. **Shift + A → Texture → Image Texture**
2. **Open** → vyberte soubor `*_Color.png` nebo `*_Diffuse.png`
3. Propojte žlutý výstup **Color** → do vstupu **Base Color** na Principled BSDF

### Napojení Roughness mapy

1. **Shift + A → Texture → Image Texture**
2. **Open** → vyberte `*_Roughness.png`
3. **Důležité:** V nodu Image Texture změňte **Color Space** na **Non-Color** (roughness není barva!)
4. Propojte **Color** výstup → vstup **Roughness** na Principled BSDF

### Napojení Normal mapy

1. **Shift + A → Texture → Image Texture**
2. **Open** → vyberte `*_Normal.png` (nebo `*_NormalGL.png`)
3. Změňte **Color Space** na **Non-Color**
4. **Shift + A → Vector → Normal Map** – přidejte node Normal Map
5. Propojte Image Texture **Color** → Normal Map **Color**
6. Propojte Normal Map **Normal** → Principled BSDF **Normal**

> **Pozor:** Blender používá OpenGL formát normálových map. Pokud textura vypadá „obráceně" (vyboulení místo prohlubní), zkuste invertovat zelený kanál nebo hledejte verzi s příponou `_NormalGL`.

---

- Tři Image Texture nody vlevo
- Principled BSDF uprostřed
- Material Output vpravo
- Propojení: žluté čáry (Color), šedé/fialové čáry (Non-Color data)
- U Roughness a Normal nodu: Color Space nastavený na „Non-Color"
- Normal Map node mezi Normal texturou a Principled BSDF

---

### Napojení Displacement mapy

1. **Shift + A → Texture → Image Texture**
2. **Open** → vyberte `*_Displacement.png` (nebo `*_Height.png`)
3. Změňte **Color Space** na **Non-Color**
4. **Shift + A → Vector → Displacement** – přidejte node Displacement
5. Propojte Image Texture **Color** → Displacement **Height**
6. Propojte Displacement **Displacement** → **Material Output** vstup **Displacement** (ne do Principled BSDF!)
7. V Properties panelu → Material → **Settings → Surface → Displacement**: změňte na **Displacement and Bump** nebo **Displacement Only**

> **Tip pro výuku:** Displacement vyžaduje dostatečnou geometrii (subdivize). Pro začátek stačí ukázat princip – skutečný efekt uvidíte až s Subdivision Surface modifikátorem nebo Adaptive Subdivision v Cycles.

---

- Kompletní setup: 4 textury + 2 utility nody (Normal Map, Displacement)
- Principled BSDF uprostřed se všemi napojenými vstupy
- Material Output s napojeným Displacement vstupem
- Barevné rozlišení propojení
- Nastavení Color Space u jednotlivých textur (sRGB vs Non-Color)

---

### Náhled textury ve viewportu

- Přepněte viewport do **Material Preview** režimu: klávesa **Z → Material Preview** nebo ikona koule v pravém horním rohu viewportu (třetí koule zleva)
- Pro plně realistický náhled: přepněte na **Rendered** režim (čtvrtá koule) – vyžaduje nastavený render engine (Cycles nebo EEVEE)

---

- Levá strana: domeček bez textury (šedý materiál)
- Pravá strana: domeček s cihlovou texturou – viditelné detaily z Normal mapy
- Rozdíl v realističnosti – roughness, normály, barva
- Viewport v režimu Material Preview

---

## Fáze 3 – Import hotových 3D modelů (10 min)

### Podporované formáty

| Formát | Přípona | Kdy se používá |
|--------|---------|----------------|
| **FBX** | .fbx | Nejrozšířenější výměnný formát, podporuje materiály, animace, rigging |
| **OBJ** | .obj | Starší formát, jen geometrie + základní materiály (MTL soubor) |
| **glTF / GLB** | .gltf / .glb | Moderní formát, PBR materiály, animace – doporučený pro web |
| **STL** | .stl | Pouze geometrie – pro 3D tisk |
| **DAE (Collada)** | .dae | Starší formát, podporuje animace |
| **Blender** | .blend | Nativní formát – lze importovat přes Append/Link |

### Postup importu

1. **File → Import** → vyberte formát (např. FBX, OBJ, glTF)
2. Najděte stažený soubor na disku
3. Nastavte parametry importu (v levém dolním panelu po importu):
   - **Scale:** Pokud je model obrovský nebo miniaturní, upravte scale (např. 0.01 pro modely z Unrealu)
   - **Forward / Up axis:** Pokud je model otočený, změňte osy (typicky: Forward = -Y, Up = Z)
4. Klikněte **Import**

> **Tip pro výuku:** Nejčastější problém po importu je špatné měřítko. Ukažte studentům, jak použít **S** (scale) a poté **Ctrl + A → Scale** pro aplikování.

---

- Menu File → Import plně rozbalené
- Seznam formátů: FBX, OBJ, glTF 2.0, Alembic, DAE, STL, SVG, USD…
- Zvýrazněné tři nejdůležitější: FBX, OBJ, glTF

---

- Importovaný model ve viewport (strom, postava nebo jiný asset)
- Panel s parametry importu vlevo dole
- Porovnání velikosti s jinými objekty ve scéně (např. domečkem)
- Outliner vpravo nahoře – nové objekty z importu

---

### Kde stahovat 3D modely zdarma

1. **Sketchfab** – vyberte model → klikněte **Download** (u modelů s povoleným stahováním) → vyberte formát (glTF doporučen pro Blender)
2. **Poly Haven** → sekce **Models** → stáhněte ve formátu .blend nebo .gltf
3. **Fab.com** → přidejte do knihovny → stáhněte → formát FBX nebo UASSET (pro FBX vyberte Blender-kompatibilní verzi)
4. **Turbosquid** → některé modely zdarma → registrace nutná

> **Tip pro výuku:** Připravte si předem 2–3 stažené modely (strom, auto, postava) ve formátu glTF nebo FBX, aby studenti nemuseli čekat na stahování.

---

## Fáze 4 – Append vs Link – import celých scén (10 min)

### File → Append

- **Zkopíruje** vybrané objekty/materiály/kolekce z jiného .blend souboru do aktuálního
- Data se stanou součástí vašeho souboru – **nezávislá kopie**
- Změny v původním souboru se **nepromítnou**
- Vhodné pro: jednorázové použití objektů, materiálů

**Postup:**
1. **File → Append**
2. Najděte `.blend` soubor na disku
3. Otevřete složku uvnitř souboru (Object, Material, Collection…)
4. Vyberte, co chcete importovat → **Append**

### File → Link

- **Odkazuje** na data v jiném .blend souboru
- Data zůstávají v původním souboru – **nelze přímo editovat**
- Změny v původním souboru se **automaticky promítnou** při otevření
- Vhodné pro: sdílené assety v týmu, velké projekty

**Postup:**
1. **File → Link**
2. Najděte `.blend` soubor
3. Vyberte kolekci nebo objekt → **Link**

### Srovnání Append vs Link

| Vlastnost | Append | Link |
|-----------|--------|------|
| Data ve vašem souboru | Ano (kopie) | Ne (odkaz) |
| Editovatelné | Ano | Ne (jen přes Library Override) |
| Aktualizace z originálu | Ne | Ano (automaticky) |
| Velikost souboru | Větší | Menší |
| Kdy použít | Jednorázový import | Sdílené assety, týmová práce |

---

- Dialogové okno Append s file browserem
- Otevřený .blend soubor – viditelné vnitřní složky (Collection, Material, Object…)
- Vybraný objekt ke zkopírování
- Tlačítko „Append" vpravo dole

---

- Outliner se dvěma objekty: jeden Append (editovatelný), jeden Link (ikona knihovny/zámku)
- Vizuální rozdíl v ikonách
- Případně: pokus o editaci linkovaného objektu – chybová hláška

---

## Fáze 5 – Společný projekt: PBR textura na domeček + import stromu (20–30 min)

> **Poznámka pro učitele:** Tento projekt navazuje na domeček z Lekce 1. Pokud studenti nemají uložený model, připravte si základní domeček jako .blend soubor k rozdání. Budete potřebovat: staženou PBR texturu cihlové zdi z Poly Haven a stažený model stromu ze Sketchfabu (formát glTF).

### Příprava – stažení materiálů

#### Stažení PBR textury z Poly Haven

1. Otevřete [polyhaven.com/textures](https://polyhaven.com/textures)
2. Vyhledejte **„brick wall"** nebo **„red bricks"**
3. Klikněte na vybranou texturu (např. „red_brick_03")
4. Vyberte rozlišení **2K** a formát **ZIP**
5. Klikněte **Download**
6. Rozbalte stažený ZIP – měli byste mít tyto soubory:
   - `red_brick_03_diff_2k.jpg` (Base Color)
   - `red_brick_03_rough_2k.jpg` (Roughness)
   - `red_brick_03_nor_gl_2k.exr` (Normal – OpenGL)
   - `red_brick_03_disp_2k.png` (Displacement)
   - `red_brick_03_ao_2k.jpg` (Ambient Occlusion)

#### Stažení modelu stromu ze Sketchfabu

1. Otevřete [sketchfab.com](https://sketchfab.com)
2. Vyhledejte **„low poly tree free"**
3. Filtrujte: **Downloadable** → **Free**
4. Vyberte model → klikněte **Download 3D Model**
5. Vyberte formát **glTF** (.gltf nebo .glb)
6. Stáhněte a rozbalte

> **Tip pro výuku:** Stáhněte oba assety předem a dejte je studentům přes sdílený disk / USB / školní síť, aby se nezdržovalo čekáním na stahování.

### Krok 1 – Otevření domečku a přepnutí do Shading workspace

1. Otevřete soubor s domečkem z Lekce 1 (nebo připravený .blend)
2. V horní liště klikněte na záložku **Shading** – přepne se workspace
3. Ve viewportu vyberte tělo domečku (klik)
4. Ve Shader Editoru byste měli vidět výchozí **Principled BSDF** → **Material Output**

> Pokud materiál neexistuje, klikněte v Shader Editoru na **+ New** (tlačítko nahoře)

### Krok 2 – Napojení Base Color (cihlová textura)

1. V Shader Editoru: **Shift + A → Texture → Image Texture**
2. Na nodu klikněte **Open** → najděte `red_brick_03_diff_2k.jpg`
3. Propojte výstup **Color** (žlutý) → vstup **Base Color** na Principled BSDF
4. Přepněte viewport do **Material Preview** (Z → Material Preview)
5. Měli byste vidět cihlovou texturu na domečku!

> **Pozor:** Textura se pravděpodobně bude zobrazovat divně (roztažená, pootočená). To je normální – v příští lekci se naučíme UV unwrapping. Prozatím to stačí jako ukázka.

---

- Domeček s cihlovou texturou (i když neperfektně namapovanou)
- Shader Editor s prvním napojeným nodem
- Viewport v Material Preview režimu
- Image Texture node s načteným souborem

---

### Krok 3 – Napojení Roughness mapy

1. **Shift + A → Texture → Image Texture**
2. **Open** → vyberte `red_brick_03_rough_2k.jpg`
3. **Důležité:** V nodu změňte **Color Space** z „sRGB" na **Non-Color**
4. Propojte **Color** → vstup **Roughness** na Principled BSDF
5. Podívejte se na výsledek – povrch by měl mít přirozenější odlesky (malta mezi cihlami lesklejší, cihly drsnější)

### Krok 4 – Napojení Normal mapy

1. **Shift + A → Texture → Image Texture**
2. **Open** → vyberte `red_brick_03_nor_gl_2k.exr`
3. Změňte **Color Space** na **Non-Color**
4. **Shift + A → Vector → Normal Map** – přidejte utility node
5. Propojte: Image Texture **Color** → Normal Map **Color**
6. Propojte: Normal Map **Normal** → Principled BSDF **Normal**
7. Výsledek: na povrchu jsou vidět drobné nerovnosti cihel a spáry – i když je geometrie rovná!

> **Tip pro výuku:** Nastavte sílu Normal mapy (hodnota **Strength** na Normal Map nodu) – nechte studenty experimentovat s hodnotami 0.5, 1.0, 2.0 a pozorovat rozdíl.

### Krok 5 – Napojení Displacement mapy

1. **Shift + A → Texture → Image Texture**
2. **Open** → vyberte `red_brick_03_disp_2k.png`
3. Změňte **Color Space** na **Non-Color**
4. **Shift + A → Vector → Displacement**
5. Propojte: Image Texture **Color** → Displacement **Height**
6. Propojte: Displacement **Displacement** → **Material Output** vstup **Displacement**
7. V Properties → Material → Settings → Surface → **Displacement**: změňte na **Displacement and Bump**
8. Pro viditelný efekt přidejte **Subdivision Surface** modifikátor (úroveň 3–4) nebo zapněte **Adaptive Subdivision** v Cycles

---

- Kompletní node tree – 4 textury + 2 utility nody
- Přehledné uspořádání zleva doprava
- Color Space nastavení u jednotlivých textur (sRGB vs Non-Color)
- Domeček s plnou PBR texturou ve viewportu
- Viditelný rozdíl oproti verzi jen s Base Color

---

### Krok 6 – Import stromu ze Sketchfabu

1. **File → Import → glTF 2.0 (.glb/.gltf)**
2. Najděte stažený soubor stromu (např. `low_poly_tree.glb`)
3. Klikněte **Import glTF 2.0**
4. Strom se objeví ve scéně – pravděpodobně bude potřeba upravit:
   - **Velikost:** S → upravte měřítko (strom by měl být přiměřeně velký vůči domečku)
   - **Pozice:** G → X / Y → umístěte strom vedle domečku
   - **Rotace:** R → Z → případně otočte
5. Po úpravě aplikujte transformace: **Ctrl + A → All Transforms**

---

- Texturovaný domeček (cihlová zeď s PBR materiálem)
- Importovaný strom s vlastním materiálem (zelené listí, hnědý kmen)
- Přiměřené proporce obou objektů
- Scéna z pěkného úhlu (perspektiva)
- Outliner s objekty: domeček + strom

---

### Hotový společný projekt – shrnutí kroků

| Krok | Co jsme udělali | Nový skill |
|------|----------------|------------|
| 1 | Otevřeli Shading workspace | Orientace v Shader Editoru |
| 2 | Napojili Base Color | Image Texture node, propojení |
| 3 | Napojili Roughness | Color Space: Non-Color |
| 4 | Napojili Normal mapu | Normal Map utility node |
| 5 | Napojili Displacement | Displacement node, Material Output |
| 6 | Importovali strom | File → Import → glTF |

---

## Fáze 6 – Samostatný projekt (15–25 min)

> **Zadání:** Vyberte si jeden z následujících projektů. Využijte znalosti z dnešní lekce – stáhněte texturu z některého z probíraných zdrojů a aplikujte ji v Shader Editoru. Případně importujte hotový model a zkombinujte ho s vlastní tvorbou.

### Projekt A – Keramický hrnek s PBR texturou

**Obtížnost:** ⭐⭐ (střední)

**Co procvičíte:** Stažení PBR textury, napojení všech map v Shader Editoru

**Postup:**
1. Otevřete model hrnku z Lekce 1 (nebo vytvořte rychle nový – válec s dutinou)
2. Přejděte na [ambientcg.com](https://ambientcg.com) a stáhněte texturu keramiky nebo glazovaného povrchu (hledejte „ceramic", „porcelain" nebo „clay")
3. Rozbalte ZIP a otevřete Shader Editor
4. Napojte všechny dostupné mapy:
   - Base Color → Base Color
   - Roughness → Roughness (Non-Color!)
   - Normal → Normal Map → Normal
5. Přepněte do Material Preview a zkontrolujte výsledek
6. **Bonus:** Přidejte druhý materiál pro vnitřek hrnku (jiná barva/textura) – vyberte plochy v Edit Mode → Assign

### Projekt B – Kamenný meč s texturou

**Obtížnost:** ⭐⭐⭐ (těžší)

**Co procvičíte:** PBR textury na složitějším modelu, více materiálů na jednom objektu

**Postup:**
1. Otevřete model meče z Lekce 1 (nebo vymodelujte zjednodušený meč)
2. Stáhněte 2 textury:
   - Kámen/kov pro čepel (hledejte „stone", „metal" nebo „steel" na Poly Haven)
   - Dřevo/kůže pro rukojeť (hledejte „wood", „leather")
3. Vytvořte 2 materiály:
   - Materiál 1: Čepel – napojte kamennou/kovovou PBR texturu
   - Materiál 2: Rukojeť – napojte dřevěnou/koženou texturu
4. V Edit Mode vyberte plochy čepele → přiřaďte Materiál 1
5. Vyberte plochy rukojeti → přiřaďte Materiál 2
6. **Bonus:** Přidejte Metallic mapu pro kovový vzhled čepele

### Projekt C – Malá scéna z importovaných assetů

**Obtížnost:** ⭐⭐ (střední)

**Co procvičíte:** Import více modelů, sestavení scény, Append

**Postup:**
1. Vytvořte rovinu jako podlahu (**Shift + A → Mesh → Plane**, zvětšete **S → 10**)
2. Aplikujte na rovinu travní texturu z Poly Haven (hledejte „grass")
3. Importujte 2–3 modely ze Sketchfabu nebo Poly Haven:
   - Strom (glTF)
   - Kámen nebo keř
   - Lavička, plot nebo jiný doplněk
4. Uspořádejte objekty do smysluplné scény
5. Upravte měřítka a pozice, aby vše sedělo dohromady
6. **Bonus:** Přidejte HDRI osvětlení z Poly Haven (World Properties → Environment Texture → otevřete stažený .hdr soubor)

---

## Fáze 7 – Shrnutí a závěr (5 min)

### Co jsme se dnes naučili

- **Zdroje textur a modelů:** Fab.com, Poly Haven, AmbientCG, Sketchfab
- **PBR textury:** Co jsou jednotlivé mapy (Base Color, Roughness, Normal, Displacement) a k čemu slouží
- **Shader Editor:** Principled BSDF, Image Texture node, Normal Map node, Displacement node
- **Color Space:** Kdy nastavit sRGB (barvy) a kdy Non-Color (data – roughness, normal, displacement)
- **Import modelů:** File → Import (FBX, OBJ, glTF) – nastavení měřítka a os
- **Append vs Link:** Rozdíl mezi kopírováním a odkazováním dat z jiných .blend souborů

### Klávesové zkratky a postupy – tahák

| Akce | Postup |
|------|--------|
| Otevřít Shader Editor | Spodní panel → ikona editoru → Shader Editor |
| Shading workspace | Záložka „Shading" nahoře |
| Přidat node | Shift + A (v Shader Editoru) |
| Image Texture | Shift + A → Texture → Image Texture |
| Normal Map node | Shift + A → Vector → Normal Map |
| Displacement node | Shift + A → Vector → Displacement |
| Material Preview | Z → Material Preview |
| Rendered Preview | Z → Rendered |
| Import modelu | File → Import → formát (FBX / OBJ / glTF) |
| Append z .blend | File → Append → vybrat soubor → Object/Collection |
| Link z .blend | File → Link → vybrat soubor → Object/Collection |
| Nový materiál | Properties → Material → + New |
| Apply transformace | Ctrl + A → All Transforms |

### Nejčastější chyby a řešení

| Problém | Příčina | Řešení |
|---------|---------|--------|
| Textura je růžová/fialová | Soubor textury nenalezen | Znovu načtěte texturu (Open na Image Texture nodu) |
| Roughness/Normal vypadá divně | Špatný Color Space | Změňte na Non-Color |
| Normal mapa je „obrácená" | DirectX vs OpenGL formát | Hledejte verzi NormalGL nebo invertujte zelený kanál |
| Importovaný model je obrovský/miniaturní | Jiné jednotky ve zdrojovém programu | S → upravte měřítko, Ctrl + A → Scale |
| Textura je roztažená | Špatné UV mapování | Řešení v příští lekci (UV Unwrapping) |
| Displacement nefunguje | Málo geometrie / špatné nastavení | Přidejte Subdivision Surface, nastavte Displacement and Bump v Material Settings |
| Linkovaný objekt nelze editovat | Normální chování Linku | Použijte Append místo Link, nebo Library Override |

---

## Poznámky pro učitele

### Příprava před lekcí

- [ ] Stáhnout PBR texturu cihlové zdi z Poly Haven (2K rozlišení, ZIP)
- [ ] Stáhnout model stromu ze Sketchfabu (formát glTF, licence Free)
- [ ] Připravit .blend soubor s domečkem z Lekce 1 (pro studenty, kteří ho nemají)
- [ ] Ověřit přístup na Poly Haven, AmbientCG a Sketchfab ze školní sítě (některé školy blokují)
- [ ] Připravit sdílený disk / USB s předem staženými texturami a modely (záloha pro případ problémů se sítí)
- [ ] Ověřit, že Blender je ve verzi 3.x nebo 4.x (starší verze nemají Principled BSDF v aktuální podobě)

### Tipy pro průběh výuky

- **Tempo:** Fáze 1 (zdroje) projděte rychle – důležité je, aby studenti věděli, kde hledat. Detailní procházení stránek nechte na domácí přípravu.
- **Shader Editor:** Toto je pro mnohé studenty první setkání s node-based editorem. Vysvětlete koncept „uzlů a propojení" jednoduše – jako stavebnice LEGO, kde každý díl dělá jednu věc a propojením vznikne celek.
- **Nejčastější problémy:**
  - Studenti zapomenou změnit Color Space na Non-Color → roughness a normal vypadají špatně
  - Studenti propojí Displacement do Principled BSDF místo do Material Output → nefunguje
  - Studenti nemohou najít staženou texturu na disku → ukažte, kam se ukládají stažené soubory
  - Import modelu je obrovský → ukažte S → 0.01 jako rychlé zmenšení
- **Pokročilejší studenti:** Ať zkusí Projekt C (scéna z importovaných assetů) nebo přidají HDRI osvětlení.
- **Slabší studenti:** Pomozte jim s Projektem A (hrnek) – napojení Base Color a Roughness stačí pro pochopení principu.
- **Internetové připojení:** Pokud je ve škole pomalý internet, mějte vše předem stažené. Stahování textur v celé třídě najednou může zahltit síť.

### Hodnocení samostatného projektu

| Kritérium | Body |
|-----------|------|
| Stažena a aplikována alespoň 1 PBR textura | 3 |
| Správné napojení v Shader Editoru (Base Color + alespoň 1 další mapa) | 3 |
| Správné nastavení Color Space (Non-Color kde patří) | 2 |
| Import modelu nebo použití Append | 1 |
| Přidané vlastní detaily navíc (více materiálů, HDRI, úprava scény) | 1 |
| **Celkem** | **10** |

---

> **Příští lekce:** Lekce 6 – UV Unwrapping a pokročilé mapování textur. Naučíme se, jak správně „rozbalit" 3D model, aby se textury zobrazovaly přesně tam, kde chceme – bez roztahování a deformací.

