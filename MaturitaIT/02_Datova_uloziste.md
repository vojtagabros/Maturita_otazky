# 2. Datová úložiště a budoucnost hardwaru

> Souvisí s: [[01_Architektura_PC]] | [[04_Virtualizace]] | [[08_Cloud_computing]] | [[20_Umela_inteligence]]

---

## a) Charakteristika HDD a SSD

### HDD (Hard Disk Drive) – magnetický pevný disk
- Funguje na principu **magnetického záznamu** na rotující kovové plotny (aluminium nebo sklo).
- Čtecí/zápisová hlava se pohybuje nad plottami – **mechanický pohyb = hlavní omezení**.
- Data jsou uspořádána do stop, sektorů a cylindrů.

**Parametry HDD:**
- Kapacita: 500 GB – 22 TB (spotřebitelské), až 30 TB (enterprise).
- Rychlost čtení/zápisu: 80–200 MB/s (sekvenční).
- Otáčky: 5 400 rpm (notebooky, NAS, úsporné), 7 200 rpm (desktop, výkon).
- Přístupová doba (seek time + latence): 5–15 ms – limitující faktor pro náhodný přístup.
- Rozhraní: **SATA III** (6 Gbit/s), **SAS** (servery – 12/24 Gbit/s, vyšší spolehlivost).

**Výhody:** nízká cena za GB (~20 €/TB), velké kapacity, ověřená technologie.
**Nevýhody:** citlivost na nárazy/vibrace, hlučnost, pomalý náhodný přístup, vysoká spotřeba (5–10 W).
**Použití:** NAS úložiště, zálohy a archivace, servery s velkým objemem dat, kde rychlost není kritická.

---

### SSD (Solid State Drive) – flash disk
- Žádné pohyblivé části – data uložena v **NAND flash paměti** (floating gate nebo charge trap tranzistory).
- Princip: elektrický náboj v buňce reprezentuje data.

**Typy NAND flash buněk:**

| Typ | Bity/buňka | Rychlost | Výdrž (P/E cykly) | Cena |
|---|---|---|---|---|
| SLC | 1 | Nejrychlejší | 100 000 | Nejvyšší |
| MLC | 2 | Rychlá | 10 000 | Střední |
| TLC | 3 | Dobrá | 3 000 | Nízká |
| QLC | 4 | Pomalejší | 1 000 | Nejnižší |

**3D NAND** – buňky vrstveny vertikálně (64–232 vrstev) → více kapacity, lepší výdrž.

