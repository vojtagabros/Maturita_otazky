# 19. Základní pojmy programování a jeho definice

> Souvisí s: [[18_Algoritmy]] | [[20_Umela_inteligence]] | [[10_Firemni_IS]]

---

## a) Základní pojmy: proměnná, metoda, cyklus, knihovna, API

### Proměnná (Variable)
- Pojmenované místo v paměti pro uložení hodnoty, která se může měnit.
- **Název (identifikátor):** libovolný název dle konvencí jazyka (CamelCase, snake_case).
- **Datový typ:** určuje, jaký druh dat proměnná uchovává a kolik paměti zabírá.
  - `int` – celé číslo (32/64 bit)
  - `float / double` – desetinné číslo (IEEE 754)
  - `bool` – pravda/nepravda (True/False)
  - `str / String` – textový řetězec
  - `char` – jeden znak
  - `list / array` – kolekce prvků
- **Statické typování:** typ určen při kompilaci (Java, C++, Rust).
- **Dynamické typování:** typ určen za běhu (Python, JavaScript, Ruby).
- **Rozsah (Scope):** kde je proměnná viditelná – lokální (v funkci), globální (v celém programu).

### Konstanta (Constant)
- Pojmenovaná hodnota, která se **nemění** za běhu programu.
- Konvence: VELKÁ_PÍSMENA (`MAX_SIZE = 100`, `PI = 3.14159`).

### Metoda / Funkce (Method / Function)
- **Funkce:** pojmenovaný blok kódu, který vykonává specifický úkol. Lze volat opakovaně.
- **Metoda:** funkce definovaná uvnitř třídy (OOP) – přistupuje k datům objektu.
- **Parametry:** vstupní hodnoty předávané funkci při volání (formální parametry vs. argumenty).
- **Návratová hodnota:** výsledek, který funkce vrátí (`return` příkaz).
- **Rekurze:** funkce volající samu sebe (faktoriál, Fibonacci, průchod stromem).

```python
def factorial(n):       # definice funkce
    if n <= 1:
        return 1
    return n * factorial(n - 1)  # rekurzivní volání

result = factorial(5)   # volání funkce, result = 120
```

### Cyklus (Loop)
Opakování bloku kódu. Typy:
- **For cyklus:** iterace přes sekvenci nebo určitý počet opakování.
  ```python
  for i in range(10):
      print(i)
  ```
- **While cyklus:** opakuje dokud platí podmínka.
  ```python
  while x > 0:
      x -= 1
  ```
- **Do-while / repeat-until:** tělo se provede alespoň jednou (Python nemá nativně).
- **Řídící příkazy:** `break` (ukončí cyklus), `continue` (přeskočí aktuální iteraci).

### Knihovna (Library)
- Kolekce předpřipravených funkcí, tříd a modulů pro opakované použití.
- Ušetří čas – nemusím implementovat základní funkce od nuly.
- **Standardní knihovna:** součást jazyka (Python: `os`, `math`, `json`, `datetime`).
- **Třetí strana (Third-party):** instalovatelné z repozitářů (Python: pip/PyPI, Node.js: npm, Java: Maven/Gradle).
- Příklady: `NumPy, Pandas` (data science), `React` (frontend), `Django, Flask` (web backend), `TensorFlow, PyTorch` (AI/ML).

### API (Application Programming Interface)
- **Rozhraní** definující, jak spolu mohou komunikovat různé softwarové komponenty.
- Abstrakce – volám API bez znalosti vnitřní implementace.
- **Typy API:**
  - **REST API (Representational State Transfer):** HTTP protokol, JSON/XML formát. Nejrozšířenější pro webové služby. Metody: GET, POST, PUT, PATCH, DELETE.
  - **SOAP:** starší, XML-based, komplexnější, silná typizace.
  - **GraphQL:** flexibilní dotazovací jazyk pro API (Meta/Facebook). Klient si specifikuje, co chce.
  - **gRPC:** Google, binární protokol (Protocol Buffers), rychlý, pro mikroservisy.
  - **Webové hooky (Webhooks):** push notifikace – server volá klienta při události.
- **API Key / OAuth:** autentizace pro přístup k API.

```python
import requests
response = requests.get("https://api.github.com/users/torvalds")
data = response.json()
print(data["name"])  # Linus Torvalds
```

---

## b) Objektově orientované vs. procedurální programování

### Procedurální (imperativní) programování
- Program = sled příkazů vykonávaných sekvenčně.
- Data a funkce jsou **odděleny**.
- Kód se organizuje do funkcí/procedur.
- Stav programu je udržován v proměnných.
- **Výhody:** jednoduchost, srozumitelnost pro malé programy, rychlost pro procedurální úlohy.
- **Nevýhody:** při velkých projektech se obtížně spravuje (spaghetti code), slabá znovupoužitelnost.
- Příklady jazyků: **C, Pascal, Fortran, BASIC, Shell scripting**.

