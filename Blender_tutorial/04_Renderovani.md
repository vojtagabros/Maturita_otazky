# Lekce 4 – Renderování

> **Délka lekce:** cca 60–90 minut
> **Cíl:** Studenti pochopí rozdíl mezi render enginy Eevee a Cycles, naučí se základní nastavení renderu (rozlišení, sampling, denoise), vyrenderují obrázek i krátkou animaci a uloží výstupy ve správném formátu.

---

## Přehled lekce

| Fáze | Obsah | Čas |
|------|-------|-----|
| 1 | Render enginy – Eevee vs Cycles | 10 min |
| 2 | Základní nastavení renderu | 10 min |
| 3 | Render obrázku (F12) a uložení | 10 min |
| 4 | Render animace – Output Properties a formát | 10 min |
| 5 | Tipy – viewport preview a compositing | 5 min |
| 6 | Společný projekt – Renderování scény domečku | 20–25 min |
| 7 | Samostatný projekt (výběr ze 3 úkolů) | 15–20 min |
| 8 | Shrnutí a závěr | 5 min |

---

## Fáze 1 – Render enginy: Eevee vs Cycles (10 min)

### Co je renderování
- **Renderování** = proces, při kterém Blender vypočítá finální obrázek/animaci z 3D scény
- Blender nabízí dva hlavní render enginy: **Eevee** a **Cycles**
- Nastavení se provádí v **Render Properties** (ikona fotoaparátu v Properties panelu)

### Eevee
- **Rasterizační** engine – podobný princip jako herní enginy
- **Velmi rychlý** – výsledek téměř v reálném čase
- Méně realistické odrazy a stíny (ale pro většinu účelů stačí)
- Vhodný pro: animace, stylizované scény, rychlé náhledy, herní assety
- Od verze Blender 4.0 přejmenován na **Eevee Next** s vylepšeními

### Cycles
- **Path-tracing** engine – simuluje fyzikální chování světla
- **Výrazně pomalejší** – výpočet může trvat minuty až hodiny
- Fotorealistické výsledky – reálné odrazy, caustics, globální osvětlení
- Podporuje GPU rendering (CUDA/OptiX pro NVIDIA, HIP pro AMD)
- Vhodný pro: fotorealistické vizualizace, product rendery, filmové efekty

### Kdy co použít – přehled

| Vlastnost | Eevee | Cycles |
|-----------|-------|--------|
| Rychlost | Velmi rychlý (sekundy) | Pomalý (minuty–hodiny) |
| Realističnost | Dobrá, stylizovaná | Fotorealistická |
| Odrazy | Aproximované (Screen Space) | Fyzikálně přesné |
| Stíny | Aproximované | Fyzikálně přesné |
| GPU využití | Nízké | Vysoké (doporučeno) |
| Ideální pro | Animace, hry, náhledy | Vizualizace, product, film |

### Jak přepnout render engine
1. Otevřete **Render Properties** (ikona fotoaparátu v Properties panelu)
2. V rozbalovacím menu **Render Engine** vyberte **Eevee** nebo **Cycles**

> **Tip pro výuku:** Mějte připravenou stejnou scénu a přepínejte mezi Eevee a Cycles přímo před studenty. Nechte je porovnat kvalitu i čas renderování. Rozdíl je okamžitě viditelný.

---

- Properties panel na pravé straně
- Ikona fotoaparátu (Render Properties) zvýrazněná
- Rozbalovací menu s možnostmi Eevee / Cycles
- Aktuálně vybraný engine

---

- Vlevo render z Eevee s popiskem „Eevee – 2 sekundy"
- Vpravo render z Cycles s popiskem „Cycles – 45 sekund"
- Viditelný rozdíl ve stínech (Cycles má měkčí, přirozenější stíny)
- Viditelný rozdíl v odrazech (pokud scéna obsahuje lesklé materiály)
- Oba rendery ze stejného úhlu kamery

---

## Fáze 2 – Základní nastavení renderu (10 min)

