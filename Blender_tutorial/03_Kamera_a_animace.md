# Lekce 3 – Nastavení kamery a vytvoření záznamu (animace)

> **Délka lekce:** cca 60–90 minut
> **Cíl:** Studenti se naučí správně umístit a nastavit kameru, porozumí základním pravidlům kompozice záběru a vytvoří jednoduchou keyframe animaci. Společně vytvoří plynulý průlet kamery kolem modelu domečku z Lekce 1 a poté samostatně animují jednu ze tří scén na výběr.

---

## Přehled lekce

| Fáze | Obsah | Čas |
|------|-------|-----|
| 1 | Umístění a ovládání kamery | 10 min |
| 2 | Vlastnosti kamery – focal length, depth of field, clipping | 10 min |
| 3 | Kompozice záběru – pravidla a průvodce | 10 min |
| 4 | Keyframe animace – Timeline a základy | 10 min |
| 5 | Společný projekt – Průlet kamery kolem domečku | 25–30 min |
| 6 | Samostatný projekt (výběr ze 3 animací) | 20–25 min |
| 7 | Shrnutí a ukázání prací | 5 min |

---

## Fáze 1 – Umístění a ovládání kamery (10 min)

### Co ukázat
- Ve scéně je **výchozí kamera** (objekt Camera v Outlineru) – pokud ji studenti smazali, přidají novou přes **Shift + A → Camera**
- Kamera je objekt jako každý jiný – dá se posouvat (**G**), otáčet (**R**) a škálovat
- Klíčový je **pohled kamery** (co se bude renderovat)

### Klávesové zkratky pro kameru

| Akce | Klávesa / postup |
|------|-------------------|
| Pohled kamery (co uvidí kamera) | **Numpad 0** |
| Nastavit kameru na aktuální pohled | **Ctrl + Alt + Numpad 0** |
| Aktivní kamera → vybraný objekt | Properties → Scene → Camera → vybrat objekt |
| Zamknout kameru k pohledu (volný pohyb) | **N** → View → ✅ Camera to View |
| Vybrat kameru | Klik na kameru ve viewportu nebo v Outlineru |
| Zaměřit na kameru | Vybrat kameru → **Numpad .** |

> **Tip pro výuku:** Nejdůležitější zkratka je **Ctrl + Alt + Numpad 0** – studenti nastaví pohled ve viewportu tak, jak chtějí záběr, a tímhle příkazem kameru „přichytí" na stejnou pozici. Ušetří spoustu času oproti ručnímu posouvání kamery. Kdo nemá numpad, může použít menu `View → Align View → Align Active Camera to View`.

---

- Rámeček kamery (čárkovaný obdélník) uprostřed viewportu
- Model domečku uvnitř rámečku
- Ztmavená/průhledná oblast mimo záběr kamery
- V Outlineru zvýrazněný objekt Camera

---

- Porovnání PŘED a PO použití Ctrl + Alt + Numpad 0
- Vlevo: původní nevhodný pohled kamery
- Vpravo: kamera přichycená na aktuální viewport pohled
- Domeček hezky vycentrovaný v záběru

---

### Camera to View – zamknutí kamery

1. Stiskněte **Numpad 0** (pohled kamery)
2. Otevřete boční panel: **N**
3. Záložka **View** → zaškrtněte **Camera to View**
4. Nyní se kamera pohybuje s vaším pohledem – kolečkem přiblížíte, středním tlačítkem otočíte
5. Po dokončení **odškrtněte** Camera to View (jinak se kamera bude pořád hýbat)

> **Tip pro výuku:** Upozorněte studenty, ať Camera to View po použití zase vypnou. Je to častý zdroj zmatenosti – „proč se mi kamera pořád hýbe?"

---

## Fáze 2 – Vlastnosti kamery (10 min)

### Kde najít nastavení kamery
1. Vyberte kameru (klik nebo Outliner)
2. V **Properties panelu** (vpravo) klikněte na ikonu **kamery** (Object Data Properties)