```c
// Procedurální přístup v C
int plocha_obdelniku(int sirka, int vyska) {
    return sirka * vyska;
}

int main() {
    int s = 5, v = 3;
    printf("Plocha: %d\n", plocha_obdelniku(s, v));
    return 0;
}
```

### Objektově orientované programování (OOP)
- Program je modelován jako sada **objektů** interagujících navzájem.
- Objekt = data (atributy/vlastnosti) + chování (metody).
- **Třída (Class):** šablona/plán pro vytváření objektů.
- **Objekt (Instance):** konkrétní výskyt třídy.

**4 základní pilíře OOP:**

1. **Zapouzdření (Encapsulation):**
   - Skrytí vnitřní implementace – přístup k datům pouze přes definované rozhraní (gettery/settery).
   - Modifikátory přístupu: `public`, `private`, `protected`.

2. **Dědičnost (Inheritance):**
   - Třída (potomek/subclass) přebírá vlastnosti a metody jiné třídy (rodič/superclass).
   - Umožňuje znovupoužití kódu a hierarchii tříd.
   - `class Pes(Zvíře)` – Pes dědí od Zvíře.

3. **Polymorfismus (Polymorphism):**
   - Objekty různých tříd mohou reagovat na stejné volání metody různě.
   - **Přetížení metod (Overloading):** stejné jméno metody, jiné parametry.
   - **Přepis metod (Overriding):** potomek přepíše metodu rodiče.

4. **Abstrakce (Abstraction):**
   - Skrytí komplexity – pracuji s rozhraním, ne implementací.
   - Abstraktní třídy a rozhraní (interface).

```python
# OOP přístup v Pythonu
class Tvar:
    def plocha(self):
        raise NotImplementedError  # abstraktní metoda

class Obdelnik(Tvar):
    def __init__(self, sirka, vyska):
        self.sirka = sirka
        self.vyska = vyska

    def plocha(self):  # přepis (Override)
        return self.sirka * self.vyska

class Kruh(Tvar):
    def __init__(self, polomer):
        self.polomer = polomer

    def plocha(self):
        return 3.14159 * self.polomer ** 2

# Polymorfismus
tvary = [Obdelnik(5, 3), Kruh(4)]
for t in tvary:
    print(t.plocha())  # každý typ volá svou verzi plocha()
```

### Srovnání OOP vs. Procedurální

| Vlastnost | Procedurální | OOP |
|---|---|---|
| Organizace | Funkce/procedury | Třídy a objekty |
| Data | Oddělena od funkcí | Zapouzdřena v objektech |
| Znovupoužitelnost | Omezená | Dědičností, modulárnost |
| Složitost | Vhodné pro malé projekty | Vhodné pro velké systémy |
| Paradigma | Imperativní | Imperativní + deklarativní |
| Příklady jazyků | C, Pascal | Java, C++, Python, C# |

**Společné znaky:**
- Obě používají proměnné, podmínky, cykly.
- Obě jsou imperativní (říkáme, jak co dělat).
- Obě jsou Turingovsky úplné – řeší stejné problémy.
- Python, C++ – podporují oba paradigmata.

---

## c) Programovací jazyk – definice, typy

### Definice
**Programovací jazyk** je formální jazyk s přesně definovanou syntaxí (gramatika, pravidla zápisu) a sémantikou (význam příkazů), umožňující člověku zápis algoritmů ve formě, kterou lze (po překladu nebo interpretaci) vykonat počítačem.

### Úrovně abstrakce

**Strojový kód (Machine Code):**
- Binární instrukce přímo srozumitelné CPU (0 a 1).
- Specifický pro konkrétní architekturu (x86, ARM).
- Zcela nečitelný pro člověka. Příklad: `10110000 01100001`

**Assembler (nízkoúrovňový jazyk):**
- Symbolická reprezentace strojového kódu. Každá instrukce odpovídá jedné nebo několika strojovým instrukcím.
- Přeložen **assemblerem** na strojový kód.
- Stále architekturově specifický. Použití: ovladače, firmware, optimalizace výkonu.
```asm
MOV AL, 61h   ; přesuň hodnotu 61h do registru AL
ADD AL, 5     ; přičti 5 k AL
```

**Vyšší programovací jazyky (High-level languages):**
- Abstrakce od hardware – nezávislé na architektuře.
- Srozumitelnější pro člověka, produktivnější vývoj.
- Přeloženy **kompilátorem** nebo spouštěny **interpretem**.

### Překlad programu

**Kompilace:**
- Zdrojový kód (např. C++) → kompilátor → **nativní strojový kód** (spustitelný soubor .exe, .out).
- Překlad proběhne jednou před spuštěním.
- Výhody: rychlý výsledný kód, odhalení chyb při kompilaci.
- Příklady: C, C++, Rust, Go, Swift, Kotlin (do bytecode), Haskell.