### Rozlišení (Resolution)
1. Otevřete **Output Properties** (ikona tiskárny v Properties panelu)
2. Sekce **Format** (nebo **Dimensions** ve starších verzích):
   - **Resolution X:** šířka v pixelech (výchozí 1920)
   - **Resolution Y:** výška v pixelech (výchozí 1080)
   - **%** (Resolution percentage): škálování – 50 % = poloviční rozlišení (rychlejší pro testování)

| Rozlišení | Použití |
|-----------|---------|
| 1920 × 1080 (Full HD) | Standardní výstup, prezentace |
| 3840 × 2160 (4K) | Vysoká kvalita, tisk |
| 960 × 540 (50 %) | Testovací rendery |
| 1080 × 1080 | Instagram, čtvercový formát |

> **Tip pro výuku:** Při testování nastavte Resolution % na 25–50 %. Render bude mnohem rychlejší a studenti nebudou čekat. Finální render pak na 100 %.

### Sampling (Vzorkování)
- **Sampling** = kolikrát engine vypočítá barvu každého pixelu
- Více vzorků = čistší obraz, ale delší render
- Nastavuje se v **Render Properties → Sampling**

#### Sampling v Cycles
| Parametr | Popis | Doporučená hodnota |
|----------|-------|--------------------|
| **Render Samples** | Počet vzorků pro finální render | 128–512 (začátečníci: 128) |
| **Viewport Samples** | Počet vzorků pro náhled ve viewportu | 32–64 |
| **Denoise** | Odšumování – odstraní zrnitost | Zapnout (OpenImageDenoise) |

#### Sampling v Eevee
| Parametr | Popis | Doporučená hodnota |
|----------|-------|--------------------|
| **Render Samples** | Počet vzorků | 64–128 (Eevee je rychlý) |
| **Viewport Samples** | Náhledové vzorky | 16–32 |

### Denoise (Odšumování)
- Cycles při nízkém počtu vzorků vytváří **šum** (zrnitý obraz)
- **Denoise** tento šum odstraní a obraz vyhladí
- Nastavení: **Render Properties → Sampling → Denoise** → zaškrtnout
- Doporučený denoiser: **OpenImageDenoise** (nejlepší výsledky)
- Alternativy: OptiX (pouze NVIDIA GPU), Automatic

> **Tip pro výuku:** Ukažte studentům render s 16 vzorky BEZ denoise (hodně zrnitý) a pak TEN SAMÝ render s denoise zapnutým. Rozdíl je dramatický a studenti okamžitě pochopí, proč je denoise důležitý.

---

- Output Properties panel (ikona tiskárny)
- Pole Resolution X = 1920, Resolution Y = 1080
- Posuvník/pole pro % (nastaven na 100 %)
- Sekce Frame Range (Start, End) – zatím jen zmínit

---

- Render Properties panel (ikona fotoaparátu)
- Sekce Sampling rozbalená
- Render Samples nastavené na 128
- Viewport Samples nastavené na 32
- Denoise zaškrtnuté, denoiser nastaven na OpenImageDenoise
- Zvýrazněné klíčové hodnoty šipkami

---

- Tři rendery vedle sebe nebo pod sebou s popisky
- (A) viditelně zrnitý/šumový obraz – „16 samples, denoise OFF"
- (B) čistý obraz i při 16 vzorcích – „16 samples, denoise ON"
- (C) nejčistší obraz – „256 samples, denoise ON"
- Detail/výřez na problematickou oblast (stín, odraz, tmavý kout)

---

## Fáze 3 – Render obrázku: F12 a uložení (10 min)

### Spuštění renderu
| Akce | Způsob |
|------|--------|
| Render obrázku | **F12** nebo menu **Render → Render Image** |
| Zrušení renderu | **Esc** |
| Render s animací | **Ctrl + F12** |

### Postup krok za krokem
1. Zkontrolujte, že máte správně nastavenou **kameru** (pohled kamery: **Numpad 0**)
2. Ověřte nastavení renderu (engine, sampling, rozlišení)
3. Stiskněte **F12**
4. Počkejte, až render doběhne (progress bar nahoře)
5. Otevře se okno **Blender Render** s výsledkem

