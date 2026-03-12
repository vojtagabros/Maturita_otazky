# 9. Informační systémy

> Souvisí s: [[10_Firemni_IS]] | [[08_Cloud_computing]] | [[05_Pocitacove_site]]

---

## a) Informační podpora – nástroje, význam

### Co je informační podpora?
Informační podpora označuje využívání informačních technologií a systémů pro sběr, zpracování, ukládání a distribuci informací za účelem podpory rozhodování, řízení procesů a komunikace v organizaci.

### Nástroje informační podpory
- **Hardware:** servery, pracovní stanice, mobilní zařízení, síťová infrastruktura – viz [[01_Architektura_PC]], [[06_Sitova_zarizeni]].
- **Software:** databáze, aplikační servery, middleware, analytické nástroje.
- **Databáze:** relační (MySQL, PostgreSQL, Oracle, MS SQL Server) i nerelační (MongoDB, Redis, Cassandra).
- **Business Intelligence (BI):** nástroje pro analýzu a vizualizaci dat – Power BI, Tableau, Qlik.
- **Komunikační nástroje:** e-mail, videokonference (Teams, Zoom), intranet, podnikové portály.
- **Cloudové platformy:** SaaS aplikace – viz [[08_Cloud_computing]].

### Význam informační podpory
- Zrychlení a automatizace procesů (snížení manuální práce).
- Zlepšení kvality rozhodování (datová analytika, reporting).
- Sdílení informací v organizaci (eliminiace informačních sil – silos).
- Konkurenční výhoda – firmy s lepší informační podporou reagují rychleji na trh.
- Základní podmínka pro digitální transformaci.

---

## b) Základy problematiky IS – komponenty, funkce, význam

### Definice informačního systému
**Informační systém (IS)** je organizovaný soubor lidí, dat, procesů, informačních a komunikačních technologií, který shromažďuje, zpracovává, uchovává a distribuuje informace za účelem podpory rozhodování, koordinace, řízení, analýzy a vizualizace procesů v organizaci.

**Klíčové: IS = Lidé + Data + Procesy + Technologie**

### Základní komponenty IS
1. **Vstup (Input):** sběr a zachycení dat ze zdrojů (formuláře, senzory, databáze, soubory, API).
2. **Zpracování (Processing):** transformace vstupních dat na informace (výpočty, třídění, klasifikace, analýza).
3. **Výstup (Output):** prezentace informací uživatelům (reporty, dashboardy, notifikace, dokumenty).
4. **Úložiště (Storage):** databáze, datové sklady (Data Warehouse), archivy.
5. **Zpětná vazba (Feedback):** výstupy použity pro korekci vstupů a procesů.
6. **Řízení (Control):** pravidla a postupy zajišťující správné fungování systému.

### Funkce IS
- **Operační funkce:** zpracování každodenních transakcí (TPS – Transaction Processing System).
- **Manažerská funkce:** reporting, monitoring KPI (Key Performance Indicators).
- **Strategická funkce:** podpora dlouhodobého rozhodování, trendová analýza.
- **Komunikační funkce:** sdílení informací uvnitř i vně organizace.

### Význam IS
- Zvýšení efektivity a produktivity.
- Snížení chybovosti (automatizace vs. ruční zpracování).
- Lepší zákaznický servis.
- Dodržování legislativních povinností (reporting, GDPR).
- Umožnění práce na dálku (remote work).

---

## c) Typy a příklady IS

### TPS – Transaction Processing System
- Zpracování velkého množství rutinních transakcí v reálném čase.
- Příklady: bankovní systémy, pokladní systémy (POS – Point of Sale), rezervační systémy.
- Klíčové vlastnosti: rychlost, spolehlivost, ACID vlastnosti databáze (Atomicity, Consistency, Isolation, Durability).

### MIS – Management Information System
- Poskytuje manažerům periodické reporty pro operativní řízení.
- Agreguje data z TPS a dalších zdrojů.
- Příklady: měsíční reporty prodeje, reporty docházky, přehledy skladu.

### DSS – Decision Support System
- Podporuje strukturované i nestrukturované rozhodovací procesy.
- Kombinuje databáze, analytické modely, grafická rozhraní.
- Příklady: systémy pro plánování výroby, finanční modelování, logistická optimalizace.

### EIS / ESS – Executive Information System / Executive Support System
- Poskytuje vrcholovému managementu strategické informace.
- Dashboardy, KPI, trendy, výjimky – přehledně vizualizované.

### ERP – Enterprise Resource Planning
- Viz [[10_Firemni_IS]] – integruje všechny klíčové procesy firmy.

### CRM – Customer Relationship Management
- Viz [[10_Firemni_IS]] – správa vztahů se zákazníky.

