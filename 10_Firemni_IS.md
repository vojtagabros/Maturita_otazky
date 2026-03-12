# 10. Firemní informační systémy

> Souvisí s: [[09_Informacni_systemy]] | [[08_Cloud_computing]] | [[20_Umela_inteligence]]

---

## a) Význam a specifikace firemních IS

### Proč firemní IS?
Moderní podniky generují obrovské množství dat a spravují komplexní procesy napříč odděleními (finance, logistika, HR, výroba, prodej). **Firemní informační systém** integruje a automatizuje tyto procesy, čímž:

- Eliminuje informační silos (každé oddělení má vlastní data, která nejsou sdílena).
- Zajišťuje konzistenci dat (jedna verze pravdy).
- Automatizuje rutinní procesy (snižuje manuální práci a chyby).
- Poskytuje manažerům real-time přehled o stavu podniku.
- Snižuje náklady a zvyšuje efektivitu (lean management).
- Umožňuje škálování (systém roste s firmou).

### Specifikace a výběr IS
Při výběru firemního IS se hodnotí:
- **Funkční požadavky:** pokrytí potřebných obchodních procesů.
- **Technické požadavky:** integrace s existujícími systémy, API, cloudová vs. on-premises verze.
- **Škálovatelnost:** schopnost růst s firmou.
- **TCO (Total Cost of Ownership):** celkové náklady (licence, implementace, školení, provoz).
- **Vendor support:** podpora, aktualizace, komunita.
- **Bezpečnost a GDPR compliance** – viz [[14_Bezpecnost_HW_SW]].

---

## b) ERP, CRM, BI – příklady využití

### ERP – Enterprise Resource Planning
**ERP** je komplexní podnikový informační systém integrující všechny klíčové procesy firmy v jednom centralizovaném systému sdílejícím společnou databázi.

**Moduly ERP:**
- **Finance a účetnictví:** hlavní kniha, pohledávky/závazky, výkaznictví.
- **Logistika a sklady:** nákup, příjem, skladové hospodářství, expedice.
- **Výroba (MRP/MRP II):** plánování výroby, BOM (kusovník), kapacitní plánování.
- **HR (Lidské zdroje):** mzdy, docházka, vzdělávání, nábor.
- **Prodej (Sales):** objednávky, fakturace, ceníky.
- **Projektové řízení:** plánování, sledování nákladů projektů.

**Implementace ERP:**
- Greenfield (od nuly) vs. Brownfield (migrace ze starého systému).
- Customizace: out-of-the-box vs. přizpůsobení → riziko problémů při upgradu.
- Cloud ERP (SaaS) vs. On-premises – trend přesunu do cloudu.

**Příklady ERP:**
- **SAP S/4HANA:** největší světový ERP, enterprise, velmi drahý. ČR: průmyslové podniky.
- **Microsoft Dynamics 365:** integrace s M365, vhodný pro střední a velké firmy.
- **Oracle ERP Cloud:** silný v financích a výrobě.
- **Odoo:** open-source, modulární, vhodný pro SME (malé a střední firmy).
- **POHODA, Money S5:** české řešení pro malé firmy.

---

### CRM – Customer Relationship Management
**CRM** je systém pro správu vztahů se zákazníky – sleduje interakce, příležitosti, obchodní cykly a pomáhá maximalizovat hodnotu zákaznické báze.

**Funkce CRM:**
- **Sales (Obchod):** správa leadů, příležitostí (deals), pipeline, forecast prodeje.
- **Marketing:** e-mailové kampaně, segmentace zákazníků, marketing automation.
- **Customer Service:** helpdesk, ticketing, SLA management, znalostní báze.
- **Analytika:** CLV (Customer Lifetime Value), konverzní míra, churn analýza.

**Příklady CRM:**
- **Salesforce:** největší cloudový CRM, velmi rozšířený globálně.
- **HubSpot:** oblíbený pro SME, freemium model, silný v marketingu.
- **Microsoft Dynamics 365 Sales:** integrace s Office 365, Teams.
- **Pipedrive:** jednoduchý pro prodejní týmy.
- **Zoho CRM, Freshsales:** cenově dostupné alternativy.

---

### BI – Business Intelligence
**BI** je soubor procesů, technologií a nástrojů pro transformaci surových dat na smysluplné informace a znalosti pro obchodní rozhodování.

**Architektura BI:**

```
Zdroje dat → ETL → Data Warehouse → OLAP/Analytika → Reporting/Dashboardy
```

- **ETL (Extract, Transform, Load):** výtah dat ze zdrojových systémů, čištění, transformace, nahrání do DWH.
- **Data Warehouse (DWH):** centrální analytický datový sklad (Snowflake, Google BigQuery, Amazon Redshift, Microsoft Synapse).
- **Data Mart:** tematický výřez DWH pro konkrétní oddělení.
- **OLAP (Online Analytical Processing):** multidimenzionální analýza dat (kostky, drill-down/roll-up).
- **Data Lake:** úložiště surových dat v původním formátu (Hadoop, AWS S3) – pro big data a ML.

**BI nástroje:**
- **Microsoft Power BI:** nejrozšířenější v ČR, integrace s M365, DAX jazyk.
- **Tableau:** vizuálně silný, drag and drop, oblíbený v analytice.
- **Qlik Sense:** asociativní datový model.
- **Looker (Google):** moderní, cloud-native.
- **Apache Superset:** open-source alternativa.

