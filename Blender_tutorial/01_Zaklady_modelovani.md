# Lekce 1 – Základy modelování v Blenderu

> **Délka lekce:** cca 90–120 minut
> **Cíl:** Studenti se naučí orientaci v Blenderu, základní transformace, Edit Mode a klíčové modelovací nástroje. Společně vytvoří 3D model domečku a poté samostatně jeden ze tří objektů na výběr.

---

## Přehled lekce

| Fáze | Obsah | Čas |
|------|-------|-----|
| 1 | Orientace v rozhraní | 10 min |
| 2 | Transformace a režimy | 10 min |
| 3 | Výběr a základní nástroje | 15 min |
| 4 | Společný projekt – Domeček s komínem | 35–45 min |
| 5 | Samostatný projekt (výběr ze 3 objektů) | 25–35 min |
| 6 | Shrnutí a ukázání prací | 5 min |

---

## Fáze 1 – Orientace v rozhraní Blenderu (10 min)

### Co ukázat
- **Viewport** – hlavní pracovní prostor uprostřed
- **Outliner** (vpravo nahoře) – hierarchie objektů ve scéně
- **Properties panel** (vpravo) – vlastnosti objektu, modifikátory, materiály
- **Timeline** (dole) – zatím jen zmínit, využijeme v lekci 3
- **Toolbar** (vlevo) – nástroje, dají se vyvolat i klávesami

### Navigace ve viewportu
| Akce | Ovládání |
|------|----------|
| Otáčení pohledu | Prostřední tlačítko myši (kolečko) držet a táhnout |
| Posun pohledu | Shift + prostřední tlačítko |
| Přiblížení/oddálení | Scroll kolečkem |
| Přední pohled | Numpad 1 |
| Boční pohled | Numpad 3 |
| Pohled shora | Numpad 7 |
| Perspektiva / Ortho | Numpad 5 |
| Zaměření na objekt | Numpad . (tečka) |

> **Tip pro výuku:** Nechte studenty 2 minuty volně otáčet pohled kolem výchozí kostky, aby si zvykli na ovládání. Kdo nemá numpad, ukažte `View → Viewpoint` menu nebo zapněte `Emulate Numpad` v `Edit → Preferences → Input`.

---

## Fáze 2 – Základní transformace a režimy (10 min)

### Transformace objektů (Object Mode)
| Klávesa | Funkce | Příklad |
|---------|--------|---------|
| **G** | Grab (posun) | G → X = posun pouze po ose X |
| **R** | Rotate (otočení) | R → Z → 45 = otočení o 45° kolem Z |
| **S** | Scale (změna velikosti) | S → Z → 2 = dvojnásobná výška |

- Po stisknutí G/R/S lze zadat osu (**X**, **Y**, **Z**) a přesnou hodnotu číslem
- **Enter** potvrdí, **Esc** nebo pravé tlačítko zruší

> **Tip pro výuku:** Nechte studenty posunout kostku na konkrétní pozici, např. „Posuňte kostku o 3 metry doprava (G → X → 3 → Enter)". Ověří si, že chápou osy.

---

### Object Mode vs Edit Mode
| Režim | Klávesa | K čemu slouží |
|-------|---------|---------------|
| **Object Mode** | Tab | Manipulace s celými objekty (pozice, rotace, scale) |
| **Edit Mode** | Tab | Úprava geometrie objektu (vertexy, hrany, plochy) |

- Přepínání klávesou **Tab**
- V Edit Mode se mění samotný tvar, v Object Mode se s objektem pohybuje jako celkem

---

## Fáze 3 – Výběr a základní modelovací nástroje (15 min)

### Režimy výběru v Edit Mode
| Režim | Klávesa | Ikona | Vybírá |
|-------|---------|-------|--------|
| Vertex | 1 | Bod | Jednotlivé body |
| Edge | 2 | Čára | Hrany |
| Face | 3 | Čtverec | Plochy |

### Způsoby výběru
- **Klik** – vybere jeden prvek
- **Shift + klik** – přidá do výběru
- **Alt + klik na hranu** – Loop Select (vybere celou smyčku)
- **B** – Box Select (obdélníkový výběr)
- **A** – vybrat vše / **Alt + A** – zrušit výběr

### Klíčové modelovací nástroje