### Focal Length (ohnisková vzdálenost)

| Hodnota | Efekt | Použití |
|---------|-------|---------|
| **18–24 mm** | Širokoúhlý záběr, velké zkreslení | Interiéry, krajiny, dramatické záběry |
| **35–50 mm** | Přirozený pohled, minimální zkreslení | Univerzální, běžné scény |
| **85–200 mm** | Teleobjektiv, komprese perspektivy | Portréty, detaily, produktové foto |

- Výchozí hodnota v Blenderu je **50 mm**
- Nastavení: Properties → Camera → Lens → **Focal Length**

> **Tip pro výuku:** Nechte studenty měnit focal length v reálném čase při pohledu kamery (Numpad 0). Ať zkusí 18 mm, 50 mm a 135 mm a uvidí rozdíl na vlastní oči. Efekt je velmi vizuální a dobře zapamatovatelný.

---

- Tři rendery/viewport záběry vedle sebe
- 18 mm – domeček vypadá zkreslený, přehnaná perspektiva
- 50 mm – přirozený pohled
- 135 mm – plochý záběr, domeček vypadá „stlačený"
- U každého záběru popisek s hodnotou focal length

---

### Depth of Field (hloubka ostrosti – rozostření pozadí)

Hloubka ostrosti vytváří efekt **rozostření** (bokeh) – objekt v popředí je ostrý, pozadí rozmazané. Profesionální vzhled snadno.

1. Vyberte kameru → Properties → Camera → **Depth of Field** → zaškrtněte ✅
2. **Focus Object** – vyberte objekt, na který má být zaostřeno (např. domeček)
   - Alternativa: **Focus Distance** – ruční nastavení vzdálenosti zaostření v metrech
3. **F-Stop** – čím nižší číslo, tím větší rozostření:
   - **f/1.4** = hodně rozostřené pozadí (filmový look)
   - **f/5.6** = mírné rozostření
   - **f/22** = téměř vše ostré

| Parametr | Kde najít | Co dělá |
|----------|-----------|---------|
| Depth of Field (checkbox) | Camera → DoF | Zapne/vypne rozostření |
| Focus Object | Camera → DoF → Focus Object | Objekt, na který se zaostřuje |
| Focus Distance | Camera → DoF → Focus Distance | Ruční vzdálenost zaostření |
| F-Stop | Camera → DoF → Aperture → F-Stop | Míra rozostření (nízké = více) |

---

- Vlevo: záběr bez Depth of Field – vše je ostré
- Vpravo: záběr s DoF zapnutým (f/1.4) – domeček ostrý, pozadí rozmazané
- V Properties panelu viditelné nastavení DoF s hodnotami
- Jasný vizuální rozdíl mezi oběma záběry

---

### Clipping (ořezové roviny)

- **Clip Start** – minimální vzdálenost, od které kamera „vidí" (výchozí 0.1 m)
- **Clip End** – maximální vzdálenost, kam kamera „dohlédne" (výchozí 1000 m)
- Pokud se objekty nezobrazují v pohledu kamery, zkontrolujte clipping
- Nastavení: Properties → Camera → Lens → **Clip Start / Clip End**

> **Tip pro výuku:** Clipping většinou není potřeba měnit. Zmíňte ho krátce – studenti se s ním setkají, až budou mít velké scény nebo když se objekty „záhadně" nezobrazí.

---

## Fáze 3 – Kompozice záběru (10 min)

### Rule of Thirds (pravidlo třetin)
- Záběr se rozdělí na **3×3** mřížku
- Klíčové prvky scény umísťujte na **průsečíky** nebo **podél čar** – ne doprostřed
- Horizont na horní nebo dolní třetinu, nikdy přesně uprostřed