### SCM – Supply Chain Management
- Řízení dodavatelského řetězce – od nákupu materiálu po dodání zákazníkovi.
- Příklady: SAP SCM, Oracle SCM Cloud.

### ECM – Enterprise Content Management
- Správa dokumentů, obsahu, workflow. Příklady: SharePoint, Confluence, Alfresco.

### Odborné/specializované IS
- **Zdravotnictví:** NIS (Nemocniční IS), PACS (obrazový archiv) – RTG snímky.
- **Vzdělávání:** LMS (Learning Management System) – Moodle, Canvas.
- **Veřejná správa:** ISZR (Informační systém základních registrů), datové schránky.
- **Logistika:** WMS (Warehouse Management System), TMS (Transport Management System).

---

## d) Prostorově orientované informační systémy (GIS)

### Co je GIS?
**GIS (Geographic Information System)** je informační systém pro sběr, ukládání, zpracování, analýzu a vizualizaci geograficky (prostorově) lokalizovaných dat.

GIS propojuje prostorová data (kde?) s atributovými daty (co?) a umožňuje jejich analýzu.

### Složky GIS
1. **Hardware:** servery, pracovní stanice, GPS přijímače, skenery, drony.
2. **Software:** GIS aplikace – ArcGIS (Esri), QGIS (open-source), Google Earth Engine.
3. **Data:** vektorová data (body, linie, polygony), rastrová data (satelitní snímky, digitální terénní modely).
4. **Metody:** analytické metody (prostorová analýza, interpolace, síťová analýza).
5. **Lidé:** geodeti, analytici, správci dat.

### Typy prostorových dat
- **Vektorová data:** body (POI – Points of Interest), linie (silnice, řeky), polygony (budovy, parcely, okresy).
- **Rastrová data:** mřížka pixelů – satelitní snímky, výškové modely DEM/DTM, mapy.
- **Formáty:** Shapefile (.shp), GeoJSON, KML/KMZ, GeoTIFF, WFS/WMS (webové služby).

### Souřadnicové systémy
- **WGS-84:** světový systém – GPS (zeměpisná šířka/délka). Příklad: 49.1951° N, 16.6068° E.
- **S-JTSK:** český systém – katastr nemovitostí.
- **UTM (Universal Transverse Mercator):** metrický systém, zóny.

### GIS analýzy
- **Překrytí vrstev (Overlay):** kombinace více vrstev pro zjištění prostorových vztahů.
- **Buffer (Obalová zóna):** oblasti v určité vzdálenosti od objektu (500 m od školy).
- **Síťová analýza:** nejkratší cesta, spádová oblast (Google Maps, navigace).
- **Interpolace:** odhad hodnot v neměřených místech (srážky, teploty).
- **Clustering:** shlukování prostorových dat (kriminalita, nemoci).

### Příklady využití GIS
- **Veřejná správa:** katastr nemovitostí (ČÚZK), územní plánování, evidence infrastruktury.
- **Doprava:** navigační systémy (Google Maps, Waze, HERE), plánování tras MHD.
- **Záchranné složky:** plánování tras IZS, povodňové zóny, evakuační plány.
- **Životní prostředí:** monitoring znečištění, krajinná ekologie, lesní hospodářství.
- **Logistika a retail:** analýza spádových oblastí, optimální umístění provozoven.
- **Smart City:** propojení senzorů IoT s GIS pro řízení města (parkování, osvětlení, odpadky).
- **Zemědělství (Precision Farming):** NDVI analýza satelitních snímků – zdraví porostů, variabilní hnojení.

### Propojení s dalšími technologiemi
- **IoT senzory:** real-time data z terénu (meteostanice, kvalita ovzduší) → GIS vizualizace.
- **Drony (UAV):** fotogrammetrie, 3D modely terénu, mapování nedostupných oblastí.
- **Strojové učení:** automatická klasifikace satelitních snímků (detekce lesních požárů, povodní).
- **Cloud GIS:** ArcGIS Online, Google Earth Engine – zpracování velkých dat bez lokálního hardware.

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(2 min)** Co je IS – definice, komponenty (vstup/zpracování/výstup/úložiště/zpětná vazba)
2. **(2 min)** Informační podpora – nástroje, databáze, BI, cloud; proč je důležitá
3. **(4 min)** Typy IS – TPS, MIS, DSS, EIS, ERP, CRM, SCM s příklady
4. **(3 min)** GIS – definice, vektorová vs. rastrová data, typy analýz
5. **(2 min)** Příklady využití GIS – katastr, navigace, IZS, smart city
6. **(2 min)** Propojení GIS s IoT, drony, AI, cloud