#### Extrude (Vysunutí) – klávesa E
- Vysune vybranou plochu/hranu/vertex a vytvoří novou geometrii
- **E** = extrude, pak pohyb myší
- **Alt + E** → Extrude Along Normals = vysunutí rovnoměrně podle normál
- **Extrude Individual Faces** = každá vybraná plocha se vysune samostatně

---

#### Bevel (Zkosení) – Ctrl+B
- Zaoblí/zkosí vybranou hranu
- **Ctrl + B** → pohyb myší = šířka zkosení
- **Scroll kolečkem** = přidání segmentů (více = hladší)
- Na vertexech: **Ctrl + Shift + B**

---

#### Inset Faces – klávesa I
- Vloží menší plochu dovnitř vybrané plochy
- Užitečné před extrude (např. okno ve stěně)

#### Loop Cut – Ctrl+R
- Přidá nový řez (edge loop) do objektu
- **Ctrl + R** → najet na objekt → scroll pro počet řezů → klik

---

#### Knife Tool – klávesa K
- Volné řezání – klikáním se kreslí řezná čára
- **Enter** potvrdí řez

#### Další užitečné
| Nástroj | Klávesa | Funkce |
|---------|---------|--------|
| Bridge Edge Loops | Edge menu → Bridge | Spojí dva edge loopy plochou |
| Fill | F | Vyplní výběr plochou |
| Merge | M | Sloučí vertexy do jednoho bodu |

> **Tip pro výuku:** Ukažte každý nástroj na výchozí kostce, nechte studenty zopakovat. Na tohle dejte 1–2 minuty na nástroj. Nemusí si pamatovat vše – budou to používat v projektu.

---

## Fáze 4 – Společný projekt: Domeček s komínem 🏠 (35–45 min)

> **Poznámka pro učitele:** Tento projekt záměrně využívá všechny probrané nástroje. Budujte krok po kroku, po každém kroku počkejte, až studenti dohoní. Promítejte svůj Blender na plátno/TV.

### Krok 1 – Tělo domečku (kostka)
1. Otevřete Blender – výchozí kostka bude základ
2. V Object Mode změňte velikost: **S → Z → 1.5 → Enter** (vyšší kostka)
3. Aplikujte scale: **Ctrl + A → Scale** (důležité pro správné fungování nástrojů)

---

### Krok 2 – Střecha (extrude + scale)
1. Přepněte do Edit Mode (**Tab**)
2. Face select (**3**)
3. Vyberte horní plochu
4. **E** (extrude) → **S** (scale) → zmenšit na cca 0.0 → **Enter** (stáhne do špičky)
   - Alternativa: **E → Z → 1** (extrude nahoru) → **S → Shift+Z → 0** (stáhne do čáry) pro sedlovou střechu

> **Tip pro výuku:** Nechte studenty zkusit obě varianty – špičatou a sedlovou střechu. Sedlová je náročnější, ale lepší pro procvičení.

---

### Krok 3 – Dveře (loop cut + inset + extrude)
1. Přepněte na přední pohled (**Numpad 1**)
2. **Ctrl + R** – přidejte 2 horizontální loop cuty na přední stěnu (pro vymezení oblasti dveří)
3. **Face select (3)** – vyberte plochu, kde budou dveře
4. **I** (Inset) – trochu zmenšit (rámeček dveří)
5. **E** → záporný směr (dovnitř) – vytvoří zapuštění dveří

---

### Krok 4 – Okna (inset + extrude)
1. Vyberte plochu na boční stěně (případně přidejte loop cuty pro lepší pozici)
2. **I** (Inset) → vytvoříme rámeček okna
3. **E** → mírně dovnitř – zapuštění okna
4. Opakujte na druhé straně

---

### Krok 5 – Komín (extrude)
1. Face select – vyberte malou plochu na střeše (možná budete muset přidat loop cut na střechu)
2. **E** → nahoru – vysunout komín
3. Vyberte horní plochu komínu → **I** (Inset) → **E** dolů – vytvoří dutinu komínu

---

### Krok 6 – Bevel pro realističtější hrany
1. Přepněte na Edge select (**2**)
2. Vyberte hrany střechy (**Alt + klik** pro loop select)
3. **Ctrl + B** → jemný bevel → scroll pro 2–3 segmenty
4. Totéž na hranách kolem dveří a oken

---