### Uložení renderovaného obrázku
1. V okně s renderem klikněte **Image → Save As** (nebo **Alt + S**)
2. Vyberte formát:
   - **PNG** – bezztrátový, podporuje průhlednost (alfa kanál), větší soubor
   - **JPEG** – ztrátový, menší soubor, bez průhlednosti
   - **EXR/HDR** – pro post-processing, 32-bit barevná hloubka
3. Zvolte cestu a název souboru
4. Klikněte **Save As Image**

| Formát | Výhody | Nevýhody | Kdy použít |
|--------|--------|----------|------------|
| PNG | Bezztrátový, alfa kanál | Větší soubor | Finální obrázky, průhledné pozadí |
| JPEG | Malý soubor | Ztrátový, žádná alfa | Web, náhledy, sociální sítě |
| EXR | 32-bit, HDR data | Velký soubor, potřeba editoru | Compositing, profesionální workflow |

> **Tip pro výuku:** Upozorněte studenty, že pokud render uložit ZAPOMENOU a zavřou okno, obrázek je PRYČ. Blender ho neukládá automaticky. Naučte je reflexivně po renderu hned ukládat.

---

- Hotový render scény domečku v okně Blender Render
- Otevřené menu Image → Save As (zvýrazněné)
- Progress bar nahoře ukazující 100 % / dokončeno
- V dolní části informace o rozlišení a čase renderu

---

- File Browser (prohlížeč souborů) v Blenderu
- Rozbalovací menu formátu souboru (zvýrazněné) – PNG vybrané
- Pole pro název souboru dole
- Navigace ve složkách vlevo
- Tlačítko „Save As Image" vpravo dole

---

## Fáze 4 – Render animace: Output Properties a formát (10 min)

### Nastavení animace pro render
1. Otevřete **Output Properties** (ikona tiskárny)
2. Nastavte **Frame Range:**
   - **Frame Start:** první snímek (obvykle 1)
   - **Frame End:** poslední snímek (např. 120 = 5 sekund při 24 fps)
   - **Frame Step:** po kolika snímcích renderovat (1 = každý)
3. Nastavte **Frame Rate** v **Output Properties → Format → Frame Rate** (24 fps = film, 30 fps = video)

### Výstupní formát pro animaci
- V **Output Properties → Output** nastavte:
  - **Cestu** kam se bude ukládat (klikněte na ikonu složky)
  - **File Format:** vyberte formát

| Formát | Typ | Popis |
|--------|-----|-------|
| **PNG Sequence** | Obrázky | Každý snímek jako PNG – bezpečné, lze přerušit a pokračovat |
| **FFmpeg Video** | Video | Přímo video soubor – pohodlné, ale nelze přerušit |
| **AVI Raw** | Video | Nekomprimované video – obrovské soubory |

### Nastavení FFmpeg/MP4 (nejčastější varianta)
1. File Format: **FFmpeg Video**
2. Klikněte na rozbalení **Encoding**
3. **Container:** MPEG-4
4. **Video Codec:** H.264
5. **Output Quality:** Medium nebo High
6. **Audio Codec:** AAC (pokud máte zvuk)

### Spuštění renderu animace
| Akce | Způsob |
|------|--------|
| Render animace | **Ctrl + F12** nebo **Render → Render Animation** |
| Zrušení | **Esc** |

> **Pozor:** Animace renderuje KAŽDÝ snímek zvlášť. 120 snímků = 120× render. Pokud jeden snímek trvá 30 sekund, celá animace = 60 minut. Použijte nízké rozlišení a sampling pro testování!

> **Tip pro výuku:** Pro první test animace nastavte Resolution % na 25 %, Sampling na minimum a Frame End na 30 (cca 1 sekunda). Studenti uvidí výsledek rychle a pochopí princip. Finální render nechte na konci hodiny nebo jako domácí úkol.

---