### Zapnutí průvodců kompozice v Blenderu
1. Vyberte kameru
2. Properties → Camera → **Viewport Display**
3. **Composition Guides:**
   - **Thirds** – mřížka třetin (nejdůležitější)
   - **Center** – středový kříž
   - **Center Diagonal** – diagonály
   - **Golden Ratio** – zlatý řez
   - **Harmony Triangle** – harmonické trojúhelníky

---

- Pohled kamery s mřížkou třetin (čáry rozdělující záběr na 3×3)
- Domeček umístěný na jednom z průsečíků (ne ve středu)
- V Properties panelu zaškrtnutá volba „Thirds"
- Volitelně i další guides (Golden Ratio) pro porovnání

---

### Základní tipy pro kompozici

| Pravidlo | Popis | Příklad |
|----------|-------|---------|
| Rule of Thirds | Hlavní objekt na průsečíku třetin | Domeček v pravé třetině záběru |
| Leading Lines | Čáry vedou oko diváka k hlavnímu objektu | Cesta vedoucí k domečku |
| Headroom | Nechte prostor nad/pod objektem | Domeček nemá „nalepený" na horní okraj |
| Depth | Přední, střední a zadní plán | Keř vpředu, domeček uprostřed, kopce vzadu |

> **Tip pro výuku:** Ukažte studentům 2–3 filmové záběry (screenshoty z filmů) s viditelnou mřížkou třetin. Uvidí, že pravidlo třetin se používá v reálné kinematografii. Můžete promítnout záběr z oblíbeného filmu a přiložit mřížku.

---

## Fáze 4 – Keyframe animace a Timeline (10 min)

### Co je keyframe
- **Keyframe** = „klíčový snímek" – uložená hodnota vlastnosti v daném čase
- Blender **interpoluje** (dopočítá plynulý přechod) mezi keyframy automaticky
- Můžete animovat cokoliv: pozici, rotaci, scale, focal length, barvy...

### Timeline panel
- Nachází se **dole** v rozhraní
- Zobrazuje čas v **frame** (snímcích)
- Výchozí: 24 fps (frames per second) → 1 sekunda = 24 snímků
- Zelená čára = **playhead** (aktuální pozice v čase)

| Prvek Timeline | Popis |
|----------------|-------|
| Playhead (zelená čára) | Ukazuje aktuální frame |
| Start/End frame | Rozsah animace (výchozí 1–250) |
| Žluté diamanty | Keyframy na timeline |
| Tlačítka přehrávání | Play, pauza, skok na začátek/konec |

### Nastavení rozsahu animace (frame range)

1. V Timeline panelu – vlevo dole: **Start Frame** (výchozí 1)
2. Vpravo dole: **End Frame** (výchozí 250)
3. Pro 5sekundovou animaci při 24 fps: End Frame = **120** (5 × 24)
4. Alternativa: Properties → Output → Frame Range

| Délka animace | FPS | End Frame |
|---------------|-----|-----------|
| 3 sekundy | 24 | 72 |
| 5 sekund | 24 | 120 |
| 10 sekund | 24 | 240 |
| 5 sekund | 30 | 150 |

### Vkládání keyframů – klávesa I

1. Vyberte objekt (např. kameru)
2. Na Timeline přesuňte playhead na požadovaný frame
3. Stiskněte **I** → zvolte typ keyframu:
   - **Location** – uloží pozici
   - **Rotation** – uloží rotaci
   - **Scale** – uloží velikost
   - **Location, Rotation & Scale** – uloží vše najednou (LocRotScale)
4. Posuňte playhead na jiný frame, změňte pozici/rotaci, a vložte další keyframe (**I**)

| Akce | Klávesa |
|------|---------|
| Vložit keyframe | **I** |
| Smazat keyframe | **Alt + I** |
| Přehrát animaci | **Spacebar** |
| Zastavit přehrávání | **Spacebar** (znovu) |
| Další frame | **Šipka doprava** |
| Předchozí frame | **Šipka doleva** |
| Skok na začátek | **Shift + Šipka doleva** |
| Skok na konec | **Shift + Šipka doprava** |

