# Lekce 2 – Nastavení světel a scény

> **Délka lekce:** cca 60–90 minut
> **Cíl:** Studenti se naučí pracovat se světly v Blenderu, porozumí typům světel a jejich vlastnostem, nastaví tříbodové osvětlení, přidají HDRI prostředí a připraví kompletní scénu. Společně nasvítí model domečku z lekce 1 a poté samostatně vytvoří jednu ze tří světelných scén na výběr.

---

## Přehled lekce

| Fáze | Obsah | Čas |
|------|-------|-----|
| 1 | Typy světel v Blenderu | 10 min |
| 2 | Vlastnosti světel – intenzita, barva, velikost | 10 min |
| 3 | Tříbodové osvětlení (key, fill, rim) | 15 min |
| 4 | HDRI prostředí a nastavení scény | 10 min |
| 5 | Společný projekt – Profesionální nasvícení domečku | 25–30 min |
| 6 | Samostatný projekt (výběr ze 3 scén) | 20–30 min |
| 7 | Shrnutí a ukázání prací | 5 min |

---

## Fáze 1 – Typy světel v Blenderu (10 min)

### Přidání světla do scény
- **Shift + A → Light** – otevře menu s výběrem typu světla
- Světlo se přidá na pozici 3D kurzoru (stejně jako jakýkoli jiný objekt)
- Světlo lze posouvat (**G**), otáčet (**R**) a škálovat (**S**) jako každý objekt

### Čtyři typy světel

| Typ | Ikona | Chování | Kdy použít |
|-----|-------|---------|------------|
| **Point** | Tečka | Svítí ze středu do všech směrů (jako žárovka) | Lampy, svíčky, pouliční osvětlení |
| **Sun** | Slunce | Rovnoběžné paprsky, pozice nehraje roli – záleží jen na rotaci | Denní venkovní světlo, měsíční svit |
| **Spot** | Kužel | Kuželový paprsek s nastavitelným úhlem a okrajem | Reflektory, jevištní osvětlení, baterka |
| **Area** | Obdélník | Plošné světlo z obdélníkové/čtvercové plochy | Okna, softboxy, studiové osvětlení |

> **Tip pro výuku:** Přidejte do scény postupně všechny 4 typy světel vedle sebe a přepněte do renderovaného pohledu (**Z → Rendered**). Studenti okamžitě uvidí rozdíl v tom, jak každé světlo osvětluje stejný objekt. Nechte je hádat, které je které.

---

- Čtyři koule v řadě, každá s jiným typem světla
- Point: měkký kruhový odlesk, stín do všech stran
- Sun: rovnoměrné osvětlení, rovnoběžné stíny
- Spot: kuželový dopad světla s jasným středem a tmavým okolím
- Area: měkký obdélníkový odlesk, jemné stíny

---

### Přepínání zobrazení pro náhled světel

| Akce | Klávesa / postup |
|------|-------------------|
| Rendered pohled (Eevee) | **Z → Rendered** |
| Material Preview | **Z → Material Preview** |
| Solid (výchozí) | **Z → Solid** |
| Wireframe | **Z → Wireframe** |

> **Tip pro výuku:** V Solid zobrazení světla nevidíte. Studenti se často ptají, proč se nic neděje – ujistěte se, že přepnou na Rendered nebo alespoň Material Preview. Doporučení: pracujte celou lekci v Rendered pohledu.

---

## Fáze 2 – Vlastnosti světel – intenzita, barva, velikost (10 min)

### Kde najít nastavení světla
1. Vyberte světlo v scéně (klik)
2. V **Properties panelu** (vpravo) klikněte na ikonu **žárovky** (Object Data Properties)
3. Zde najdete všechna nastavení vybraného světla

### Intenzita (Power / Watts)

| Typ světla | Jednotka | Doporučený rozsah pro interiér | Doporučený rozsah pro exteriér |
|------------|----------|-------------------------------|-------------------------------|
| Point | Watts (W) | 50–500 W | 500–5000 W |
| Sun | Watts/m² | 1–5 | 3–10 |
| Spot | Watts (W) | 100–1000 W | 1000–10000 W |
| Area | Watts (W) | 50–500 W | 500–5000 W |