- Output Properties panel (ikona tiskárny)
- Pole Output path s cestou ke složce (např. //renders/)
- File Format: FFmpeg Video (zvýrazněné)
- Rozbalená sekce Encoding:
  - Container: MPEG-4
  - Video Codec: H.264
  - Output Quality: Medium
- Frame Range: Start 1, End 120

---

- Render okno s rozpracovaným snímkem
- Progress bar nahoře: „Fra: 47/120" nebo podobný indikátor
- Informace o čase renderu aktuálního snímku
- Informace o celkovém odhadovaném čase (pokud dostupné)

---

## Fáze 5 – Tipy: viewport preview a compositing (5 min)

### Rendered Mode ve viewportu
- Není nutné vždy renderovat přes F12 – můžete si zobrazit **náhled přímo ve viewportu**
- V pravém horním rohu viewportu klikněte na **zobrazovací režimy** (4 kroužky) nebo klávesou **Z**:

| Režim | Klávesa Z → výběr | Popis |
|-------|-------------------|-------|
| Solid | výchozí | Šedý náhled, nejrychlejší |
| Material Preview | - | Náhled materiálů s HDRI osvětlením |
| Wireframe | - | Drátěný model |
| **Rendered** | - | Živý náhled renderu ve viewportu |

- **Rendered mode** zobrazuje scénu tak, jak bude vypadat po renderu (v reálném čase pro Eevee, postupně se zpřesňuje pro Cycles)
- Ideální pro ladění materiálů, světel a kompozice bez čekání na plný render

### Compositing (jen zmínka)
- Blender má zabudovaný **Compositor** – záložka **Compositing** v horní liště
- Umožňuje post-processing přímo v Blenderu: úprava barev, bloom, glare, vignetting, color grading
- Pro tuto lekci jen zmíňte, že existuje – podrobněji v pokročilých lekcích
- Zapnutí: záložka Compositing → zaškrtnout **Use Nodes**

> **Tip pro výuku:** Ukažte studentům Rendered mode ve viewportu – je to nejrychlejší způsob, jak zkontrolovat, jestli scéna vypadá dobře. Compositing pouze zmíňte a ukažte na 30 sekund rozhraní – studenti by neměli trávit čas jeho nastavováním.

---

- Čtyři verze stejné scény v mřížce 2×2
- Wireframe: drátěný model, průhledný
- Solid: šedý/barevný náhled bez osvětlení
- Material Preview: materiály s HDRI osvětlením
- Rendered: plný render preview
- Zvýrazněné ikony 4 režimů v rohu viewportu

---

## Fáze 6 – Společný projekt: Renderování scény domečku (20–25 min)

> **Poznámka pro učitele:** Studenti by měli mít hotovou scénu domečku z předchozích lekcí (model z Lekce 1, materiály z Lekce 2, osvětlení z Lekce 3). Pokud někdo scénu nemá, připravte si soubor ke sdílení.

### Část A – Render obrázku v Eevee (8 min)

#### Krok 1 – Kontrola scény
1. Otevřete soubor se scénou domečku z předchozích lekcí
2. Přepněte do pohledu kamery: **Numpad 0**
3. Zkontrolujte, že kamera zabírá celou scénu (pokud ne: vyberte kameru → **G** → posunout)
4. Přepněte viewport do **Rendered** mode (klávesa **Z** → Rendered) – rychlý náhled

#### Krok 2 – Nastavení Eevee renderu
1. **Render Properties** → Render Engine: **Eevee**
2. Sampling → Render: **64**
3. **Output Properties** → Resolution: **1920 × 1080** → %: **100**

#### Krok 3 – Render a uložení
1. Stiskněte **F12**
2. Počkejte na dokončení (Eevee: cca 2–5 sekund)
3. **Image → Save As** (Alt + S)
4. Formát: **PNG**
5. Uložte jako `domeček_eevee.png`

> **Tip pro výuku:** Zapište čas renderu na tabuli. Studenti ho budou porovnávat s Cycles.

### Část B – Render obrázku v Cycles (8 min)

#### Krok 4 – Přepnutí na Cycles
1. **Render Properties** → Render Engine: **Cycles**
2. Pokud máte NVIDIA GPU: **Render Properties → Device → GPU Compute**
   - Povolení GPU: **Edit → Preferences → System → CUDA/OptiX** → zaškrtnout GPU
3. Sampling → Render: **128**
4. Denoise: **zaškrtnout** → Denoiser: **OpenImageDenoise**

#### Krok 5 – Render a uložení
1. Stiskněte **F12**
2. Počkejte na dokončení (Cycles: cca 20–60 sekund, záleží na HW)
3. **Image → Save As** (Alt + S)
4. Uložte jako `domeček_cycles.png`

#### Krok 6 – Porovnání
1. Otevřete oba obrázky vedle sebe (v prohlížeči obrázků nebo přímo v Blenderu)
2. Porovnejte: stíny, odrazy, celkový dojem, čas renderu
3. Diskuze se studenty: „Který vypadá lépe? Stojí ten rozdíl za ten čas navíc?"

---

- Render Properties: Device = GPU Compute (zvýrazněné)
- Preferences okno: System → CUDA nebo OptiX
- Zaškrtnutý GPU (název grafické karty viditelný)
- Šipky propojující obě nastavení

---

### Část C – Render krátké animace jako MP4 (8 min)

#### Krok 7 – Příprava animace
1. Přepněte zpět na **Eevee** (pro rychlost)
2. Zkontrolujte, že máte animaci kamery z Lekce 3 (pokud ne: jednoduše nastavte kameru na 2 keyframy – počáteční a koncová pozice)
3. Přehrajte animaci ve viewportu: **Spacebar** (ověření)

#### Krok 8 – Nastavení výstupu animace
1. **Output Properties:**
   - Frame Start: **1**
   - Frame End: **72** (3 sekundy při 24 fps)
   - Frame Rate: **24 fps**
   - Resolution %: **50** (pro rychlost – testovací render)
2. **Output → Output path:** zvolte složku (např. `//renders/`)
3. **File Format:** FFmpeg Video
4. **Encoding:**
   - Container: **MPEG-4**
   - Video Codec: **H.264**
   - Output Quality: **Medium**

#### Krok 9 – Render animace
1. Stiskněte **Ctrl + F12**
2. Počkejte na dokončení (cca 1–3 minuty pro 72 snímků v Eevee při 50 %)
3. Najděte výstupní soubor ve zvolené složce
4. Přehrajte video (dvojklik na soubor)

> **Tip pro výuku:** Zatímco animace renderuje, projděte třídu a pomozte studentům, kteří měli problémy s nastavením. Render v Eevee při 50 % by měl být dostatečně rychlý.

---

- Celé rozhraní Blenderu (ne jen jeden panel)
- Čísla 1–4 označující klíčové oblasti nastavení
- Šipky ukazující pořadí kroků
- Timeline dole s viditelným rozsahem snímků (1–72)
- Render Properties a Output Properties viditelné vpravo

---

## Fáze 7 – Samostatný projekt (15–20 min)

> **Zadání:** Vyberte si jeden z následujících úkolů a zpracujte ho. Použijte znalosti z dnešní lekce i z předchozích lekcí (materiály, osvětlení).

### Úkol A – Fotorealistický product render hrnku

**Obtížnost:** ⭐⭐ (střední)

**Co procvičíte:** Cycles, vysoký sampling, denoise, kompozice, uložení PNG

**Zadání:**
1. Otevřete model hrnku z Lekce 1 (Objekt A – Hrnek na kávu)
2. Ujistěte se, že hrnek má materiály (z Lekce 2) a osvětlení (z Lekce 3)
3. Nastavte **Cycles** jako render engine
4. Sampling: **256** vzorků, Denoise: **ON**
5. Rozlišení: **1920 × 1080** (100 %)
6. Přidejte jednoduché pozadí – rovinu pod hrnkem s neutrálním materiálem (světle šedá/bílá)
7. Nastavte kameru tak, aby hrnek vypadal jako z katalogu (mírně shora, ze strany)
8. Vyrenderujte (**F12**) a uložte jako **PNG**
9. **Bonus:** Vyrenderujte stejnou scénu v Eevee a porovnejte výsledky

**Hodnocení:**
| Kritérium | Body |
|-----------|------|
| Správné nastavení Cycles (sampling, denoise) | 2 |
| Kvalitní kompozice (kamera, pozadí) | 3 |
| Obrázek uložen ve správném formátu | 2 |
| Celkový vizuální dojem | 3 |
| **Celkem** | **10** |

### Úkol B – Cinematický záběr meče

**Obtížnost:** ⭐⭐⭐ (těžší)

**Co procvičíte:** Cycles, dramatické osvětlení, nízký úhel kamery, vysoké rozlišení

**Zadání:**
1. Otevřete model meče z Lekce 1 (Objekt C – Meč/Dýka)
2. Upravte osvětlení pro dramatický efekt:
   - Hlavní světlo (Key Light) z jedné strany – silné, teplé
   - Výplňové světlo (Fill Light) z druhé strany – slabší, chladnější
   - Zadní světlo (Rim Light) – pro siluetu
3. Nastavte **Cycles**, Sampling: **256**, Denoise: **ON**
4. Kamera: nízký úhel (jako by se divák díval na meč zdola nahoru)
5. Pozadí: tmavé (černé nebo tmavě modré)
6. Rozlišení: **1920 × 1080**
7. Vyrenderujte a uložte jako **PNG**
8. **Bonus:** Zkuste přidat World shader s tmavým HDRI pro atmosféru

**Hodnocení:**
| Kritérium | Body |
|-----------|------|
| Dramatické osvětlení (3-point light) | 3 |
| Zajímavý úhel kamery | 2 |
| Správné nastavení Cycles | 2 |
| Celkový vizuální dojem a atmosféra | 3 |
| **Celkem** | **10** |

### Úkol C – Galerie porovnání Eevee vs Cycles

**Obtížnost:** ⭐⭐ (střední)

**Co procvičíte:** Oba enginy, různá nastavení, organizace výstupů, analytické myšlení

**Zadání:**
1. Použijte jakoukoliv scénu z předchozích lekcí (domeček, hrnek, stůl nebo meč)
2. Vyrenderujte scénu ve **4 variantách:**
   - **Eevee** – výchozí nastavení (64 samples)
   - **Cycles** – nízký sampling (32 samples, BEZ denoise)
   - **Cycles** – nízký sampling (32 samples, S denoise)
   - **Cycles** – vysoký sampling (256 samples, S denoise)
3. Všechny 4 rendery uložte jako PNG s popisnými názvy:
   - `porovnani_01_eevee_64.png`
   - `porovnani_02_cycles_32_no_denoise.png`
   - `porovnani_03_cycles_32_denoise.png`
   - `porovnani_04_cycles_256_denoise.png`
4. Zapište si čas renderu pro každou variantu
5. **Bonus:** Sestavte jednoduchou tabulku nebo prezentaci s porovnáním (čas vs kvalita)

**Hodnocení:**
| Kritérium | Body |
|-----------|------|
| Všechny 4 rendery hotové a uložené | 4 |
| Správné pojmenování souborů | 2 |
| Zapsané časy renderu | 2 |
| Vlastní zhodnocení/porovnání (ústní nebo písemné) | 2 |
| **Celkem** | **10** |

---

## Fáze 8 – Shrnutí a závěr (5 min)

### Co jsme se dnes naučili
- Rozdíl mezi **Eevee** (rychlý, stylizovaný) a **Cycles** (pomalý, fotorealistický)
- Nastavení **rozlišení** (Resolution X/Y, procenta)
- **Sampling** – vliv na kvalitu a čas renderu
- **Denoise** – odšumování pro čistší obraz při nižším samplingu
- Render obrázku (**F12**) a uložení (**Image → Save As**)
- Render animace (**Ctrl + F12**) s nastavením FFmpeg/MP4
- **Viewport Rendered mode** pro rychlý náhled
- Zmínka o **Compositing** záložce

### Klávesové zkratky – tahák

| Zkratka | Funkce |
|---------|--------|
| **F12** | Render obrázku |
| **Ctrl + F12** | Render animace |
| **Esc** | Zrušení renderu |
| **Alt + S** (v render okně) | Uložit obrázek |
| **Numpad 0** | Pohled kamery |
| **Z** | Menu zobrazovacích režimů viewportu |
| **Ctrl + Z** | Zpět (Undo) |
| **Spacebar** | Přehrát animaci ve viewportu |

### Důležité zkratky nastavení – přehled

| Nastavení | Kde najít |
|-----------|-----------|
| Render Engine | Render Properties → Render Engine |
| Sampling | Render Properties → Sampling |
| Denoise | Render Properties → Sampling → Denoise |
| Rozlišení | Output Properties → Format → Resolution |
| Frame Range | Output Properties → Format → Frame Start/End |
| Výstupní formát | Output Properties → Output → File Format |
| FFmpeg nastavení | Output Properties → Output → Encoding |
| GPU aktivace | Edit → Preferences → System → CUDA/OptiX |

---

## Poznámky pro učitele

### Příprava před lekcí
- [ ] Ověřit, že na školních počítačích funguje Cycles (některé staré PC nemají podporu GPU – Cycles pak běží na CPU a je velmi pomalý)
- [ ] Připravit scénu domečku se všemi materiály a světly (pro studenty, kteří nemají svou)
- [ ] Otestovat čas renderu na školním HW – podle toho upravit doporučený sampling a rozlišení
- [ ] Vytvořit složku pro ukládání renderů (např. na sdíleném disku nebo ploše)
- [ ] Připravit si porovnávací rendery Eevee vs Cycles pro úvodní ukázku
- [ ] Mít připravený krátký hotový render animace jako ukázku finálního výsledku

### Tipy pro průběh výuky
- **Hardware:** Pokud školní počítače nemají GPU, používejte primárně Eevee. Cycles na CPU je použitelný jen s velmi nízkým samplingem (32–64) a denoise
- **Čekání na render:** Během renderování Cycles promluvte o teorii (jak path tracing funguje, proč je pomalý) nebo projděte třídu
- **Čas:** Fáze renderu animace může být časově náročná. Pokud nestíháte, nastavte jen 24 snímků (1 sekunda) nebo Resolution % na 25 %
- **Nejčastější chyby studentů:**
  - Zapomenou uložit render (zavřou okno a obrázek je pryč)
  - Nastaví příliš vysoký sampling → render trvá věčně → Esc a snížit
  - Nevidí rozdíl Eevee/Cycles, protože scéna nemá lesklé materiály ani komplexní osvětlení
  - Render animace ukládají bez nastavení cesty → soubor se uloží do /tmp/ nebo na neočekávané místo
  - Zapomenou přepnout na FFmpeg → renderují se jednotlivé PNG místo videa
- **Pokročilejší studenti:** Ať zkusí vyšší rozlišení (4K), přidají HDRI pozadí nebo experimentují s Compositing uzly
- **Slabší studenti:** Stačí jim vyrenderovat jednu Eevee fotku a uložit ji. Animaci mohou přeskočit

### Hodnocení samostatného projektu

| Kritérium | Body |
|-----------|------|
| Správné nastavení render enginu a samplingu | 2 |
| Kvalitní kompozice (kamera, osvětlení) | 3 |
| Obrázek/animace uložen ve správném formátu | 2 |
| Celkový vizuální dojem výstupu | 3 |
| **Celkem** | **10** |

### Časová záloha
Pokud zbyde čas, můžete ukázat:
- **Render Region** (Ctrl + B v render okně) – renderování jen části obrázku pro testování
- **View Layer Properties** – renderování s průhledným pozadím (Film → Transparent)
- **Stamp** nastavení – automatické popisky na renderu (čas, frame, soubor)

---

> **Příští lekce:** Lekce 5 – Pokročilé techniky. Podíváme se na sculpting, particle systémy a pokročilé modifikátory pro tvorbu složitějších scén!