> **Tip pro výuku:** Udělejte rychlou ukázku – posuňte kostku z bodu A do bodu B pomocí dvou keyframů. Studenti uvidí, jak Blender automaticky vytvoří plynulý pohyb. Trvá to 30 sekund a efekt je „wow".

---

- Vyskakovací menu „Insert Keyframe Menu" po stisknutí I
- Volby: Location, Rotation, Scale, LocRotScale aj.
- Na Timeline panelu dole žlutý diamant (vložený keyframe)
- Vybraná kamera ve viewportu (oranžový obrys)

---

- Timeline panel s dvěma žlutými keyframy (frame 1 a frame 120)
- Zelený playhead uprostřed
- Start Frame = 1, End Frame = 120
- Ve viewportu viditelná dráha pohybu kamery (motion path)

---

## Fáze 5 – Společný projekt: Průlet kamery kolem domečku (25–30 min)

> **Poznámka pro učitele:** Tento projekt používá model domečku z Lekce 1. Pokud ho studenti nemají, připravte si uložený .blend soubor ke sdílení. Budujte krok po kroku, promítejte svůj Blender.

### Krok 1 – Příprava scény (3 min)
1. Otevřete soubor s modelem domečku z Lekce 1 (nebo přiložený .blend soubor)
2. Ujistěte se, že domeček je přibližně v **počátku** scény (0, 0, 0)
3. Pokud je daleko od počátku: vyberte domeček → **Alt + G** (resetovat pozici)
4. Zkontrolujte, že ve scéně je kamera (pokud ne: **Shift + A → Camera**)

### Krok 2 – Vytvoření kruhové dráhy (5 min)
1. Přidejte kruh: **Shift + A → Curve → Circle**
2. Zvětšete kruh: **S → 10 → Enter** (aby obklopil domeček s odstupem)
3. Zkontrolujte z pohledu shora (**Numpad 7**) – kruh by měl být kolem domečku
4. Případně posuňte kruh nahoru: **G → Z → 3 → Enter** (aby kamera nebyla na úrovni země)

---

- Pohled shora (Numpad 7)
- Domeček uprostřed scény
- Oranžová kruhová křivka obklopující domeček
- V Outlineru: objekty Camera, domecek, BezierCircle
- Kruh je viditelně větší než domeček (dostatečný odstup)

---

### Krok 3 – Přichycení kamery na dráhu – Follow Path (5 min)
1. **Vyberte kameru** (klik nebo Outliner)
2. Přejděte do Properties → **Object Constraint Properties** (ikona řetězu)
3. **Add Object Constraint → Follow Path**
4. V poli **Target** vyberte kruhovou křivku (**BezierCircle**)
5. Zaškrtněte **Follow Curve** (kamera se bude otáčet ve směru dráhy)
6. Klikněte na **Animate Path** (automaticky vytvoří animaci po dráze)

---

- Properties panel → Object Constraint Properties (ikona řetězu)
- Follow Path constraint s nastaveným Target: BezierCircle
- Zaškrtnutá volba Follow Curve
- Tlačítko Animate Path
- Ve viewportu kamera „sedící" na kruhové křivce

---

### Krok 4 – Nastavení kamery, aby se dívala na domeček (3 min)
1. Kamera nyní jezdí po kruhu, ale nedívá se na domeček
2. Vyberte kameru → Properties → Object Constraint Properties
3. **Add Object Constraint → Track To**
4. **Target** = domeček (objekt domečku)
5. **Track Axis** = **-Z**, **Up** = **Y** (standardní nastavení pro kameru)
6. Nyní se kamera vždy dívá směrem k domečku, ať je kdekoliv na dráze

---

- Properties panel s oběma constrainty: Follow Path + Track To
- Track To: Target = domeček, Track Axis = -Z, Up = Y
- Ve viewportu (Numpad 0): domeček vycentrovaný v záběru kamery
- Kamera se „dívá" na domeček z pozice na křivce