**Parametry SSD:**
- Kapacita: 128 GB – 8 TB.
- Rozhraní + rychlost:
  - **SATA SSD** (M.2 nebo 2,5"): čtení ~550 MB/s, zápis ~520 MB/s.
  - **NVMe SSD** (PCIe 4.0): čtení až 7 000 MB/s, zápis až 6 500 MB/s.
  - **NVMe PCIe 5.0**: čtení až 14 000 MB/s.
- Latence: 0,05–0,1 ms (100–300× nižší než HDD).
- Životnost měřena v **TBW** (Terabytes Written) a **MTBF** (Mean Time Between Failures).

**Výhody:** extrémní rychlost, odolnost vůči nárazům, tichý provoz, nízká spotřeba (2–4 W).
**Nevýhody:** vyšší cena za GB (~60–100 €/TB), omezený počet zápisů, data mohou být ztracena po dlouhé nečinnosti bez napájení.
**Použití:** systémové disky (OS + aplikace), pracovní stanice, notebooky, herní PC.

### Porovnání HDD vs. SSD

| Parametr | HDD | SATA SSD | NVMe SSD |
|---|---|---|---|
| Sekvenční čtení | ~150 MB/s | ~550 MB/s | ~7 000 MB/s |
| Latence | 5–15 ms | 0,1 ms | 0,05 ms |
| Odolnost na nárazy | Nízká | Vysoká | Vysoká |
| Cena/TB | ~20 € | ~60 € | ~80–100 € |
| Spotřeba | 5–10 W | 2–4 W | 3–8 W |

---

## b) Flash paměti a cloudová úložiště

### Flash paměti (mimo SSD)
- Nevolatilní paměť – data zůstávají i bez napájení.
- **USB flash disky:** přenosná úložiště, kapacita 4 GB – 2 TB, rozhraní USB 2.0/3.0/3.2/USB-C.
- **Paměťové karty:** SD (Secure Digital), microSD, CompactFlash – pro fotoaparáty, drony, kamery, SBC (Raspberry Pi).
  - Rychlostní třídy: Class 4/10, UHS-I/II, Video Speed Class (V30, V60, V90).
- **eMMC (embedded MMC):** integrovaná flash paměť na desce – levnější notebooky, tablety, SBC. Pomalejší než NVMe.
- **UFS (Universal Flash Storage):** nástupce eMMC v mobilních zařízeních, rychlejší (UFS 3.1, UFS 4.0).

### Cloudová úložiště
Data uložena na **vzdálených serverech** přístupná přes internet. Funguje na principu virtualizace a distribuovaného úložiště – viz [[04_Virtualizace]] a [[08_Cloud_computing]].

**Modely cloudového úložiště:**
- **Veřejný cloud:** Google Drive, OneDrive, Dropbox, iCloud, Amazon S3.
- **Soukromý cloud:** vlastní infrastruktura firmy (Nextcloud, ownCloud, Ceph).
- **Hybridní cloud:** kombinace veřejného a soukromého cloudu.

**Výhody:** přístup odkudkoliv, automatické zálohy, škálovatelnost, snadné sdílení, redundance.
**Nevýhody:** závislost na internetu, bezpečnostní rizika (úniky dat), GDPR compliance při ukládání osobních dat mimo EU, průběžné náklady.

**Tier storage (studené/horké úložiště):**
- **Hot storage:** rychlý přístup, drahé (SSD, NVMe) – pro aktivně používaná data.
- **Cold storage:** pomalý přístup, levné (pásky, archivní HDD, AWS Glacier) – pro zálohy.

---

## c) Aktuální trendy v oblasti hardwaru

### ARM procesory
- Architektura RISC (viz [[01_Architektura_PC]]) – nízká spotřeba, vysoký výkon na watt.
- **Apple M-series (M1, M2, M3, M4):** ARM čipy pro Mac/iPad – SoC (System on Chip) integrující CPU, GPU, NPU, paměť. Revoluční poměr výkon/spotřeba.
- **Qualcomm Snapdragon X Elite/Plus:** ARM Windows notebooky (Copilot+ PC).
- **Servery:** AWS Graviton (Amazon), Ampere Altra – ARM v datových centrech.
- **Superpočítače:** Fugaku (#1, Japonsko) – 48 jader ARM A64FX.

### Akcelerátory
- **GPU (Graphics Processing Unit):** NVIDIA (RTX, H100, B200), AMD (Radeon RX, MI300). Masivní paralelismus – tisíce jader. Ideální pro AI/ML trénování.
- **TPU (Tensor Processing Unit):** Google – optimalizace pro tensorové operace v neuronových sítích. Používá Google Cloud.
- **NPU (Neural Processing Unit):** integrované v moderních CPU – Apple Neural Engine, Intel AI Boost, Qualcomm Hexagon. Lokální AI inference (edge AI).
- **FPGA (Field Programmable Gate Array):** rekonfigurovatelné obvody – HPC, edge computing, Xilinx (AMD), Intel Altera.

### Energetická efektivita
- Datová centra spotřebují ~2–3 % světové elektřiny – tlak na snižování TDP.
- **Heterogenní architektury:** P-cores (výkonná) + E-cores (úsporná) – Intel hybrid (Raptor Lake), Apple M-series (Performance + Efficiency cores).
- Výrobní procesy: **TSMC 3 nm, 2 nm** – menší tranzistory = nižší spotřeba + vyšší výkon.
- **Liquid cooling, immersion cooling** – chlazení serverů v kapalině.

---

## d) Budoucnost počítačů – Moorův zákon, kvantové počítače

### Moorův zákon
- Formulován **Gordonem Mooreem** (spoluzakladatel Intel) v roce **1965**.
- Empirické pozorování: **počet tranzistorů na čipu se zdvojnásobuje přibližně každé 2 roky** při zachování ceny.
- Historicky platil přesně: Intel 4004 (1971) – 2 300 tranzistorů → Apple M2 Ultra (2023) – 134 miliard tranzistorů.

**Zánik Moorova zákona?**
- Fyzikální limity: tranzistory na úrovni atomů (2 nm ≈ 10 atomů křemíku), **kvantové tunelování** způsobuje chyby.
- Ekonomické limity: extrémní náklady na výrobu (továrna TSMC = 20+ miliard USD).
- Alternativy k Moorovu zákonu: 3D čipování (chiplets – AMD), nové materiály (grafen, GaN), specializované čipy (ASIC), kvantové počítače.

### Kvantové počítače
Využívají principy kvantové mechaniky místo klasické logiky.

**Základní pojmy:**
- **Qubit** – kvantový bit. Na rozdíl od klasického bitu (0 nebo 1) může být v **superpozici** (0 a 1 současně).
- **Superpozice:** qubit existuje v obou stavech do okamžiku měření (kolaps vlnové funkce).
- **Provázanost (Quantum Entanglement):** propojení qubitů – stav jednoho okamžitě determinuje stav druhého, bez ohledu na vzdálenost.
- **Interference:** zesiluje pravděpodobnost správných výsledků, tlumí nesprávné.

**Kvantová převaha (Quantum Supremacy):**
- Google (2019): 53-qubitový procesor Sycamore zvládl specifický výpočet za 200 sekund, klasický superpočítač by potřeboval tisíce let.
- IBM (2023): 1 000+ qubitový čip Condor/Heron.

**Aplikace:**
- **Kryptografie:** Shorův algoritmus – teoreticky prolomí RSA šifrování (motivace pro post-quantum kryptografii).
- **Optimalizace:** logistika, portfolio management, léková logistika.
- **Simulace molekul:** farmaceutika, vývoj materiálů, chemie.
- **Strojové učení:** kvantové ML algoritmy.

**Výzvy:**
- **Dekoherence:** qubity jsou extrémně citlivé na rušení z okolí.
- Chlazení na ~15 millikelvinů (téměř absolutní nula).
- Chybovost – nutné kvantové error correction (vyžaduje 1 000 fyzických qubitů na 1 logický qubit).
- Škálovatelnost – propojení tisíců qubitů.

**Hráči:** IBM Quantum, Google Quantum AI, Microsoft (topologické qubity), IonQ, Quantinuum.

### Další perspektivní technologie
- **Neuromorphic computing:** čipy napodobující strukturu lidského mozku (Intel Loihi 2). Extrémně energeticky efektivní pro AI inference.
- **In-memory computing:** výpočty přímo v paměti, eliminace Von Neumannova bottlenecku (viz [[01_Architektura_PC]]).
- **Fotonika:** přenos dat světlem místo elektronů → rychlost světla, nižší spotřeba.

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(3 min)** HDD – princip magnetického záznamu, parametry, výhody/nevýhody, použití
2. **(3 min)** SSD – princip flash paměti, typy NAND (SLC–QLC), NVMe vs. SATA, porovnání s HDD
3. **(2 min)** Flash paměti – USB, SD karty, eMMC; cloudová úložiště, hot/cold storage, GDPR
4. **(3 min)** Trendy – ARM procesory, GPU/NPU/TPU akcelerátory, energetická efektivita
5. **(2 min)** Moorův zákon – definice, historická platnost, fyzikální a ekonomické limity
6. **(2 min)** Kvantové počítače – qubit, superpozice, provázanost, aplikace, výzvy
