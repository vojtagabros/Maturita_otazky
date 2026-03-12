# 1. Architektura PC a základní principy fungování počítače

> Souvisí s: [[02_Datova_uloziste]] | [[03_Operacni_systemy]] | [[04_Virtualizace]]

---

## a) Historie vývoje počítačů

Počítače prošly od svých počátků obrovským vývojem rozdělovaným do **generací**:

- **0. generace – mechanické stroje** (17.–19. stol.): Pascal (Pascaline, 1642), Babbage (Analytical Engine) – první myšlenka programovatelného stroje. Hollerith – děrné štítky pro sčítání lidu (1890).
- **1. generace – elektronky (1940–1955)**: ENIAC (1945, USA), UNIVAC. Obrovské stroje (stovky m²), nespolehlivé, programování v strojovém kódu, vstup přes děrné štítky.
- **2. generace – tranzistory (1955–1965)**: Menší, rychlejší, spolehlivější. Vznik assembleru a prvních vyšších jazyků (FORTRAN, COBOL).
- **3. generace – integrované obvody (1965–1975)**: IBM System/360, minipočítače, time-sharing, operační systémy.
- **4. generace – mikroprocesory (1975–dnes)**: Intel 4004 (1971, první komerční mikroprocesor), Apple II (1977), IBM PC (1981), osobní počítač pro každého.
- **5. generace – AI a paralelismus**: Neuronové sítě, GPU computing, kvantové počítače (viz [[02_Datova_uloziste]]).

---

## b) Von Neumannova vs. Harvardská architektura, CISC vs. RISC

### Von Neumannova architektura (1945)
Navržena Johnem von Neumannem. Klíčové vlastnosti:
- Data i program jsou uloženy ve **stejné operační paměti**.
- Sekvenční načítání a vykonávání instrukcí (fetch–decode–execute cyklus).
- Základní komponenty: **CPU, paměť (RAM), vstup/výstup, sběrnice**.
- **Von Neumannův bottleneck**: CPU čeká na data z paměti – sběrnice je úzkým hrdlem.
- Použití: naprostá většina dnešních PC a serverů.

### Harvardská architektura
- **Oddělená paměť** pro instrukce a pro data (fyzicky i logicky).
- Paralelní přístup k oběma → vyšší propustnost.
- Použití: mikrokontroléry (Arduino, PIC, AVR), DSP procesory, signálové procesory.
- Moderní CPU kombinují obě: L1 cache je oddělená (instrukce/data) = **modifikovaná Harvardská architektura**.

### CISC vs. RISC

| Vlastnost | CISC | RISC |
|---|---|---|
| Počet instrukcí | Velký (stovky) | Malý (desítky) |
| Délka instrukce | Variabilní | Fixní (32 bit) |
| Příklady | Intel x86, x86-64 | ARM, RISC-V, MIPS |
| Filosofie | Komplexní instrukce, méně kódu | Jednoduché instrukce, rychlejší pipeline |
| Použití | Desktop, server | Mobily, embedded, ARM servery |

ARM (RISC) se dnes prosazuje i do desktopů a serverů díky energetické efektivitě – Apple M-series, AWS Graviton.

---

## c) Jednotky Bit a Byte, základní kódování

### Jednotky
- **Bit (b)** – nejmenší jednotka informace, hodnota 0 nebo 1.
- **Byte (B)** = 8 bitů – základní adresovatelná jednotka paměti.
- **Předpony (binární):** KB = 1 024 B, MB = 1 024 KB, GB = 1 024 MB, TB = 1 024 GB.
- Telekomunikace a výrobci disků používají dekadické předpony (1 GB = 1 000 000 000 B) → zdánlivě větší kapacity.

### Kódování znaků

**ASCII (American Standard Code for Information Interchange):**
- 7bitové kódování → 128 znaků (0–127).
- Obsahuje anglická písmena, číslice, speciální znaky, řídicí znaky (Enter, Tab...).
- Rozšířená ASCII = 8 bitů (256 znaků) – různé národní varianty (ISO 8859-1, Windows-1250).
- **Problém:** nepokrývá všechny světové jazyky, různé standardy jsou nekompatibilní.

**UTF-8 (Unicode Transformation Format – 8-bit):**
- Variabilní délka: 1 až 4 bajty na znak.
- Zpětně kompatibilní s ASCII (prvních 128 znaků identické).
- Pokrývá celý Unicode standard – 149 000+ znaků, všechny jazyky světa, emoji, symboly.
- Dnes **dominantní standard** na internetu (>98 % webových stránek).
- Alternativy: UTF-16 (Java, Windows interně), UTF-32 (fixní 4B/znak, plýtvavé).

---

## d) Hlavní komponenty PC, periferie