---

### Krok 5 – Nastavení focal length a depth of field (3 min)
1. Vyberte kameru → Properties → **Camera** (ikona kamery)
2. **Focal Length:** nastavte na **35 mm** (pěkný záběr celého domečku)
3. Zapněte **Depth of Field** → Focus Object = domeček
4. **F-Stop:** nastavte na **2.8** (mírné rozostření pozadí, ale ne přehnané)
5. Přepněte se do pohledu kamery (**Numpad 0**) a zkontrolujte záběr

### Krok 6 – Nastavení délky animace na 5 sekund (2 min)
1. V Timeline panelu nastavte: **Start Frame = 1**, **End Frame = 120**
2. Ověřte FPS: Properties → Output → **Frame Rate = 24 fps**
3. Výpočet: 5 sekund × 24 fps = 120 framů
4. V Follow Path constraintu zkontrolujte, že animace trvá 100 framů → upravte na **120** v Graph Editoru nebo přes Offset Factor keyframy

> **Tip pro výuku:** Pokud Animate Path nastavilo jinou délku, vyberte křivku BezierCircle → Properties → Object Data → Path Animation → **Frames = 120**.

### Krok 7 – Přehrání a kontrola animace (4 min)
1. Přesuňte playhead na frame 1: **Shift + Šipka doleva**
2. Přepněte do pohledu kamery: **Numpad 0**
3. Přehrajte animaci: **Spacebar**
4. Sledujte, jak kamera plynule objíždí domeček
5. Pokud je pohyb trhaný → Properties → Output → Frame Rate ověřte 24 fps
6. Zastavte: **Spacebar**

---

- Pohled kamery s domečkem z bočního úhlu (uprostřed animace)
- Depth of Field efekt – pozadí mírně rozostřené
- Timeline dole s playheadem na cca frame 60
- Composition guides (Thirds) viditelné přes záběr
- Celkový „filmový" dojem záběru

---

- Domeček uprostřed scény
- Kruhová křivka (dráha kamery) viditelná kolem domečku
- Kamera na křivce s vyznačeným směrem pohledu (čárkovaný kužel)
- Perspektivní pohled „zvenčí" (ne pohled kamery)
- Orientační osy v rohu viewportu

---

### Hotový průlet – shrnutí použitých nástrojů

| Krok | Použité nástroje a funkce |
|------|---------------------------|
| Dráha kamery | Shift + A → Curve → Circle, Scale |
| Pohyb kamery po dráze | Follow Path constraint, Animate Path |
| Zaměření na domeček | Track To constraint |
| Nastavení záběru | Focal Length 35 mm, Depth of Field, F-Stop 2.8 |
| Délka animace | Frame Range 1–120 (5 s při 24 fps) |
| Kontrola | Numpad 0, Spacebar |

---

## Fáze 6 – Samostatný projekt (20–25 min)

> **Zadání:** Vyberte si jednu ze tří animačních scén a vytvořte ji. Použijte keyframe animaci nebo Follow Path. Dbejte na správné nastavení kamery (focal length, depth of field) a kompozici záběru.

### Scéna A – Dramatický zoom na meč ⚔️
**Obtížnost:** ⭐⭐ (střední)

**Co procvičíte:** Keyframe animace pozice kamery, animace focal length, Depth of Field

**Zadání:**
- Kamera začíná na celkovém záběru scény (wide shot) a během 5 sekund plynule najíždí na detail čepele meče
- Focal length se animuje z 24 mm na 85 mm (dolly zoom efekt)
- Depth of Field zapnutý – na konci animace je ostrý jen meč, pozadí rozmazané