- Hodnoty se velmi liší podle velikosti scény a render enginu (Eevee vs Cycles)
- V **Cycles** jsou hodnoty fyzikálně přesné, v **Eevee** je potřeba experimentovat

---

- Vybrané světlo v scéně (oranžový obrys)
- Properties panel → záložka Light (ikona žárovky)
- Slider/pole Power s číselnou hodnotou
- Dropdown pro výběr typu světla nahoře

---

### Barva světla
- Klikněte na barevný obdélník vedle **Color** v nastavení světla
- Otevře se color picker – můžete zadat RGB hodnoty nebo vybrat vizuálně
- **Teplé světlo** (žluté/oranžové): interiér, svíčky, západ slunce → cca `#FFD4A0`
- **Studené světlo** (modré/bílé): kancelář, měsíc, zima → cca `#C4D8FF`
- **Neutrální bílé**: studiové osvětlení → `#FFFFFF`

> **Tip pro výuku:** Nechte studenty experimentovat s extrémními barvami (červená, zelená, modrá), aby viděli efekt. Poté vysvětlete, že v praxi se používají jemné odstíny bílé – teplé a studené.

### Velikost světla (měkkost stínů)

| Parametr | Kde najít | Efekt |
|----------|-----------|-------|
| **Radius** (Point, Spot) | Light Properties → Radius | Větší = měkčí stíny |
| **Size** (Area) | Light Properties → Size | Větší plocha = měkčí stíny |
| **Angle** (Sun) | Light Properties → Angle | Větší úhel = měkčí stíny |

- **Malý radius** = ostré, tvrdé stíny (dramatické, thriller)
- **Velký radius** = měkké, rozptýlené stíny (portrét, produktová fotka)
- V **Eevee** je potřeba zapnout **Soft Shadows**: Render Properties → Shadows → Soft Shadows

---

- Levý render: ostrý, jasně definovaný stín
- Pravý render: měkký, rozplývající se stín
- Popisky „Radius 0.1" a „Radius 1.0"
- Stejný objekt, stejná pozice světla, jiný radius

---

### Nastavení Spot světla – speciální parametry

| Parametr | Funkce |
|----------|--------|
| **Spot Size** | Úhel kužele (15°–175°) |
| **Blend** | Měkkost okraje kužele (0 = ostrý, 1 = úplně rozptýlený) |
| **Show Cone** | Zobrazí kužel ve viewportu (zaškrtněte pro lepší orientaci) |

---

- Spot světlo s viditelným žlutým kuželem ve viewportu
- Objekt osvětlený kuželovým paprskem
- Properties panel s parametry Spot Size a Blend
- Dopad světla na podlahu – kruhová skvrna

---

## Fáze 3 – Tříbodové osvětlení (15 min)

### Teorie tříbodového osvětlení

Tříbodové osvětlení je základ profesionálního nasvícení ve fotografii, filmu i 3D grafice. Skládá se ze tří světel:

| Světlo | Anglický název | Pozice | Účel | Intenzita |
|--------|---------------|--------|------|-----------|
| **Hlavní** | Key Light | 45° vlevo/vpravo, mírně nad objektem | Primární osvětlení, definuje tvar | 100 % |
| **Výplňové** | Fill Light | Opačná strana než key, na úrovni objektu | Zjemní stíny od key lightu | 30–50 % key |
| **Obrysové** | Rim / Back Light | Za objektem, nahoře | Oddělí objekt od pozadí, vytvoří obrys | 50–80 % key |

---

- Pohled shora na scénu
- Objekt uprostřed
- Key light vlevo nahoře (největší ikona/popisek)
- Fill light vpravo (menší)
- Rim light vzadu (za objektem)
- Šipky nebo čáry ukazující směr osvětlení

---

### Praktické nastavení krok za krokem

