# 18. Algoritmus a algoritmizace úloh

> Souvisí s: [[19_Programovani]] | [[20_Umela_inteligence]]

---

## a) Charakteristika algoritmů

### Co je algoritmus?
**Algoritmus** je konečná, jednoznačná posloupnost instrukcí (kroků), která řeší daný problém nebo úlohu a vede k výsledku v konečném čase.

Původ slova: ze jména perského matematika **Al-Chórezmí** (9. stol.), latinizovaný jako Algoritmi.

### Příklady algoritmů v každodenním životě
- Recept na vaření: ingredience (vstup) → kroky → hotové jídlo (výstup).
- Navigace GPS: startovní bod + cíl → výpočet trasy.
- Vyhledávání v Googlu: dotaz → rankingový algoritmus → výsledky.
- Třídění oblečení: proces roztřídění položek do kategorií.

---

## b) Vlastnosti algoritmů

Pro to, aby byl algoritmus správný a použitelný, musí splňovat **5 základních vlastností**:

### 1. Konečnost (Finiteness)
- Algoritmus musí skončit po **konečném počtu kroků**.
- Nekonečná smyčka = algoritmus nesplňuje konečnost.
- Příklad chyby: `while True: pass` bez podmínky ukončení.

### 2. Určitost / Jednoznačnost (Definiteness)
- Každý krok musí být **přesně a jednoznačně definován** – nesmí připouštět různé interpretace.
- Každý krok má jediný možný výklad.
- Špatný příklad: „Přidej trochu soli" – neurčité.
- Správný příklad: „Přidej 5 gramů NaCl."

### 3. Vstup (Input)
- Algoritmus má **nula nebo více vstupů** – data, se kterými pracuje.
- Vstupy jsou z dobře definované množiny hodnot.
- Nula vstupů: algoritmus generuje výstup z konstantních dat.

### 4. Výstup (Output)
- Algoritmus produkuje **jeden nebo více výstupů** – výsledky výpočtu.
- Výstup musí mít vztah ke vstupním datům.

### 5. Efektivnost / Proveditelnost (Effectiveness)
- Každý krok algoritmu musí být **proveditelný** – realizovatelný v konečném čase.
- Kroky musí být dostatečně jednoduché, aby je bylo možné přesně vykonat.
- Příklad neproveditelného kroku: „Vypiš všechna prvočísla" (nekonečná množina).

### Další žádoucí vlastnosti
- **Správnost (Correctness):** algoritmus produkuje správné výsledky pro všechny platné vstupy.
- **Efektivita (Efficiency):** minimalizace potřebného času a paměti.
- **Obecnost (Generality):** řeší třídu problémů, ne jen jeden konkrétní případ.
- **Čitelnost (Readability):** srozumitelnost pro člověka (dokumentace kódu).
- **Robustnost:** správné chování i pro neočekávané nebo chybné vstupy.

### Složitost algoritmů (výkonnostní analýza)
**Big O notace** – popisuje, jak roste čas/paměť v závislosti na velikosti vstupu n:
- **O(1)** – konstantní čas: přístup k prvku pole.
- **O(log n)** – logaritmická: binární vyhledávání.
- **O(n)** – lineární: procházení pole.
- **O(n log n)** – „n log n": efektivní třídění (Merge Sort, Quick Sort).
- **O(n²)** – kvadratická: Bubble Sort, vnořené smyčky.
- **O(2ⁿ)** – exponenciální: brute-force prohledávání, NP-úplné problémy.

---

## c) Vývojové diagramy – komponenty a jejich značení

**Vývojový diagram (flowchart)** je grafická reprezentace algoritmu pomocí standardizovaných symbolů spojených šipkami (toková logika).

Standard: **ISO 5807:1985** (nebo norma ČSN).

### Základní symboly

| Symbol | Tvar | Název | Použití |
|---|---|---|---|
| ○ / Zaoblený obdélník | Ovál/Zaoblený | **Terminál (Start/Stop)** | Začátek a konec algoritmu |
| □ | Obdélník | **Proces (instrukce)** | Výpočet, přiřazení, operace |
| ◇ | Kosočtverec | **Rozhodnutí (podmínka)** | Větvení: Ano/Ne, True/False |
| ▱ | Rovnoběžník | **Vstup/Výstup** | Čtení vstupu, výpis výstupu |
| □ (s dvojitou čarou) | Obdélník s čarami | **Podprogram/Funkce** | Volání podprogramu |
| ⬠ | Šestiúhelník | **Příprava/Cyklus** | Inicializace cyklu (FOR) |
| → | Šipka | **Tok řízení** | Spojení symbolů, směr průchodu |

### Základní řídící struktury (ve vývojovém diagramu)

**Sekvence (Sequence):**
```
[START] → [Instrukce A] → [Instrukce B] → [Instrukce C] → [STOP]
```
Kroky se provádějí postupně za sebou.