### Krok 7 – Subdivision Surface (volitelné)
1. Přepněte do Object Mode (**Tab**)
2. Properties panel → Modifier (klíč ikona) → **Add Modifier → Subdivision Surface**
3. Viewport úroveň: 1–2
4. Ukažte rozdíl – objekt se zaoblí

> **Poznámka:** Na domečku subdivision nebude vypadat nejlépe (zaoblí hrany), ale je důležité ukázat, jak funguje. Můžete ho zase smazat a vysvětlit, že se hodí spíše na organické tvary.

---

### Krok 8 – Boolean: díra pro okno kulatého tvaru (bonus)
1. V Object Mode přidejte válec: **Shift + A → Mesh → Cylinder**
2. Zmenšete a umístěte ho tak, aby procházel stěnou domečku
3. Vyberte domeček → Modifier → **Boolean** → operace: **Difference** → Object: Cylinder
4. Klikněte **Apply**
5. Smažte válec

---

> **Tip pro výuku:** Boolean je mocný nástroj, ale občas dělá problémy s topologií. Ukažte studentům, že výsledek může mít trojúhelníky a vysvětlete, proč je clean topology (quady) důležitá.

### Krok 9 – Reference obrázek (ukázka principu)
1. **Shift + A → Image → Reference**
2. Vyberte obrázek (připravte si předem PNG s náčrtem domečku z boku/zepředu)
3. Nastavte průhlednost v Properties → Object Data → Opacity
4. Zarovnejte do bočního pohledu (**Numpad 3**)

> **Tip pro výuku:** Připravte si předem jednoduchou referenční fotku/náčrt. Studenti uvidí princip – v samostatné práci si mohou najít vlastní referenci.

---

### Hotový domeček – shrnutí použitých nástrojů
| Část domečku | Použité nástroje |
|-------------|-----------------|
| Tělo | Scale, Apply Scale |
| Střecha | Extrude, Scale |
| Dveře | Loop Cut, Inset, Extrude |
| Okna | Inset, Extrude (+ Boolean pro kulaté) |
| Komín | Extrude, Inset |
| Detaily | Bevel, Subdivision Surface |
| Reference | Image Reference |

---

## Fáze 5 – Samostatný projekt (25–35 min)

> **Zadání:** Vyberte si jeden z následujících objektů a vymodelujte ho. Použijte nástroje, které jsme se dnes naučili. Můžete si najít referenční obrázek na internetu a vložit ho do Blenderu.

### Objekt A – Hrnek na kávu ☕
**Obtížnost:** ⭐⭐ (střední)

**Co procvičíte:** Extrude, Bevel, Subdivision Surface, Boolean

**Postup (nápověda):**
1. Začněte s válcem (Shift + A → Mesh → Cylinder, 32 segmentů)
2. V Edit Mode vyberte horní plochu → **I** (Inset) → **E** dolů (vnitřek hrnku)
3. Vyberte hrany nahoře → **Ctrl + B** (bevel) – zaoblení okraje
4. Ucho: přidejte Torus (Shift + A → Mesh → Torus), zmenšete, umístěte na bok, spojte Boolean Union
5. Přidejte **Subdivision Surface** modifier (level 2) – hrnek se krásně zaoblí
6. Volitelně: přidejte talířek pod hrnek (zploštělý válec s bevel)

### Objekt B – Jednoduchý stůl 🪑
**Obtížnost:** ⭐ (lehčí)

**Co procvičíte:** Extrude, Scale po osách, Loop Cut, Bevel

**Postup (nápověda):**
1. Začněte s kostkou – zploštěte ji (**S → Z → 0.1**) = deska stolu
2. Edit Mode → Face select → vyberte spodní plochu
3. **I** (Inset) – zmenšit
4. **E** dolů – vysunou se 4 nohy? Ne – tímhle vznikne „sukně". Lepší postup:
5. Smažte vnitřní plochu, vyberte 4 rohové plochy spodní strany → **E** dolů po jedné = 4 nohy
6. Alternativa: nohy jako samostatné objekty (Shift + A → Mesh → Cylinder), umístit pod rohy
7. **Bevel** na hranách desky – realističtější vzhled
8. Volitelně: **Loop Cut** pro přidání příčky mezi nohy

### Objekt C – Meč / Dýka ⚔️
**Obtížnost:** ⭐⭐⭐ (těžší)