**Postup (nápověda):**
1. Otevřete/vytvořte scénu s mečem (z Lekce 1 nebo nový jednoduchý model)
2. Frame 1: kameru umístěte daleko od meče, focal length = 24 mm → **I → LocRotScale** + najet kurzorem na Focal Length → **I**
3. Frame 120: kameru přesuňte blízko k meči, focal length = 85 mm → **I → LocRotScale** + keyframe na focal length
4. DoF: Focus Object = meč, F-Stop = 1.8
5. Přehrajte a zkontrolujte (**Spacebar**)

### Scéna B – Produktová rotace stolu (product spin) 🪑
**Obtížnost:** ⭐ (lehčí)

**Co procvičíte:** Follow Path, Track To constraint, nastavení kamery pro produktové video

**Zadání:**
- Model stolu (z Lekce 1) rotuje na místě nebo kamera ho objíždí – „produktové video"
- Kamera na fixní výšce, plynulý 360° objezd za 5 sekund
- Čisté studio pozadí (bílá/šedá plocha pod stolem)

**Postup (nápověda):**
1. Otevřete scénu se stolem z Lekce 1
2. Přidejte plochu pod stůl: **Shift + A → Mesh → Plane** → **S → 20** (velká podlaha)
3. Přidejte kruhovou dráhu: **Shift + A → Curve → Circle** → **S → 8**
4. Výška kamery: posuňte kruh nahoru **G → Z → 2**
5. Follow Path + Track To (stejný postup jako ve společném projektu)
6. Focal Length: **50 mm** (přirozený produktový záběr)
7. DoF: f/4.0 – jemné rozostření

### Scéna C – Průchod místností (walk-through) 🚪
**Obtížnost:** ⭐⭐⭐ (těžší)

**Co procvičíte:** Keyframe animace na více framech, plynulý pohyb kamery, focal length pro interiér

**Zadání:**
- Vytvořte jednoduchou místnost (4 stěny, podlaha, stůl a židle uvnitř) a animujte průchod kamery od dveří ke stolu
- Kamera se pohybuje plynule vpřed a mírně se otáčí (jako byste šli po chodbě)
- 5sekundová animace s 3–4 keyframy pro pozici kamery

**Postup (nápověda):**
1. Vytvořte místnost: kostka → Edit Mode → smazat horní a jednu boční plochu (dveře) → **S** zvětšit
2. Přidejte dovnitř stůl a židli (jednoduché tvary – kostka + válce pro nohy)
3. Kameru umístěte ke „dveřím" (otevřená stěna)
4. Frame 1: kamera u dveří, focal length 24 mm (širokoúhlý interiér) → **I → LocRotScale**
5. Frame 40: kamera uprostřed místnosti, mírně otočená → **I → LocRotScale**
6. Frame 80: kamera blíž ke stolu → **I → LocRotScale**
7. Frame 120: detail stolu → **I → LocRotScale**
8. DoF: Focus Distance animujte (na začátku zaostřeno daleko, na konci blízko)
9. Přehrajte a vyhlazujte pohyb v **Graph Editoru** (volitelné, pokročilé)

---

## Fáze 7 – Shrnutí a závěr (5 min)

### Co jsme se dnes naučili
- **Ovládání kamery:** Numpad 0 (pohled kamery), Ctrl + Alt + Numpad 0 (kamera na aktuální pohled)
- **Vlastnosti kamery:** Focal Length, Depth of Field (F-Stop), Clipping
- **Kompozice:** Rule of Thirds, Composition Guides v Blenderu
- **Keyframe animace:** klávesa I, Timeline panel, přehrávání Spacebar
- **Follow Path:** pohyb kamery po křivce, Track To constraint
- **Nastavení animace:** Frame Range, FPS, délka v sekundách

### Klávesové zkratky – tahák