#### 1. Key Light (hlavní světlo)
1. Smažte výchozí světlo ve scéně (**X** nebo **Delete**)
2. **Shift + A → Light → Area** (Area dává nejhezčí měkké stíny)
3. Přesuňte: **G → X → -3** (vlevo od objektu)
4. Posuňte nahoru: **G → Z → 3**
5. Natočte směrem k objektu: **R → Y → -45** (experimentujte)
6. Nastavte Power: **300 W** (upravíte podle potřeby)
7. Nastavte Size: **2 m** (větší = měkčí stíny)

#### 2. Fill Light (výplňové světlo)
1. **Shift + A → Light → Area**
2. Přesuňte na opačnou stranu: **G → X → 2**, **G → Z → 2**
3. Natočte k objektu
4. Power: **100 W** (třetinová intenzita key lightu)
5. Size: **3 m** (větší než key = ještě měkčí)
6. Volitelně: lehce namodralá barva pro kontrast

#### 3. Rim Light (obrysové světlo)
1. **Shift + A → Light → Spot** (nebo Area)
2. Přesuňte za objekt: **G → Y → 3**, **G → Z → 3**
3. Natočte směrem k objektu (zezadu)
4. Power: **200 W**
5. Pokud Spot: Spot Size cca **60°**, Blend cca **0.5**

> **Tip pro výuku:** Přidávejte světla jedno po druhém a po každém nechte studenty přepnout do Rendered pohledu. Ať vidí, jak každé další světlo mění výsledek. Zeptejte se: „Co se změnilo? Proč je to lepší?"

---

- Tři rendery stejného objektu vedle sebe
- Render 1: tvrdší stíny, jedna osvětlená strana, druhá tmavá
- Render 2: zjemněné stíny na tmavé straně
- Render 3: světelný obrys kolem objektu, oddělení od pozadí
- Popisky „Key", „Key + Fill", „Key + Fill + Rim"

---

## Fáze 4 – HDRI prostředí a nastavení scény (10 min)

### Co je HDRI
- **HDRI** = High Dynamic Range Image – 360° fotografie prostředí
- Slouží jako **osvětlení** i jako **pozadí** scény zároveň
- Dává realistické odrazy a měkké globální osvětlení
- Formát: `.hdr` nebo `.exr`