**Interpretace:**
- Zdrojový kód spouštěn řádek po řádku **interpretem** za běhu.
- Žádná kompilace – přímé spuštění skriptu.
- Výhody: snadné ladění, rychlé prototypování, cross-platform.
- Nevýhody: pomalejší než kompilovaný kód.
- Příklady: Python, JavaScript (tradičně), Ruby, PHP, Bash.

**Hybridní přístup (JIT – Just-In-Time kompilace):**
- Zdrojový kód → bytecode → JIT kompilátor → strojový kód za běhu.
- Java: `.java` → javac → `.class` (bytecode) → JVM (Java Virtual Machine) + JIT.
- C#: `.cs` → .NET compiler → IL (Intermediate Language) → CLR + JIT.
- Python 3.12+, JavaScript V8 engine (Chrome) – také JIT.

---

## d) Příklady programovacích jazyků a jejich členění

### Podle paradigmatu

**Imperativní (říkáme, co a jak dělat):**
- Procedurální: C, Pascal, Fortran, COBOL.
- OOP: Java, C++, C#, Swift, Kotlin, Ruby.

**Deklarativní (říkáme, co chceme, ne jak):**
- Funkcionální: **Haskell, Erlang, Clojure**, F#. Čisté funkce, immutability, žádné side effects. **Lisp** – první funkcionální jazyk (1958).
- Logické: **Prolog** – dotazování na fakta a pravidla (AI, databáze).
- Databázové: **SQL** – deklarativní dotazování na data.

**Multiparadigmatické (podporují více paradigmat):**
- **Python:** OOP + procedurální + funkcionální prvky.
- **JavaScript:** OOP + funkcionální + prototypová dědičnost.
- **C++:** procedurální + OOP + generické programování.
- **Scala:** OOP + funkcionální (JVM).

### Podle úrovně

**Nízkoúrovňové:** Assembler, strojový kód.
**Středoúrovňové:** C – kombinuje vysokoúrovňové konstrukce s nízkoúrovňovým přístupem k paměti.
**Vysokoúrovňové:** Python, Java, C#, JavaScript, Ruby, Go, Rust.

### Populární jazyky a jejich použití

| Jazyk | Paradigma | Použití |
|---|---|---|
| **Python** | Multi | Data science, AI/ML, web backend, scripting, automatizace |
| **JavaScript** | Multi | Frontend web (všechny prohlížeče), backend (Node.js), mobilní (React Native) |
| **TypeScript** | OOP+Funkcionální | Typovaný superset JS, velké frontendové projekty |
| **Java** | OOP | Enterprise aplikace, Android, backend, Spring Framework |
| **C#** | OOP | Microsoft ekosystém, .NET, hry (Unity), ASP.NET |
| **C/C++** | Procedurální/OOP | OS (Linux v C), embedded, hry, výkonnostně kritické aplikace |
| **Rust** | Multi | Systémové programování, bezpečná alternativa C/C++ (bez memory leaks) |
| **Go (Golang)** | Multi | Cloud infrastruktura, mikroservisy (Docker, Kubernetes napsán v Go) |
| **Swift** | OOP+Funkcionální | iOS, macOS vývoj (Apple) |
| **Kotlin** | OOP+Funkcionální | Android (preferovaný Google od 2017), JVM backend |
| **PHP** | Multi | Web backend (WordPress, Laravel) – 70 % webu |
| **SQL** | Deklarativní | Databázové dotazy, veškerá relační DB |
| **R** | Funkcionální | Statistika, data analysis, bioinformatika |

### Aktuální trendy
- **Rust** – zaujme část low-level programování (MS, Google, Linux kernel přidávají Rust).
- **Python** dominuje v AI/ML, data science – nejpopulárnější jazyk světa (TIOBE 2024).
- **TypeScript** nahrazuje čistý JavaScript ve velkých projektech.
- **WebAssembly (WASM)** – kompilace C/C++/Rust do WASM pro běh v prohlížeči s nativní rychlostí.
- **AI-asistované programování:** GitHub Copilot, Cursor, Tabnine – LLM generují kód z přirozené řeči.

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(3 min)** Základní pojmy – proměnná (datový typ, scope), funkce/metoda (parametry, return), cyklus (for/while), API (REST, typy)
2. **(2 min)** Knihovny – stdlib vs. třetí strana, příklady; API klíče a autentizace
3. **(4 min)** OOP vs. procedurální – 4 pilíře OOP (zapouzdření, dědičnost, polymorfismus, abstrakce), srovnání, příklady kódu
4. **(2 min)** Překlad jazyka – kompilace vs. interpretace vs. JIT (Java, C++, Python příklady)
5. **(2 min)** Typy jazyků – imperativní/deklarativní, paradigmata; tabulka jazyků a použití
6. **(2 min)** Trendy – Python v AI, Rust, TypeScript, AI-asistované programování (Copilot)