**Co procvičíte:** Extrude, Scale, Loop Cut, Bevel, Knife Tool, Reference Image

**Postup (nápověda):**
1. Najděte si referenční obrázek meče → vložte do Blenderu (Shift + A → Image → Reference)
2. Čepel: začněte s kostkou → **S → Y** (zploštit) → **S → X** (protáhnout)
3. Edit Mode → **Loop Cut** podélný → vyberte vrchní vertexy → **G → Z** nahoru = ostří
4. **Bevel** na špičce a hranách čepele
5. Záštita (crossguard): nová kostka → **S → X** protáhnout do stran → **Bevel**
6. Rukojeť: válec → **S** zmenšit → umístit pod záštitu
7. Hlavice (pommel): UV Sphere → zmenšit → umístit na konec rukojeti
8. Volitelně: **Knife Tool** pro přidání detailů na čepel

---

## Fáze 6 – Shrnutí a závěr (5 min)

### Co jsme se dnes naučili
- Orientace v rozhraní Blenderu (viewport, panely, navigace)
- Transformace: **G** (posun), **R** (rotace), **S** (scale) + osy
- **Edit Mode** vs **Object Mode**
- Výběr: vertex/edge/face, loop select, box select
- Modelovací nástroje: **Extrude** (E), **Bevel** (Ctrl+B), **Inset** (I), **Loop Cut** (Ctrl+R), **Knife** (K), **Fill** (F), **Merge** (M)
- **Subdivision Surface** a **Boolean** modifikátory
- Vložení referenčního obrázku

### Klávesové zkratky – tahák

| Zkratka | Funkce |
|---------|--------|
| Tab | Přepnutí Object/Edit Mode |
| G / R / S | Posun / Rotace / Scale |
| X / Y / Z (po G/R/S) | Omezení na osu |
| E | Extrude |
| I | Inset Faces |
| Ctrl + R | Loop Cut |
| Ctrl + B | Bevel |
| K | Knife Tool |
| F | Fill |
| M | Merge |
| 1 / 2 / 3 | Vertex / Edge / Face select |
| Alt + klik | Loop Select |
| Shift + A | Přidat objekt |
| Ctrl + Z | Zpět (Undo) |
| Ctrl + A | Apply (Scale/Rotation/Location) |
| H / Alt + H | Skrýt / Odkrýt |

---

## Poznámky pro učitele

### Příprava před lekcí
- [ ] Nainstalovat Blender na všechny počítače (stáhnout z [blender.org](https://www.blender.org))
- [ ] Ověřit, že počítače mají myš s kolečkem (bez ní je Blender velmi těžko ovladatelný)
- [ ] Připravit referenční obrázek domečku (PNG, průhledné pozadí ideálně)
- [ ] Mít připravený hotový model domečku pro ukázku finálního výsledku
- [ ] Připravit si screenshoty/slidy klávesových zkratek k promítání

### Tipy pro průběh výuky
- **Tempo:** Budujte krok po kroku. Po každém kroku řekněte „Máte to všichni?" a projděte třídou
- **Promítání:** Mějte Blender na projektoru/sdílené obrazovce. Ideálně dvě obrazovky – na jedné vy, na druhé studenti vidí
- **Chyby studentů:** Nejčastější problémy:
  - Zapomenou přepnout do Edit Mode → nástroje nefungují
  - Extrude omylem dvakrát (vznikne dvojitá geometrie) → Ctrl+Z
  - Neaplikovaný scale → bevel a subdivision se chovají divně
  - Ztracený objekt → Numpad . (focus) nebo A → Numpad . (focus na vše)
- **Pokročilejší studenti:** Ať zkusí těžší objekt (meč) nebo přidají detaily na domeček (schody, plot, okap)
- **Slabší studenti:** Pomozte jim se stolem – je nejjednodušší a zvládnou ho i pomalejší studenti

### Hodnocení samostatného projektu
| Kritérium | Body |
|-----------|------|
| Objekt je rozpoznatelný | 3 |
| Použití alespoň 3 různých nástrojů | 3 |
| Čistá geometrie (bez artefaktů, dvojitých ploch) | 2 |
| Přidané vlastní detaily navíc | 2 |
| **Celkem** | **10** |

---

> **Příští lekce:** Lekce 2 – Nastavení světel a scény. Vezmeme si hotové modely z dnešní lekce a nasvítíme je!

