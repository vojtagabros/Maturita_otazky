# 20. Umělá inteligence (Artificial Intelligence – AI)

> Souvisí s: [[19_Programovani]] | [[02_Datova_uloziste]] | [[17_Kyberneticke_utoky]] | [[10_Firemni_IS]] | [[12_Problematika_3D]]

---

## a) Vymezení problematiky

### Co je umělá inteligence?
**Umělá inteligence (AI)** je odvětví informatiky zabývající se tvorbou systémů schopných provádět úlohy, které typicky vyžadují lidskou inteligenci – jako je vnímání, uvažování, učení, rozhodování, porozumění přirozenému jazyku a tvorba.

**Definice (John McCarthy, 1956 – otec AI):** „Věda a technika vytváření inteligentních strojů, zejména inteligentních počítačových programů."

### Historický vývoj AI

- **1943:** McCulloch-Pitts model neuronu – matematický model biologického neuronu.
- **1950:** Alan Turing – **Turingův test**: může stroj konverzovat nerozeznatelně od člověka? Článek „Computing Machinery and Intelligence".
- **1956:** **Dartmouth Conference** – McCarthy zavádí termín „Artificial Intelligence". Počátek jako akademická disciplína.
- **50.–70. léta – Zlatý věk AI (1. vlna):** optimismus, symbolická AI, expertní systémy, první chatboty (ELIZA, 1966).
- **70.–80. léta – 1. AI Winter:** přehnané sliby, nedostatečný hardware, omezené financování.
- **80. léta:** oživení – expertní systémy v průmyslu, Lisp stroje.
- **90. léta – 2. AI Winter:** expertní systémy příliš drahé na údržbu, opět útlum.
- **1997:** Deep Blue (IBM) porazil Garriho Kasparova v šachu.
- **2006:** Geoffrey Hinton – deep learning, pre-training deep neural networks.
- **2012: AlexNet** – průlom v rozpoznávání obrazu (ImageNet), začátek éry hlubokého učení.
- **2016:** AlphaGo (DeepMind/Google) porazil mistra světa v Go – hra považovaná za „příliš složitou pro AI".
- **2017:** Transformer architektura (Vaswani et al., Google) – základ moderních LLM.
- **2020:** GPT-3 (OpenAI) – LLM s 175 miliardami parametrů.
- **2022:** **ChatGPT (OpenAI)** – 100 milionů uživatelů za 2 měsíce, průlom do masového povědomí.
- **2024–2025:** GPT-4o, Claude 3.5, Gemini 2.0, multimodální modely, AI agenti.

### Úrovně AI (konceptuální)
- **ANI (Artificial Narrow Intelligence / Slabá AI):** řeší specifickou úlohu lépe než člověk, ale nic jiného. Vše existující dnes. Příklady: AlphaGo, ChatGPT, autonomní vozidla.
- **AGI (Artificial General Intelligence / Silná AI):** obecná inteligence na úrovni člověka – schopná řešit libovolný kognitivní úkol. Neexistuje. Výzkumný cíl.
- **ASI (Artificial Superintelligence / Superinteligence):** překračuje lidskou inteligenci ve všech oblastech. Hypotetická, diskutabilní existence.

---

## b) Typy a používané modely

### Tradiční AI metody

**Expertní systémy:**
- Kódují znalosti odborníků do pravidel (IF-THEN).
- Komponenty: znalostní báze + inferenční engine.
- Příklady: MYCIN (diagnóza bakteriálních infekcí, 1976), XCON (konfigurace počítačů DEC).

**Prohledávání a optimalizace:**
- Prohledávání stavového prostoru: BFS, DFS, A* algoritmus (navigace).
- Evoluční algoritmy: genetické algoritmy – optimalizace inspirovaná biologickou evolucí.

---

### Strojové učení (Machine Learning, ML)

**ML** = algoritmy, které se učí z dat bez explicitního programování.

**Typy učení:**

