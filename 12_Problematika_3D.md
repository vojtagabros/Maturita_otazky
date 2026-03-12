# 12. Problematika 3D

> Souvisí s: [[11_Graficke_editory]] | [[13_Virtualni_realita]] | [[20_Umela_inteligence]]

---

## a) Základní dimenze

### Od 2D k 3D
- **1D (jednorozměrný prostor):** přímka, bod na přímce – popis pomocí jedné souřadnice (x).
- **2D (dvourozměrný prostor):** plocha definovaná dvěma souřadnicemi (x, y). Výkresy, fotografie, UI rozhraní, vektorová grafika.
- **3D (trojrozměrný prostor):** objem definovaný třemi souřadnicemi (x, y, z). Odpovídá fyzickému světu – modely, architektury, předměty k tisku.
- **4D (čtyřrozměrný):** 3D + čas → animace, simulace pohybu. Ve vizualizaci: čtvrtá dimenze jako barva nebo velikost.

### Souřadnicové systémy v 3D
- **Kartézský systém (x, y, z):** pravý nebo levý pravoúhlý systém (RHS vs. LHS – závisí na SW).
- **Pravostranný systém (Right-Hand System):** standard v matematice, Blenderu, OpenGL.
- **Levostranný systém (Left-Hand System):** DirectX, Unity.
- **Pivot point:** střed otáčení/transformace objektu.

### Základní transformace v 3D
- **Translace (Move):** posun objektu podél os.
- **Rotace (Rotate):** otočení kolem osy (Euler angles: Yaw/Pitch/Roll) nebo quaterniony.
- **Škálování (Scale):** uniformní (zachování proporcí) nebo non-uniformní.
- **Matice transformace:** 4×4 homogenní matice kombinující všechny transformace.

### Geometrie 3D objektů
- **Polygon mesh:** síť polygonů (většinou trojúhelníků nebo čtyřúhelníků). Základ herní grafiky a animací.
- **NURBS (Non-Uniform Rational B-Splines):** hladké křivky a plochy definované matematicky. Standard v CAD a průmyslovém designu.
- **Subdivision Surface (Sub-D):** nízkopolygonální model s algoritmickým vyhlazením (Catmull-Clark).
- **Volumetrická data:** voxely (3D pixely) – medicínské CT/MRI, vědecké simulace, VDB (OpenVDB).
- **Point Cloud:** mrak bodů naměřený LiDARem nebo fotogrammetrií.

---

## b) Typy nástrojů a práce v 2D/3D

### 2D nástroje (pro výrobu a ICT)
- **CAD 2D:** technické výkresy, plány (AutoCAD LT, QCAD, LibreCAD).
- **Vektorová grafika:** Illustrator, Inkscape – viz [[11_Graficke_editory]].
- **Schematické nástroje:** EDA (Eagle, KiCad) – návrh plošných spojů.
- **GIS 2D:** QGIS, ArcGIS – viz [[09_Informacni_systemy]].

### 3D parametrické a CAD nástroje
- **Autodesk AutoCAD:** 2D/3D, průmyslový standard pro technické výkresy, architektura.
- **SolidWorks (Dassault Systèmes):** parametrické 3D CAD pro strojní inženýrství, feature-based modelování. Standard v průmyslu.
- **PTC Creo (ProE):** konkurent SolidWorks, silný v průmyslové výrobě.
- **Fusion 360 (Autodesk):** cloud-based CAD/CAM/CAE, populární pro prototypování a 3D tisk.
- **FreeCAD:** open-source parametrické CAD.
- **Rhinoceros (Rhino):** NURBS modeling, architektura, produktový design, jewellery.
- **CATIA (Dassault):** automotive a aerospace průmysl (Airbus, BMW).

### 3D modelovací a animační nástroje
- **Blender:** open-source, zdarma, kompletní pipeline (modelování, rigging, animace, rendering, VFX, video editace). Dnes standard i v profesionální oblasti.
- **Autodesk Maya:** profesionální animace a VFX, herní průmysl a film (Pixar, DreamWorks).
- **Autodesk 3ds Max:** architektonická vizualizace, herní modely, vizualizace interiérů.
- **Cinema 4D (Maxon):** motion graphics, MoGraph, populární v reklamě.
- **ZBrush (Pixologic/Maxon):** digitální sochařství, organické tvary, detailní povrchy (herní postavy, filmoví tvorové).

### Workflow 3D modelování
1. **Blockout/Sculpting:** hrubý tvar, proporce.
2. **Retopologie:** vytvoření čistého topology mesh (low-poly) ze sculptovaného modelu.
3. **UV Unwrapping:** rozvinutí 3D povrchu do 2D mapy pro texturování.
4. **Texturování:** malba textur (Substance Painter, Blender), PBR materiály (Physically Based Rendering).
5. **Rigging:** kostra a kontrolní prvky pro animaci (characters, mechanismy).
6. **Animace:** klíčové snímky, mocap, procedurální animace.
7. **Lighting + Rendering:** osvětlení scény, výpočet výsledného obrazu.

---

## c) Význam v ICT, SW pro 2D/3D modelování

### Využití 3D modelování v ICT a průmyslu

**Průmyslový design a výroba:**
- CAD modely → výrobní dokumentace → CNC obrábění → kontrola kvality.
- **Simulace (CAE – Computer-Aided Engineering):** FEM analýza (pevnostní výpočty), CFD (proudění tekutin), tepelné simulace – ANSYS, Abaqus, SolidWorks Simulation.
- **Digitální dvojče (Digital Twin):** virtuální replika fyzického produktu/zařízení/budovy aktualizovaná real-time daty ze senzorů IoT.