### Procesor (CPU – Central Processing Unit)
- Mozek počítače – načítá, dekóduje a vykonává instrukce.
- Parametry: počet jader/vláken, taktovací frekvence (GHz), cache (L1/L2/L3), TDP (W), výrobní proces (nm).
- Výrobci: **Intel** (Core i3/i5/i7/i9/Ultra), **AMD** (Ryzen 5/7/9), **Apple** (M-series – ARM).

### Paměť RAM (Random Access Memory)
- Operační paměť – dočasné úložiště pro běžící OS a programy.
- **Volatilní** – po vypnutí data zmizí.
- Typy: DDR4 (3200–5200 MHz), DDR5 (4800–8400 MHz). Parametry: kapacita, frekvence, latence (CL).
- Virtuální paměť (swap/page file) – OS rozšiřuje RAM na disk, pomalejší.

### Základní deska (Motherboard)
- Propojuje všechny komponenty, obsahuje chipset, BIOS/UEFI.
- Sloty: PCIe (GPU, NVMe SSD), RAM sloty (DIMM), konektory SATA, M.2, USB.
- **BIOS/UEFI** – firmware inicializující hardware při startu (POST), bootování OS.

### Grafická karta (GPU)
- Renderování obrazu, dnes AI/ML výpočty (CUDA, OpenCL), vědecké simulace.
- **Integrovaná GPU** – součást CPU (Intel UHD, AMD Radeon iGPU, Apple M-series).
- **Dedikovaná GPU** – samostatná karta (NVIDIA GeForce/RTX, AMD Radeon RX).

### Úložiště
Viz [[02_Datova_uloziste]] – HDD, SSD, flash paměti.

### Napájecí zdroj (PSU)
- Převádí střídavý proud (230V AC) na stejnosměrný (3,3/5/12V DC).
- Parametry: výkon (W), účinnost (80 PLUS certifikace: Bronze/Gold/Platinum/Titanium).

### Vstupní periferie
- Klávesnice, myš, skener, mikrofon, webkamera, touchpad, grafický tablet, joystick, gamepad.

### Výstupní periferie
- Monitor (LCD/OLED/AMOLED, rozlišení, obnovovací frekvence), tiskárna, reproduktory, projektor.

### Vstupně-výstupní periferie
- Dotykové obrazovky, multifunkční tiskárny, externí disky, VR headsety (viz [[13_Virtualni_realita]]).

---

## e) Právní aspekty užívání software, typy ochrany

### Typy softwarových licencí
- **Proprietární (komerční):** uživatel kupuje licenci k užívání, ne vlastnictví kódu. Příklady: Microsoft Office, Adobe Creative Suite, Windows.
- **Freeware:** zdarma k užívání, uzavřený zdrojový kód, bez možnosti úprav. Příklady: VLC, 7-Zip, Adobe Acrobat Reader.
- **Shareware:** zkušební verze zdarma, po uplynutí doby vyžaduje platbu.
- **Open Source – licence:**
  - **GPL (GNU General Public License):** odvozené dílo musí být také GPL (copyleft). Příklady: Linux, GCC, WordPress.
  - **LGPL:** méně striktní, knihovny lze použít v proprietárním SW.
  - **MIT licence:** velmi permisivní, použití i v komerčních produktech. Příklady: jQuery, React.
  - **Apache 2.0:** podobná MIT, explicitně řeší patenty.
  - **BSD:** permisivní, různé varianty.
- **Creative Commons (CC):** pro kreativní díla – CC BY, CC BY-SA, CC BY-NC, CC0 (public domain).

### Právní ochrana software v ČR
- **Zákon č. 121/2000 Sb. (Autorský zákon):** software je chráněn jako autorské dílo od vzniku, bez registrace.
- Ochrana trvá **70 let po smrti autora** (nebo 70 let od zveřejnění u firemních děl).
- Zakázáno: nelegální kopírování (piraterie), neoprávněný reverse engineering.
- **GDPR (Nařízení EU 2016/679):** ochrana osobních údajů – software pracující s osobními daty musí být GDPR-compliant.
- **Zákon č. 181/2014 Sb. (o kybernetické bezpečnosti)** – viz [[15_Kyberneticka_kriminalita]].

### Důsledky porušení
- Civilní odpovědnost: náhrada škody, soudní zákaz šíření.
- Trestní odpovědnost: trestný čin porušení autorských práv (§ 270 TZ), až 2–8 let odnětí svobody.
- **BSA (Business Software Alliance)** – organizace monitorující softwarovou piraterii.

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(2 min)** Úvod – co je architektura počítače, proč je důležitá
2. **(3 min)** Historie – generace počítačů, klíčové milníky (ENIAC → IBM PC → AI era)
3. **(3 min)** Von Neumann vs. Harvard, CISC vs. RISC – srovnání s příklady
4. **(2 min)** Jednotky a kódování – bit/byte, ASCII vs. UTF-8
5. **(3 min)** Komponenty PC – CPU, RAM, GPU, deska, periferie
6. **(2 min)** Právní aspekty – licence (GPL, MIT, proprietární), autorský zákon