| Zkratka | Funkce |
|---------|--------|
| Numpad 0 | Pohled kamery |
| Ctrl + Alt + Numpad 0 | Kamera na aktuální pohled |
| N → View → Camera to View | Zamknout kameru k pohybu viewportu |
| I | Vložit keyframe |
| Alt + I | Smazat keyframe |
| Spacebar | Přehrát / zastavit animaci |
| Šipka doprava / doleva | Další / předchozí frame |
| Shift + Šipka doleva | Skok na začátek animace |
| Shift + Šipka doprava | Skok na konec animace |
| Shift + A → Camera | Přidat kameru |
| Shift + A → Curve → Circle | Přidat kruhovou křivku |
| G / R / S | Posun / Rotace / Scale (pro kameru i objekty) |
| Ctrl + Z | Zpět (Undo) |

---

## Poznámky pro učitele

### Příprava před lekcí
- [ ] Mít připravený uložený .blend soubor s domečkem z Lekce 1 (pro studenty, kteří ho nemají)
- [ ] Ověřit, že na všech počítačích funguje Numpad (nebo zapnout Emulate Numpad: Edit → Preferences → Input)
- [ ] Připravit si 2–3 ukázkové záběry z filmů pro ukázku Rule of Thirds
- [ ] Mít připravený hotový příklad průletu kamery (pro ukázku výsledku na začátku lekce)
- [ ] Vyzkoušet si Animate Path a Follow Path constraint předem – nastavení se občas chová neintuitivně
- [ ] Připravit jednoduché pozadí/podlahu pro scénu (Plane + materiál), aby záběry nevypadaly „prázdně"

### Tipy pro průběh výuky
- **Ukázka na začátku:** Přehrajte hotovou animaci průletu (5 sekund) hned na začátku lekce. Studenti uvidí cíl a budou motivovaní
- **Tempo:** Fáze 1–4 jsou teoretické – prokládejte je praktickými ukázkami. Po každém konceptu nechte studenty zkusit na vlastním počítači
- **Numpad problémy:** Pokud studenti nemají numpad, ukažte alternativy: `View → Viewpoint → Camera` místo Numpad 0, nebo zapněte Emulate Numpad
- **Camera to View:** Upozorněte studenty, ať ho po použití vypnou – jinak se kamera bude nechtěně pohybovat
- **Follow Path nefunguje:** Nejčastější chyba – studenti zapomenou kliknout na **Animate Path** nebo mají špatný Target. Projděte třídou a zkontrolujte

### Nejčastější chyby studentů
| Chyba | Příčina | Řešení |
|-------|---------|--------|
| Kamera se nehýbe po dráze | Nekliknuto Animate Path | Kliknout Animate Path v Follow Path constraintu |
| Kamera se dívá špatným směrem | Chybí Track To constraint | Přidat Track To s Target na domeček |
| V pohledu kamery nic nevidím | Špatný Clipping nebo kamera daleko | Zvětšit Clip End nebo přesunout kameru blíž |
| Animace je příliš rychlá/pomalá | Špatný Frame Range nebo FPS | Nastavit End Frame = délka × FPS |
| Depth of Field nevidím | DoF se zobrazuje jen v renderovaném náhledu | Přepnout Viewport Shading na Rendered (Z → Rendered) |
| Keyframe se nevložil | Kurzor nebyl nad viewportem při stisknutí I | Ujistit se, že myš je nad 3D viewportem |
| Pohyb kamery je trhaný | Málo keyframů nebo lineární interpolace | Přidat více keyframů nebo změnit interpolaci na Bézier v Graph Editoru |

### Hodnocení samostatného projektu

| Kritérium | Body |
|-----------|------|
| Animace je plynulá a trvá cca 5 sekund | 2 |
| Správné nastavení kamery (focal length, DoF) | 2 |
| Dobrá kompozice záběru (objekt není uprostřed/oříznutý) | 2 |
| Použití keyframů nebo Follow Path constraintu | 2 |
| Kreativita a celkový dojem | 2 |
| **Celkem** | **10** |

---

> **Příští lekce:** Lekce 4 – Materiály a textury. Přidáme domečku barvy, textury dřeva a střechy, a naučíme se základy shadingu v Blenderu!