**Architektura a stavebnictví:**
- **BIM (Building Information Modeling):** inteligentní 3D model budovy obsahující veškeré informace (materiály, ceny, instalace) – Revit (Autodesk), ArchiCAD.
- Architektonické vizualizace, virtuální prohlídky – viz [[13_Virtualni_realita]].

**Zdravotnictví a biologie:**
- Vizualizace anatomie, chirurgické plánování, biomedicínské implantáty.
- 3D tisk chirurgických nástrojů, ortéz, protéz na míru.
- Molekulární modelování léčiv.

**Zábava a média:**
- Herní průmysl: 3D modely postav, prostředí, vozidel.
- Film a VFX: CGI efekty, animované filmy.
- Reklama: produktové vizualizace.

**Vzdělávání a trénink:**
- Simulátory pro výcvik pilotů, chirurgů, řidičů.
- Interaktivní vzdělávací materiály.

---

## d) Aditivní výroba – 3D tisk

### Co je 3D tisk (aditivní výroba)?
3D tisk = přidávání materiálu vrstvu po vrstvě (aditivní) → fyzický objekt z digitálního 3D modelu. Opak je subtraktivní výroba (frézování, soustružení = odebírání materiálu).

### Technologie 3D tisku

**FDM (Fused Deposition Modeling) / FFF:**
- Nejrozšířenější, nejlevnější metoda (Prusa, Creality Ender, Bambu Lab).
- Princip: plastové vlákno (filament) je taveno tryskou a nanášeno vrstvu po vrstvě.
- Materiály: **PLA** (biologicky rozložitelný, snadný tisk), **ABS** (pevnější, tepelně odolnější), **PETG** (kombinace vlastností), **TPU** (flexibilní), Nylon, PC, kompozity (s uhlíkovými vlákny).
- Přesnost: ±0,1–0,3 mm. Vrstva: 0,1–0,3 mm.

**SLA (Stereolithography) / MSLA (LCD):**
- UV laser nebo LCD displej vytvrzuje fotopolymerovou pryskyřici (resin).
- Velmi vysoké rozlišení a detaily – klenotnictví, zubní protetika, figurky.
- Nevýhoda: toxické materiály, menší tisková plocha, post-processing (mytí + vytvrzení).
- Příklady: Formlabs Form, Elegoo Saturn.

**SLS (Selective Laser Sintering):**
- Laser slinuje práškový nylon/polyamid.
- Bez potřeby podpor, pevné díly, průmyslové využití. Dražší technologie.
- Varianta: **MJF (Multi Jet Fusion, HP)** – rychlejší, průmyslová výroba.

**DMLS/SLM (Direct Metal Laser Sintering / Selective Laser Melting):**
- Sintrování/tavení kovového prášku (titan, nerezová ocel, hliník, kobalt-chrom) laserem.
- Letecký průmysl, medicínské implantáty, prototypy kovových dílů. Velmi drahé.

**Bioprinting:**
- Tisk s biokompatibilními materiály a živými buňkami – výzkum náhradních tkání, orgánů.

### Parametry 3D tisku (FDM)
- **Výška vrstvy:** 0,1 mm (detailní) – 0,3 mm (rychlý) – ovlivňuje kvalitu a čas tisku.
- **Výplň (Infill):** 5–100 % – hustota vnitřní struktury (mřížka, honeycomb, gyroid).
- **Teplota trysky:** PLA ~200°C, ABS ~230°C, PETG ~235°C.
- **Teplota podložky:** PLA ~60°C, ABS ~100°C (vyhřívaná podložka).
- **Rychlost tisku:** 40–500 mm/s (závisí na tiskárně a materiálu).
- **Podpory (Supports):** pro přesahy >45° – automaticky generované, manuálně nastavitelné.

### Workflow 3D tisku
1. **3D modelování** (Fusion 360, Blender, Tinkercad) nebo stažení modelu (Printables, Thingiverse, MakerWorld).
2. **Slicing** – převod STL/3MF modelu na G-code (vrstvy + instrukce pro tiskárnu). SW: **PrusaSlicer, Bambu Studio, Cura (Ultimaker), Simplify3D**.
3. **Tisk** – fyzický proces (FDM, SLA...).
4. **Post-processing:** odstranění podpor, broušení, lakování, povrchová úprava.

### Průmyslové uplatnění
- **Rapid prototyping:** rychlé ověření designu před sériovou výrobou.
- **Malosériová výroba:** zakázkové díly bez nutnosti forem.
- **Náhradní díly on-demand:** tisk v místě potřeby (loď, vojenský terén).
- **Customizace:** ortézy, protézy, zuby, sluchadla přizpůsobené konkrétnímu pacientovi.

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(2 min)** Dimenze – 1D/2D/3D/4D, souřadnicové systémy, základní transformace
2. **(2 min)** Typy 3D geometrie – polygon mesh, NURBS, sculpting, point cloud
3. **(3 min)** 3D nástroje – CAD (SolidWorks, Fusion), modelovací (Blender, Maya, ZBrush)
4. **(2 min)** Využití v ICT – průmysl (CAE, digital twin), BIM, zdravotnictví, hry/film
5. **(4 min)** 3D tisk – technologie (FDM, SLA, SLS, DMLS), materiály (PLA/ABS/PETG), parametry
6. **(2 min)** Workflow tisku – modelování → slicing → tisk → post-processing; průmyslové využití