**Větvení (Selection – IF-THEN-ELSE):**
```
           ↓
      ◇ Podmínka? ◇
     /              \
  ANO               NE
   ↓                 ↓
[Blok A]         [Blok B]
     \              /
          ↓
     (pokračování)
```

**Cyklus WHILE (podmínka na začátku):**
```
         ↓
   ◇ Podmínka? ◇ → NE → (výstup z cyklu)
         ↓ ANO
   [Tělo cyklu]
         ↑ (zpět na podmínku)
```

**Cyklus DO-WHILE (podmínka na konci):**
```
   [Tělo cyklu]
         ↓
   ◇ Podmínka? ◇ → ANO → (zpět na tělo)
         ↓ NE
   (výstup z cyklu)
```

**Cyklus FOR (počítaný):**
```
[i = 0] → ◇ i < n? ◇ → NE → (výstup)
               ↓ ANO
         [Tělo cyklu]
               ↓
         [i = i + 1]
               ↑ (zpět na podmínku)
```

---

## d) Jednoduchý příklad vývojového diagramu

### Příklad: Algoritmus pro určení, zda je číslo sudé nebo liché

**Popis:** Uživatel zadá celé číslo. Program zjistí, zda je sudé (dělitelné 2 bez zbytku) nebo liché.

**Pseudokód:**
```
START
  VSTUP: číslo n
  POKUD (n MOD 2 == 0) PAK
    VÝSTUP: "Číslo je sudé"
  JINAK
    VÝSTUP: "Číslo je liché"
  KONEC POKUD
STOP
```

**Vývojový diagram:**
```
        ┌──────────┐
        │  START   │
        └────┬─────┘
             ↓
     ┌───────────────────┐
     │ VSTUP: zadej číslo│
     └────────┬──────────┘
              ↓
     ◇ n mod 2 == 0? ◇
    /                   \
  ANO                   NE
   ↓                     ↓
┌──────────────┐   ┌────────────────┐
│ Výpis: "Sudé"│   │ Výpis: "Liché" │
└──────┬───────┘   └──────┬─────────┘
        \                 /
              ↓
        ┌──────────┐
        │  STOP    │
        └──────────┘
```

---

### Příklad: Algoritmus pro výpočet faktoriálu

**Popis:** Vypočítej n! (faktoriál čísla n). Příklad: 5! = 5×4×3×2×1 = 120.

**Pseudokód:**
```
START
  VSTUP: n
  POKUD n < 0 PAK
    VÝSTUP: "Chyba: záporné číslo"
    STOP
  KONEC POKUD
  výsledek = 1
  i = 1
  OPAKUJ DOKUD i <= n:
    výsledek = výsledek * i
    i = i + 1
  VÝSTUP: výsledek
STOP
```

**Vývojový diagram:**
```
     ┌──────────┐
     │  START   │
     └────┬─────┘
          ↓
   ┌──────────────┐
   │ VSTUP: n     │
   └──────┬───────┘
          ↓
   ◇ n < 0? ◇ → ANO → [Chyba] → STOP
          ↓ NE
   ┌──────────────────┐
   │ výsledek = 1     │
   │ i = 1            │
   └──────┬───────────┘
          ↓
   ◇ i <= n? ◇ → NE → [Výpis: výsledek] → STOP
          ↓ ANO
   ┌──────────────────────┐
   │ výsledek = výsledek*i│
   │ i = i + 1            │
   └──────────┬───────────┘
              ↑ (zpět na podmínku)
```

### Příklady algoritmů a jejich typy

**Vyhledávací algoritmy:**
- **Lineární vyhledávání (Linear Search):** O(n) – prochází postupně každý prvek.
- **Binární vyhledávání (Binary Search):** O(log n) – funguje na seřazených datech, dělí pole na půl.

**Třídicí algoritmy:**
- **Bubble Sort:** O(n²) – porovnává sousední prvky a prohodí je. Jednoduchý, pomalý.
- **Selection Sort:** O(n²) – hledá minimum a umísťuje na správnou pozici.
- **Merge Sort:** O(n log n) – divide and conquer, stabilní.
- **Quick Sort:** O(n log n) průměr – pivot-based, velmi rychlý v praxi.

**Grafové algoritmy:**
- **Dijkstra:** nejkratší cesta v grafu s nezáporným ohodnocením hran (navigace).
- **BFS/DFS (prohledávání do šířky/hloubky):** procházení grafu/stromu.

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(2 min)** Co je algoritmus – definice, etymologie, příklady z každodenního života
2. **(4 min)** Vlastnosti – konečnost, určitost, vstup, výstup, efektivnost; vysvětlit každou s příkladem
3. **(3 min)** Big O složitost – O(1), O(log n), O(n), O(n²); příklady algoritmů ke každé
4. **(3 min)** Vývojové diagramy – symboly (terminál, proces, rozhodnutí, I/O); 3 řídící struktury (sekvence, větvení, cyklus)
5. **(3 min)** Příklad – nakreslit/popsat vývojový diagram pro sudé/liché číslo nebo faktoriál