**1. Supervised Learning (Učení s učitelem):**
- Trénovací data jsou označena (labeled) – vstup + správný výstup.
- Model se učí mapování vstup → výstup.
- **Klasifikace:** výstup je kategorie. Příklady: spam filtr, detekce nemocí, rozpoznávání obrazu.
- **Regrese:** výstup je číslo. Příklady: předpověď ceny nemovitosti, akciového kurzu.
- Algoritmy: Logistická regrese, SVM, Decision Trees, Random Forest, KNN.

**2. Unsupervised Learning (Učení bez učitele):**
- Data bez označení – model hledá struktury a vzory sám.
- **Clustering:** shlukování podobných dat (K-means, DBSCAN) – segmentace zákazníků.
- **Dimenzionality Reduction:** PCA, t-SNE – vizualizace vysokodimenzionálních dat.
- **Anomaly Detection:** odhalení odchylek od normy (detekce podvodů, výrobní defekty).

**3. Reinforcement Learning (Zpětnovazební učení):**
- Agent se učí interakcí s prostředím – dostává odměny/tresty.
- Cíl: maximalizovat kumulativní odměnu.
- Příklady: **AlphaGo, AlphaZero** (hry), autonomní roboti, obchodní algoritmy, řízení datových center (Google – snížení spotřeby energie o 40 %).

---

### Hluboké učení (Deep Learning, DL)

Podmnožina ML využívající **vícevrstvé neuronové sítě**.

**Umělá neuronová síť (ANN):**
- Inspirována biologickými neurony, vrstvená architektura.
- **Vstupní vrstva → Skryté vrstvy (hidden layers) → Výstupní vrstva.**
- Každé spojení má váhu, trénovány algoritmem **backpropagation** a optimalizátory (SGD, Adam).

**CNN (Convolutional Neural Network):**
- Specializované pro zpracování obrazu. Konvoluční vrstvy extrahují příznaky.
- Použití: rozpoznávání obrazu, detekce objektů (YOLO), medicínská diagnostika (RTG, MRI).
- Průlom: AlexNet (2012), ResNet, VGG, EfficientNet.

**RNN / LSTM / GRU:**
- Rekurentní sítě pro sekvenční data – pamatují si kontext.
- Použití: NLP, předpověď časových řad, překlad.
- Překonány transformery pro NLP.