---

## c) Datové modelování

### Proč datové modelování?
Před implementací databáze je nutné správně navrhnout strukturu dat – datový model. Chyby v modelu jsou velmi nákladné na opravu po spuštění systému.

### Typy datových modelů (úrovně abstrakce)

1. **Konceptuální datový model (KDM):**
   - Nejvyšší úroveň abstrakce – co se modeluje, bez technických detailů.
   - Zaměřen na entity a jejich vztahy, srozumitelný i pro netechnické stakeholdery.
   - Nástroj: **ER diagram** (Entity-Relationship).

2. **Logický datový model:**
   - Upřesnění KDM – atributy entit, primární klíče, cizí klíče, normalizace.
   - Nezávislý na konkrétním DBMS (databázovém systému).

3. **Fyzický datový model:**
   - Konkrétní implementace v daném DBMS – tabulky, datové typy, indexy, partitioning.
   - Optimalizace výkonu.

### Datové modely podle struktury
- **Relační model:** data v tabulkách se vztahy přes klíče (nejrozšířenější). SQL databáze.
- **Hierarchický model:** stromová struktura (XML, LDAP/Active Directory).
- **Síťový model:** grafová struktura – předchůdce relačního modelu.
- **Objektový model:** data jako objekty (OOP přístup).
- **Dokumentový model:** dokumenty (JSON, XML) – MongoDB.
- **Grafový model:** uzly a hrany – Neo4j, Amazon Neptune (sociální sítě, doporučovací systémy).

---

## d) Konstrukty a principy KDM – ER diagramy, UML diagramy

### ER Diagram (Entity-Relationship Diagram)

Navržen **Peterem Chenem (1976)**, základní nástroj pro KDM.

**Komponenty ER diagramu:**

| Symbol | Název | Popis |
|---|---|---|
| Obdélník | **Entita** | Objekt reálného světa (Zákazník, Produkt, Objednávka) |
| Elipsa | **Atribut** | Vlastnost entity (Jméno, Cena, Datum). Podtržení = primární klíč |
| Kosočtverec | **Vztah** | Asociace mezi entitami (Nakupuje, Obsahuje) |
| Čára | **Spojení** | Propojení entit a vztahů |

**Kardinalita vztahů:**
- **1:1 (One-to-One):** jeden zaměstnanec má jeden pas.
- **1:N (One-to-Many):** jeden zákazník má mnoho objednávek.
- **M:N (Many-to-Many):** objednávka obsahuje mnoho produktů a produkt je v mnoha objednávkách → řeší se vazbovou (přechodovou) tabulkou.

**Crow's Foot notace:** alternativní zápis kardinalit grafickými symboly (ptačí nožičky) – běžná v moderních CASE nástrojích (Lucidchart, draw.io, ERD Plus).

**Příklad ER diagramu (e-shop):**
```
[ZÁKAZNÍK] ---<nakupuje>--- [OBJEDNÁVKA] ---<obsahuje>--- [PRODUKT]
  Jméno                      DatumObjednávky               Název
  E-mail                     StavObjednávky                Cena
  Adresa                     CelkováCena                   Sklad
```

---

### UML Diagramy (Unified Modeling Language)

UML je standardizovaný modelovací jazyk (OMG, 1997) pro vizualizaci, specifikaci, návrh a dokumentaci softwarových systémů. Obsahuje 14 typů diagramů ve 2 kategoriích.

**Strukturální diagramy (jak systém vypadá):**
- **Diagram tříd (Class Diagram):** třídy, atributy, metody, vztahy (dědičnost, asociace, kompozice) – základ OOP návrhu. Viz [[19_Programovani]].
- **Diagram komponent:** softwarové komponenty a jejich závislosti.
- **Diagram nasazení:** fyzické rozmístění softwaru na hardware.

**Behaviorální diagramy (jak systém funguje):**
- **Diagram případů užití (Use Case Diagram):** aktéři a jejich interakce se systémem. Komunikace s netechnickými stakeholdery.
- **Diagram sekvence (Sequence Diagram):** časová posloupnost zpráv mezi objekty/komponentami. Návrh API.
- **Diagram aktivit (Activity Diagram):** tok aktivit a rozhodování – podobné vývojovým diagramům.
- **Stavový diagram (State Machine Diagram):** stavy objektu a přechody mezi nimi.

**Příklad Use Case diagramu (e-shop):**
```
Zákazník --> [Přihlásit se]
Zákazník --> [Vyhledat produkt]
Zákazník --> [Přidat do košíku]
Zákazník --> [Zaplatit]
Admin    --> [Spravovat produkty]
Admin    --> [Zpracovat objednávky]
```

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(2 min)** Proč firemní IS – problémy bez IS, přínosy integrace
2. **(3 min)** ERP – moduly, implementace cloud vs. on-premises, SAP/MS Dynamics/Odoo
3. **(3 min)** CRM – funkce (sales/marketing/service), Salesforce, HubSpot
4. **(2 min)** BI – architektura (ETL → DWH → reporting), Power BI, OLAP
5. **(2 min)** Datové modelování – 3 úrovně (KDM/logický/fyzický), typy modelů
6. **(3 min)** ER diagram – entity, atributy, vztahy, kardinalita; UML – typy diagramů