### Kde stáhnout HDRI zdarma
| Web | URL | Poznámka |
|-----|-----|----------|
| **Poly Haven** | [polyhaven.com/hdris](https://polyhaven.com/hdris) | Zdarma, CC0 licence, obrovský výběr |
| HDRi Haven (starší název) | Přesměruje na Poly Haven | Stejné |
| Ambientcg | [ambientcg.com](https://ambientcg.com) | Zdarma, CC0, HDRI + textury |

> **Tip pro výuku:** Stáhněte předem 3–4 HDRI soubory (rozlišení 2K stačí pro výuku) a uložte je na sdílený disk nebo rozdejte studentům na flash discích. Doporučení: 1x exteriér (louka), 1x interiér (studio), 1x západ slunce, 1x město v noci.

### Nastavení HDRI v Blenderu

1. Otevřete **World Properties** (ikona zeměkoule v Properties panelu)
2. Klikněte na žlutou tečku vedle **Color** → vyberte **Environment Texture**
3. Klikněte **Open** → vyberte stažený `.hdr` soubor
4. Přepněte do **Rendered pohledu** (**Z → Rendered**) – uvidíte HDRI jako pozadí

### Úprava HDRI

| Akce | Jak na to |
|------|-----------|
| Otáčení HDRI | V Shader Editoru: Add → Vector → Mapping, propojit s Environment Texture, měnit Rotation Z |
| Intenzita HDRI | World Properties → Surface → Strength (výchozí 1.0) |
| HDRI jen jako osvětlení (bez pozadí) | Render Properties → Film → Transparent (zaškrtnout) – pozadí bude průhledné |

---

- World Properties panel s nastavenou Environment Texture
- Název HDRI souboru v cestě
- Viewport zobrazující HDRI panorama jako pozadí
- Objekt ve scéně s realistickým osvětlením z HDRI
- Strength slider

---

- Levý render: šedé pozadí, umělé stíny, ploché osvětlení
- Pravý render: realistické pozadí (obloha/prostředí), měkké stíny, barevné odrazy na objektu
- Jasný rozdíl v kvalitě a realističnosti
- Popisky „Bez HDRI" a „S HDRI"

---

### Základní nastavení scény

#### Pozadí a podlaha
1. **Podlaha/plán:** Shift + A → Mesh → Plane → **S → 20** (velká podlahová plocha)
2. Přesuňte plán pod objekt: **G → Z** → zarovnat se spodní hranou objektu
3. **Pozadí:** Buď HDRI (viz výše) nebo plán zakřivený nahoru:
   - Edit Mode → vyberte zadní hranu → **E → Z** nahoru → **S → Z → 0** (rovná hrana) – vytvoří nekonečné pozadí (tzv. „cyclorama")

#### Scale objektů
- Blender pracuje v metrech – 1 jednotka = 1 metr
- Zkontrolujte: Properties panel → Scene Properties → Unit System → **Metric**
- Správný scale je důležitý pro:
  - Realistické chování světel (intenzita klesá se vzdáleností)
  - Fyzikální simulace v budoucích lekcích
  - Správné proporce při importu/exportu

| Objekt | Doporučený scale |
|--------|-----------------|
| Domeček (z lekce 1) | cca 4–6 m výška |
| Hrnek | cca 0.1 m (10 cm) |
| Stůl | cca 0.75 m výška |
| Podlaha | 20–50 m |

> **Tip pro výuku:** Pokud studenti v lekci 1 neaplikovali scale (**Ctrl + A → Scale**), připomeňte jim to nyní. Neaplikovaný scale způsobuje problémy se světly a stíny.

---

## Fáze 5 – Společný projekt: Profesionální nasvícení domečku (25–30 min)

> **Poznámka pro učitele:** Studenti otevřou svůj soubor domečku z lekce 1. Pokud ho někdo nemá, připravte si předem základní model domečku ke stažení. Budujte krok po kroku, po každém kroku nechte studenty dostat se na stejnou úroveň.

### Krok 1 – Příprava scény
1. Otevřete soubor s domečkem z lekce 1 (**File → Open**)
2. Ověřte scale domečku – měl by mít cca 4–6 metrů na výšku
3. Pokud je scale špatně: vyberte domeček → **Ctrl + A → Scale**
4. Smažte výchozí světlo (**klik na světlo → X → Delete**)
5. Smažte výchozí kameru (tu nastavíme později) – nebo nechte

### Krok 2 – Přidání podlahy
1. **Shift + A → Mesh → Plane**
2. **S → 20 → Enter** (velká podlaha)
3. Zarovnejte se spodní hranou domečku: **G → Z** → posuňte dolů
4. V Properties panelu: Object Properties → Location → Z = 0 (nebo přesná hodnota)

---

- Model domečku z lekce 1 (střecha, dveře, okna, komín)
- Velká podlahová plocha pod domečkem
- Perspektivní pohled
- Outliner vpravo s objekty: domeček, Plane

---

### Krok 3 – Key Light (hlavní světlo)
1. **Shift + A → Light → Area**
2. Přejmenujte v Outlineru: dvakrát klikněte → napište **„Key_Light"**
3. Pozice: **G → X → -6**, **G → Z → 5**, **G → Y → -3** (vlevo vpředu, nahoře)
4. Natočte k domečku: vyberte světlo → v Properties → Object Properties → Rotation:
   - X: **60°**, Y: **0°**, Z: **-30°** (experimentujte)
   - Alternativa: použijte **Track To** constraint (Properties → Constraints → Track To → Target: domeček)
5. Light Properties: Power = **500 W**, Size = **3 m**, Color = **teplá bílá (#FFF0D4)**

> **Tip pro výuku:** Nechte studenty přepnout do Rendered pohledu (**Z → Rendered**) a podívat se na výsledek. Zeptejte se: „Kde jsou stíny? Je to realistické? Co by pomohlo?"

### Krok 4 – Fill Light (výplňové světlo)
1. **Shift + A → Light → Area**
2. Přejmenujte na **„Fill_Light"**
3. Pozice: **G → X → 4**, **G → Z → 3**, **G → Y → -2** (vpravo vpředu, mírně níž)
4. Natočte k domečku (stejný postup jako key)
5. Light Properties: Power = **150 W**, Size = **5 m**, Color = **lehce modrá (#D4E4FF)**

---

- Domeček v Rendered pohledu
- Hlavní osvětlení z jedné strany (teplé)
- Jemnější doplňkové osvětlení z druhé strany (chladnější)
- Měkké stíny na podlaze
- V Outlineru viditelné „Key_Light" a „Fill_Light"

---

### Krok 5 – Rim Light (obrysové světlo)
1. **Shift + A → Light → Spot**
2. Přejmenujte na **„Rim_Light"**
3. Pozice: **G → Y → 5**, **G → Z → 6** (za domečkem, vysoko)
4. Natočte dolů směrem k domečku: Rotation X: **-120°**
5. Light Properties: Power = **300 W**, Spot Size = **70°**, Blend = **0.5**
6. Zapněte **Show Cone** pro vizuální kontrolu

### Krok 6 – HDRI pozadí
1. World Properties (ikona zeměkoule) → Color → **Environment Texture**
2. Open → vyberte HDRI soubor (doporučení: exteriérová louka nebo obloha)
3. Strength: **0.5** (nechceme, aby HDRI přebilo naše světla)
4. Přepněte do Rendered pohledu – uvidíte HDRI jako pozadí

---

- Profesionálně nasvícený domeček
- Teplé hlavní světlo z jedné strany
- Jemný fill z druhé strany
- Světelný obrys (rim) na střeše a komínu
- HDRI pozadí (obloha s mraky nebo krajina)
- Měkké stíny na podlaze

---

### Krok 7 – Nastavení kamery a první render
1. Vyberte kameru (klik v Outlineru nebo ve viewportu)
2. Pozicujte kameru: **G** a **R** pro přesun a rotaci
3. **Rychlý způsob:** nastavte viewport tak, jak chcete render → **Ctrl + Alt + Numpad 0** (kamera se přesune na aktuální pohled)
4. Pohled z kamery: **Numpad 0**
5. Render: **F12** (render obrázku)
6. Uložit render: **Image → Save As** (nebo **Alt + S**)

| Akce | Klávesa |
|------|---------|
| Pohled z kamery | Numpad 0 |
| Kamera na aktuální pohled | Ctrl + Alt + Numpad 0 |
| Render obrázku | F12 |
| Uložit render | Alt + S (v render okně) |

---

- Čistý renderovaný obrázek (ne viewport, ale výstup z F12)
- Profesionální nasvícení domečku
- HDRI pozadí
- Měkké stíny a světelný obrys
- Dobře zvolený úhel kamery

---

### Hotová scéna – shrnutí nastavení

| Prvek | Typ | Nastavení |
|-------|-----|-----------|
| Key Light | Area | 500 W, Size 3 m, teplá bílá |
| Fill Light | Area | 150 W, Size 5 m, lehce modrá |
| Rim Light | Spot | 300 W, Spot Size 70°, Blend 0.5 |
| HDRI | Environment Texture | Strength 0.5 |
| Podlaha | Plane | Scale 20, zarovnáno pod domeček |
| Kamera | Camera | Nastaveno přes Ctrl + Alt + Numpad 0 |

---

## Fáze 6 – Samostatný projekt (20–30 min)

> **Zadání:** Vyberte si jednu z následujících scén a vytvořte ji. Použijte model z lekce 1 (domeček, hrnek, stůl nebo meč) nebo vytvořte jednoduchý nový objekt. Klíčové je nasvícení a atmosféra.

### Scéna A – Západ slunce 🌅
**Obtížnost:** ⭐⭐ (střední)

**Co procvičíte:** Sun světlo, HDRI, barevná teplota, atmosféra

**Postup (nápověda):**
1. Umístěte objekt (domeček nebo stůl) na podlahu (Plane)
2. Přidejte **Sun** světlo: Shift + A → Light → Sun
3. Natočte Sun nízko nad horizont: Rotation X cca **-15°** (nízké slunce)
4. Barva: teplá oranžová **#FF8C42**, Power: **3**
5. Stáhněte HDRI se západem slunce z Poly Haven (hledejte „sunset")
6. World Properties → Environment Texture → nastavte HDRI
7. Přidejte jemný **Fill Light** (Area, modrá, 50 W) z opačné strany
8. Nastavte kameru a renderujte (**F12**)
9. **Bonus:** Přidejte mlhu – World Properties → Volume → Volume Scatter

**Obtížnost:** ⭐ (lehčí)

**Co procvičíte:** Tříbodové osvětlení, čisté pozadí, Area světla

**Postup (nápověda):**
1. Umístěte objekt (hrnek nebo meč) doprostřed scény
2. Vytvořte cycloramu (nekonečné pozadí):
   - Shift + A → Mesh → Plane → S → 5
   - Edit Mode → vyberte zadní hranu → E → Z → nahoru → S → Z → 0
   - Přidejte **Subdivision Surface** modifier (level 3) pro hladký ohyb
3. Nastavte tříbodové osvětlení (Key, Fill, Rim) podle postupu z fáze 5
4. Všechna světla: **Area**, čistě bílá barva
5. Render Properties → Film → **Transparent** (průhledné pozadí) – volitelně
6. Nastavte kameru nízko, lehce nad úrovní objektu
7. Renderujte (**F12**)

### Scéna C – Dramatický spotlight 🔦
**Obtížnost:** ⭐⭐⭐ (těžší)

**Co procvičíte:** Spot světlo, kontrastní osvětlení, stíny, atmosféra

**Postup (nápověda):**
1. Umístěte objekt (meč nebo domeček) na podlahu
2. **Smažte všechna světla** a HDRI – scéna bude temná
3. World Properties → Color → černá (**#000000**) – úplně tmavé pozadí
4. Přidejte **Spot** světlo přímo nad objekt: G → Z → 5 (vysoko nad objektem)
5. Natočte dolů: Rotation X = **-90°** (svítí přímo dolů)
6. Spot Size: **30°** (úzký paprsek), Blend: **0.3** (mírně měkký okraj)
7. Power: **1000 W**, barva: **teplá žlutá**
8. Přidejte druhý **Spot** z boku – Power: **200 W**, barva: **studená modrá**
9. Přidejte **Volume Scatter** do World Properties pro viditelné paprsky:
   - World Properties → Volume → Volume Scatter → Density: **0.05**
10. Nastavte kameru a renderujte (**F12**)
11. **Bonus:** Přidejte další spot světla z různých úhlů pro dramatičtější efekt

---

- Tři rendery vedle sebe jako inspirace
- Scéna A: teplé barvy, nízké slunce, dlouhé stíny, HDRI pozadí
- Scéna B: čisté bílé pozadí, rovnoměrné osvětlení, produkt uprostřed
- Scéna C: tmavé pozadí, dramatický kužel světla, vysoký kontrast
- Popisky „Scéna A", „Scéna B", „Scéna C"

---

## Fáze 7 – Shrnutí a závěr (5 min)

### Co jsme se dnes naučili
- Čtyři typy světel: **Point**, **Sun**, **Spot**, **Area** – a kdy které použít
- Vlastnosti světel: **intenzita** (Watts), **barva**, **velikost** (měkkost stínů)
- **Tříbodové osvětlení** – Key, Fill, Rim – základ profesionálního nasvícení
- **HDRI prostředí** – realistické osvětlení a pozadí pomocí Environment Texture
- Nastavení scény: podlaha, pozadí, správný scale objektů
- Nastavení kamery a **render** (F12)

### Klávesové zkratky – tahák

| Zkratka | Funkce |
|---------|--------|
| Shift + A → Light | Přidat světlo |
| Z → Rendered | Rendered pohled (náhled osvětlení) |
| Z → Material Preview | Material Preview pohled |
| Z → Solid | Solid pohled (výchozí) |
| Numpad 0 | Pohled z kamery |
| Ctrl + Alt + Numpad 0 | Kamera na aktuální pohled |
| F12 | Render obrázku |
| Alt + S | Uložit render (v render okně) |
| G → osa → číslo | Přesun světla na přesnou pozici |
| R → osa → číslo | Rotace světla o přesný úhel |
| X / Delete | Smazat vybraný objekt |
| Ctrl + A → Scale | Aplikovat scale |
| Ctrl + Z | Zpět (Undo) |

---

## Poznámky pro učitele

### Příprava před lekcí
- [ ] Ověřit, že studenti mají uložené modely z lekce 1 (připravte záložní soubor domečku `.blend`)
- [ ] Stáhnout 3–4 HDRI soubory z [polyhaven.com/hdris](https://polyhaven.com/hdris) (rozlišení 2K, formát `.hdr`)
  - Doporučené: `kloofendal_48d_partly_cloudy`, `studio_small_09`, `sunflowers`, `moonless_golf`
- [ ] Uložit HDRI na sdílený disk / flash disky / školní server
- [ ] Připravit hotový nasvícený domeček jako ukázku finálního výsledku
- [ ] Ověřit, že render engine je nastaven na **Eevee** (rychlejší pro výuku) nebo **Cycles** (hezčí, ale pomalejší)
- [ ] Mít připravené referenční obrázky tří scén pro samostatný projekt
- [ ] Vyzkoušet, zda školní počítače zvládnou Rendered pohled plynule (pokud ne, snižte render vzorky)

### Tipy pro průběh výuky
- **Eevee vs Cycles:** Pro výuku doporučuji **Eevee** – je výrazně rychlejší a studenti uvidí změny okamžitě. Cycles dává hezčí výsledky, ale studenti budou čekat na každý render. Ukažte rozdíl na jednom příkladu a nechte rozhodnutí na studentech.
- **Rendered pohled:** Ujistěte se, že všichni studenti pracují v Rendered pohledu (**Z → Rendered**). Bez toho nevidí efekt světel a myslí si, že něco nefunguje.
- **Postupné přidávání:** Nikdy nepřidávejte všechna tři světla najednou. Vždy jedno, podívat se na výsledek, diskutovat, pak další. Studenti tak pochopí účel každého světla.
- **Pojmenování objektů:** Trvejte na přejmenování světel v Outlineru (Key_Light, Fill_Light, Rim_Light). Studenti se pak lépe orientují ve scéně.
- **Promítání:** Mějte Blender na projektoru v Rendered pohledu. Studenti potřebují vidět váš výsledek pro srovnání.

### Časté chyby studentů
| Chyba | Příčina | Řešení |
|-------|---------|--------|
| „Světla nevidím – nic se neděje" | Jsou v Solid zobrazení | Přepnout na Rendered: **Z → Rendered** |
| Světlo svítí špatným směrem | Nenatočili ho k objektu | **R** pro rotaci nebo použít Track To constraint |
| Příliš tmavá / příliš světlá scéna | Špatná intenzita | Upravit Power ve Light Properties |
| HDRI se nezobrazuje | Nepoužili Environment Texture | World Properties → Color → Environment Texture |
| Stíny jsou pixelované | Nízké rozlišení stínů v Eevee | Render Properties → Shadows → zvýšit rozlišení |
| Objekty „létají" nad podlahou | Podlaha není zarovnaná | Zkontrolovat Z pozici objektů a podlahy |
| Render je úplně černý | Žádné světlo ve scéně / špatná expozice | Přidat světlo nebo zvýšit Power / Strength HDRI |
| Spot světlo nesvítí na objekt | Kužel míří jinam | Zapnout Show Cone, natočit pomocí R |

### Hodnocení samostatného projektu

| Kritérium | Body |
|-----------|------|
| Scéna má minimálně 2 světla správně nastavená | 3 |
| Viditelný záměr v nasvícení (atmosféra, nálada) | 2 |
| Správné použití HDRI nebo pozadí | 2 |
| Kvalitní finální render (kamera, kompozice) | 2 |
| Přidané vlastní detaily navíc (mlha, extra světla, materiály) | 1 |
| **Celkem** | **10** |

---

> **Příští lekce:** Lekce 3 – Materiály a textury. Naučíme se přidávat barvy, textury a materiály na naše modely, pracovat se Shader Editorem a vytvářet realistické povrchy.