**Transformer:**
- Revoluční architektura (2017, „Attention is All You Need").
- Mechanismus **self-attention** – každý token sleduje vztahy se všemi ostatními tokeny.
- Základ všech moderních LLM: BERT, GPT, T5, PaLM, Llama, Claude.
- Použití: text, obraz (ViT), audio, kód, video.

**LLM (Large Language Models):**
- Masivní transformery trénované na obrovských textových datech.
- **GPT-4 (OpenAI):** generativní, ~1 bilion parametrů (odhadováno).
- **Claude 3.5/4 (Anthropic):** bezpečnostně zaměřený, dlouhý context window.
- **Gemini 2.0 (Google):** multimodální, integrace do Google produktů.
- **Llama 3 (Meta):** open-source, lokálně spustitelný.
- **Mistral:** efektivní open-source evropský model.

**Difúzní modely (Diffusion Models):**
- Generování obrazu: postupné odšumování z náhodného šumu.
- Příklady: **Stable Diffusion (open-source), DALL-E 3, Midjourney, Adobe Firefly**.

**GAN (Generative Adversarial Network):**
- Dvě sítě: Generátor (vytváří falešná data) vs. Diskriminátor (rozlišuje pravé od falešných).
- Kompetice vede ke stále realističtějšímu generování.
- Použití: deepfake generování, syntetická data, super-resolution.

---

## c) Význam v ICT a společnosti, právní regulace, etika

### Dopad na ICT

**Automatizace:**
- AI nahrazuje rutinní kognitivní práce: zákaznická podpora (chatboti), datová analýza, účetnictví, překlad, základní programování.
- Průmysl 4.0: AI + robotika = autonomní výrobní linky, prediktivní údržba.

**Nové produkty a služby:**
- Personalizovaná doporučení (Netflix, Spotify, YouTube – algoritmy udržují pozornost).
- Autonomní vozidla (Tesla Autopilot, Waymo – level 2–4 autonomie).
- AI asistenti (Siri, Google Assistant, Alexa, Copilot).
- AI v medicíně: diagnostika z rentgenů (radiologie), predikce nemocí, AlphaFold (3D struktury proteinů → revoluce v biologii).

### Sociální dopady
- **Trh práce:** automatizace ohrožuje rutinní práce (řidiči, účetní, call centra), ale vytváří nové profily (AI inženýr, datový vědec, AI prompt engineer).
- **Digitální propast:** ti, kdo umí pracovat s AI, mají obrovskou výhodu.
- **Dezinformace:** AI generovaný obsah (deepfake, fake news) obtížně rozpoznatelný.

### Etika AI

**Klíčové problémy:**
- **Bias (zaujatost):** AI modely trénované na historických datech přebírají lidské předsudky. Příklad: biometrické systémy méně přesné pro tmavší pleti; úvěrové systémy diskriminující na základě PSČ.
- **Explainability / XAI (Vysvětlitelnost):** „black box" problém – nevíme, proč AI rozhodla tak jak rozhodla. Problém v kritických aplikacích (medicína, soud, úvěr).
- **Soukromí:** AI trénovaná na osobních datech bez souhlasu; facial recognition surveillance.
- **Autonomní zbraně:** letální AI systémy bez lidského dohledu.
- **Bezpečnost (AI Safety):** prevence neúmyslného škodlivého chování pokročilé AI.
- **Přisuzování autorství:** AI generovaný obsah – kdo je autorem? Copyright?

**Principy zodpovědné AI:**
- **Fairness (Spravedlnost):** bez diskriminace.
- **Accountability (Zodpovědnost):** jasná zodpovědnost za rozhodnutí AI.
- **Transparency (Průhlednost):** explainability.
- **Privacy (Soukromí):** GDPR a ochrana dat.
- **Safety (Bezpečnost):** předvídatelné a bezpečné chování.

### Právní regulace

**EU AI Act (Nařízení EU o umělé inteligenci, 2024):**
- První komplexní právní rámec pro AI na světě (platnost od 2025, plná aplikace 2026–2027).
- **Rizikový přístup (risk-based):**
  - **Nepřijatelné riziko (zakázáno):** sociální kreditní systémy, real-time biometrická identifikace na veřejnosti (s výjimkami), manipulace podprahovými technikami.
  - **Vysoké riziko:** AI v kritické infrastruktuře, vzdělávání, zaměstnání, medicíně, trestní justici → přísné požadavky (transparentnost, přesnost, lidský dohled).
  - **Omezené riziko:** chatboti → povinné zveřejnění, že jde o AI (anti-deepfake).
  - **Minimální riziko:** filtry spamu, AI ve hrách → bez zvláštní regulace.
- Sankce: až 35 milionů EUR nebo 7 % světového obratu.

**GDPR a AI:**
- AI zpracovávající osobní data musí splňovat GDPR.
- Automatizované rozhodování: právo na vysvětlení, právo na lidský přezkum (čl. 22).

**USA:** zatím bez federálního AI zákona – EO 14110 (Biden 2023), sektorové regulace.

---

## d) Možný vývoj a změny v ICT plynoucí ze zavádění AI

### Krátkodobý výhled (2025–2030)

**AI agenti:**
- AI nejen odpovídá na otázky, ale **autonomně provádí úkoly** (browsing, e-maily, kód, bookování).
- Multi-agent systémy: AI systémy spolupracující a delegující úkoly.
- Příklady: OpenAI Operator, Anthropic Claude Agents, AutoGPT.

**Vibe coding / AI-assisted development:**
- GitHub Copilot (Microsoft/OpenAI), Cursor, Devin (AI software engineer).
- AI generuje 40–80 % kódu → programátoři se stávají spíše architekty a revizory.

**Personalizovaná AI:**
- Lokální modely na zařízení (Apple Intelligence, Qualcomm NPU) – bez cloudu, soukromější.
- AI s dlouhodobou pamětí, personalizací.

### Střednědobý výhled (2030–2040)

**AGI?:**
- Někteří výzkumníci (Altman, Amodei) předpovídají AGI do 2030–2035. Kontroverze.
- Ekonomické modely se dramaticky změní při dosažení AGI.

**Kvantová AI:**
- Kombinace kvantových počítačů s ML → řešení optimalizačních problémů nepřístupných klasickým PC.
- Viz [[02_Datova_uloziste]] pro kvantové počítače.

**Biotech + AI:**
- Personalizovaná medicína: AI navrhuje léky a terapie dle genomu pacienta.
- AlphaFold3 (DeepMind) – predikce interakcí protein-DNA, protein-ligand → akcelerace léčby.

---

## e) Příklady využití AI v ICT a moderních technologiích

### Zdravotnictví
- **Diagnostika:** AI analýza RTG, CT, MRI snímků (detekce nádorů, diabetická retinopatie).
- **AlphaFold 2/3 (DeepMind):** predikce 3D struktur proteinů – revolucionizovalo biologii a vývoj léků.
- **Drug discovery:** AI zkracuje vývoj léků z 15 let na 2–4 roky.
- **Chirurgické roboty:** da Vinci (intuitivní chirurgie), AI-asistovaná přesnost.

### Autonomní vozidla
- **Senzory:** LiDAR, radar, kamery, ultrazvuk – fúze senzorů.
- **Computer Vision + DL:** detekce objektů (pedestrians, jiná vozidla, dopravní značky).
- **Úrovně autonomie SAE:** L0 (žádná) → L5 (plná, bez volantu). Dnes komerčně L2–L3 (Tesla, Waymo L4 v geofenced oblastech).

### Průmysl a logistika
- **Prediktivní údržba (Predictive Maintenance):** senzory na strojích + ML → předpověď selhání před jeho vznikem.
- **Robotika:** Boston Dynamics, ABB, FANUC – AI roboti schopní nestrukturovaných prostředí.
- **Optimalizace logistiky:** Amazon – AI řídí sklady, trasy zásilkových robotů.

### Kybernetická bezpečnost (viz [[17_Kyberneticke_utoky]])
- UEBA, anomaly detection, AI-powered SIEM, SOAR automatizace.
- Ale také: AI pro útočníky (deepfake, AI phishing).

### Finance
- **Algoritmické obchodování (Algo Trading):** HFT (High-Frequency Trading) – miliony transakcí za sekundu.
- **Detekce podvodů:** ML modely analyzují transakce v reálném čase (Mastercard, Visa).
- **Credit scoring:** AI hodnocení úvěruschopnosti (ale riziko biasu!).
- **Robo-advisors:** automatizované investiční poradenství (Betterment, Wealthfront).

### Vzdělávání
- **Personalizované učení:** adaptivní výukové systémy přizpůsobují obsah tempu a stylu studenta.
- **AI tutoring:** Khan Academy Khanmigo (GPT-4), duolingo – konverzační AI.
- **Automatické hodnocení:** esejí, kódu.

### Kreativní průmysl
- **Generativní AI:** Midjourney, DALL-E 3, Sora (video), Suno (hudba), Adobe Firefly.
- Kontroverze: autorská práva, práce umělců, autenticita.

### Věda a výzkum
- **Klimatické modely:** Google DeepMind – zlepšení předpovědí počasí (GraphCast).
- **Astronomie:** ML identifikace exoplanet, gravitačních vln.
- **Fyzika:** AI návrhy experimentů, jaderná fúze (DeepMind a tokamak).

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(2 min)** Co je AI – definice, Turingův test, ANI/AGI/ASI rozdíl
2. **(2 min)** Historie – Dartmouth 1956, AI wintery, AlexNet 2012, ChatGPT 2022
3. **(4 min)** Typy ML – supervised/unsupervised/reinforcement; DL – CNN, Transformer, LLM, difúzní modely
4. **(2 min)** Dopad na společnost a ICT – automatizace, trh práce, bias, explainability
5. **(2 min)** Právní regulace – EU AI Act (4 kategorie rizika, sankce), GDPR a AI
6. **(3 min)** Příklady využití – zdravotnictví (AlphaFold), autonomní vozidla, kybernetická bezpečnost, generativní AI
