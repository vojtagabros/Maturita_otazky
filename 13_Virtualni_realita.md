# 13. Virtuální, Rozšířená a Smíšená realita

> Souvisí s: [[12_Problematika_3D]] | [[01_Architektura_PC]] | [[20_Umela_inteligence]]

---

## a) Základní principy a popis významu pro ICT

### Immersive Technologies – spektrum reality
Paul Milgram a Fumio Kishino (1994) definovali **Reality-Virtuality Continuum** – kontinuum od čisté fyzické reality po čistou virtuální realitu.

```
Fyzická realita ←→ AR (rozšířená) ←→ MR (smíšená) ←→ VR (virtuální)
```

### VR – Virtual Reality (Virtuální realita)
- Kompletně **syntetické, počítačem generované prostředí**, které zcela nahrazuje reálný svět.
- Uživatel je **plně ponořen (immersed)** do virtuálního prostoru – vidí, slyší, někdy cítí (haptika).
- Klíčové vlastnosti:
  - **Immerze:** míra, do jaké uživatel „věří", že je ve virtuálním světě.
  - **Přítomnost (Presence):** psychologický stav „bytí tam" – ovlivněn FOV, latencí, rozlišením.
  - **Interaktivita:** možnost měnit virtuální svět.
- **Motion sickness (kinetóza):** nevolnost způsobená nesouladem vizuálního vjemu a vestibulárního aparátu. Kritická latence: < 20 ms (ideálně < 7 ms), refresh rate ≥ 90 Hz.

### Technické parametry VR
- **FOV (Field of View):** zorné pole headsetu. Lidské oko ~210° (oba oči). Headsety: ~100–120°.
- **Obnovovací frekvence:** 72/90/120/144 Hz – vyšší = plynulejší, méně sickness.
- **Rozlišení na oko:** Quest 3 = 2064×2208/oko, PSVR2 = 2000×2040/oko.
- **IPD (Interpupillary Distance):** vzdálenost mezi zornicemi – individuální nastavení pro správné stereo vidění.
- **6DoF (Six Degrees of Freedom):** plná svoboda pohybu – 3D pohyb (x, y, z) + 3D rotace (Pitch/Yaw/Roll). Oproti 3DoF (pouze rotace hlavy).
- **Inside-out tracking:** kamery přímo na headsetě sledují okolní prostředí (SLAM algoritmus). Meta Quest 3, Apple Vision Pro.
- **Outside-in tracking:** externí základní stanice sledují headset (Valve Index, starý Oculus Rift). Přesnější, ale komplikovanější setup.

---

## b) Nástroje a postup práce ve virtuální realitě

### Hardware pro VR

**Standalone VR headsety** (vše integrované, bez PC):
- **Meta Quest 3:** nejpopulárnější, procesor Snapdragon XR2 Gen 2, barevná průchozí (passthrough) kamera, MR schopnosti.
- **Meta Quest 3S:** dostupnější varianta.
- **PICO 4 (ByteDance):** konkurent Questu, Enterprise verze.

**PC VR headsety** (vyžadují výkonné PC s dedikovanou GPU):
- **Valve Index:** nejkvalitnější zážitek, 144 Hz, finger tracking kontrolery. Steam VR.
- **HP Reverb G2:** vysoké rozlišení (2160×2160/oko), Windows Mixed Reality.
- **Bigscreen Beyond:** nejtenčí PCVR headset, OLED displeje.

**Konsolové VR:**
- **PlayStation VR2 (Sony, 2023):** OLED, eye tracking, 4K HDR, PS5 exkluzivní.

**Enterprise/Profesionální:**
- **Apple Vision Pro (2024):** smíšená realita, eye/hand/voice tracking, micro-OLED 4K, visionOS.
- **Microsoft HoloLens 2:** AR headset pro průmysl a zdravotnictví.

### Software a platformy

**Herní VR platformy:**
- **SteamVR (Valve):** největší PC VR platforma s tisíci hrami.
- **Meta Quest Store / Meta Horizon:** ekosystém pro Quest headsety.
- **PlayStation Store VR2:** PS5 platforma.

**Vývojové nástroje:**
- **Unity:** nejrozšířenější herní engine pro VR/AR vývoj (C#). XR Interaction Toolkit.
- **Unreal Engine 5:** fotorealistická grafika, Lumen/Nanite, VR podpora.
- **WebXR:** VR/AR v prohlížeči bez instalace (Three.js, Babylon.js, A-Frame).
- **OpenXR:** standardizované API pro VR/AR aplikace (rozhraní pro všechny headsety).

### Tvorba VR obsahu – workflow
1. **Preproduction:** scénář, storyboard, design prostředí.
2. **3D modelování a texturování** – viz [[12_Problematika_3D]]. Low-poly modely (real-time rendering).
3. **Optimalizace:** draw calls, Level of Detail (LOD), occlusion culling – cílový výkon 90 FPS+.
4. **Implementace v enginu:** Unity/Unreal – XR SDK, física, interakce.
5. **Zvuk:** prostorový (3D binaural) zvuk – klíčový pro immerzi. Ambisonic audio.
6. **Testování:** user testing, měření latence, comfort testing (motion sickness).
7. **Deploy:** distribuce na headsety (Quest store, SteamVR, sideloading).

---

## c) Prostředky pro práci ve VR, interakce, simulátory

### Vstupní zařízení a interakce

**Kontrolery (Controllers):**
- 6DoF kontrolery s tlačítky, joysticky, trigery (Meta Touch, Valve Index kontrolery).
- Hmatová zpětná vazba (haptika) – vibrace různých frekvencí a intenzit.

**Hand Tracking (sledování rukou):**
- Kamery headsetu sledují pohyb prstů bez kontrolerů.
- Meta Quest 3, Apple Vision Pro – gestura rukou jako primární vstup.

**Eye Tracking:**
- PSVR2, Apple Vision Pro, HTC VIVE Pro Eye.
- Aplikace: foveated rendering (vykreslování detailů jen tam, kam se uživatel dívá) → výrazné snížení GPU požadavků.

**Treadmilly a haptické vesty:**
- **Omni Treadmill (Virtuix):** omnidirektionální běžecký pás pro chůzi ve VR.
- **Haptické vesty (bHaptics, Subpac):** fyzické pocity výbuchů, doteků.
- **Haptické rukavice:** HaptX Gloves – simulace taktilní zpětné vazby.
- **Full Body Tracking:** Vive Trackery na kotníky a pas.

### Simulátory
Simulátory jsou jednou z nejdůležitějších aplikací VR – bezpečný a levný výcvik pro reálné situace.

- **Letecké simulátory:** Výcvik pilotů (CAE, FlightSafety International) – plnohodnotné Full Flight Simulatory (FFS) certifikované FAA/EASA. Microsoft Flight Simulator VR pro hobbyisty.
- **Vojenské simulátory:** výcvik vojáků bez rizika ztráty života (střelba, taktika, mise).
- **Medicínské simulátory:** nácvik chirurgických zákroků, endoskopie (Osso VR, Touch Surgery).
- **Řidičské simulátory:** výcvik řidičů (Waymo, autonomní vozidla), rehabilitace.
- **Průmyslové:** výcvik pro práci s nebezpečnými stroji, plynové sítě (Shell VR), montáž.
- **Architektonické prohlídky:** zákazníci prochodí budovu před jejím postavením (Revit + VR export).

### Příklady využití VR
- **Vzdělávání:** virtuální laboratoře, historické simulace, anatomie (3D4Medical), jazykové immersive kurzy.
- **Psychoterapie:** léčba fóbií (akrofobie, arachnofobie), PTSD, úzkostných poruch – exposition therapy.
- **Rehabilitace:** fyzická rehabilitace po mozkových příhodách (MindMaze), motivační cvičení.
- **Real estate:** virtuální prohlídky nemovitostí.
- **Retail a e-commerce:** virtuální zkoušení oblečení, nábytku (IKEA Place).

---

## d) Rozšířená a smíšená realita (AR a MR)

### AR – Augmented Reality (Rozšířená realita)
- Reálný svět je **doplněn digitálními prvky** (objekty, texty, animace) zobrazovanými v reálném čase.
- Uživatel vidí reálné prostředí + virtuální overlay.
- Implementace: **smartphone/tablet kamera** (nejrozšířenější), AR brýle, HUD displeje.

**Technologie AR:**
- **Marker-based AR:** detekce specifického vzoru (QR kód, obrázek) → zobrazení obsahu. Příklad: AR vizitky, učebnice.
- **Markerless AR (SLAM):** detekce povrchů a prostoru bez značky. ARKit (Apple), ARCore (Google).
- **Location-based AR:** GPS poloha určuje obsah. Pokémon GO – nejznámější příklad.

**Příklady AR aplikací:**
- **Pokémon GO:** mobilní AR hra, 2016, vzor pro location-based AR.
- **Google Maps Live View:** AR navigace – šipky přímo na pohledu z kamery.
- **IKEA Place:** virtuální umístění nábytku do místnosti.
- **Snapchat/Instagram filtry:** face tracking AR efekty.
- **Průmysl:** AR brýle pro servisní techniky – návody přímo na stroji (PTC Vuforia, Scope AR).
- **Zdravotnictví:** navigace při chirurgii (zvýraznění anatomických struktur).
- **Vzdělávání:** AR učebnice (Anatomy 4D).

---

### MR – Mixed Reality (Smíšená realita)
- **Virtuální objekty jsou zakotveny v reálném světě** a reagují na reálné prostředí.
- Na rozdíl od AR: virtuální objekty jsou ovlivňovány reálnými objekty (schování za stěnou, fyzická interakce).
- MR = vyšší stupeň integrace virtuálního a reálného než AR.

**MR technologie:**
- **Depth senzory:** LiDAR (Apple iPhone 12+, iPad Pro), Time-of-Flight kamery → přesné mapování prostoru.
- **Spatial mapping:** 3D mapa reálného prostoru → virtuální objekty na ni reagují.
- **Průchozí (Passthrough) kamera:** barevný obraz z kamer headsetu místo průhledného skla.

**Příklady MR zařízení:**
- **Apple Vision Pro (visionOS):** hybridní VR/MR, vidí přes průchozí kamery, virtuální okna v reálném prostoru.
- **Microsoft HoloLens 2:** průhledný displej (optický see-through), průmyslové aplikace (Boeing – opravy letadel, příručky v zorném poli).
- **Meta Quest 3:** barevný passthrough, MR schopnosti dostupné za nižší cenu.
- **Magic Leap 2:** enterprise MR platforma.

### Srovnání VR, AR, MR

| Vlastnost | VR | AR | MR |
|---|---|---|---|
| Reálný svět viditelný? | Ne | Ano | Ano |
| Virtuální objekty reagují na realitu? | — | Omezeně | Ano, plně |
| Typický hardware | Headset | Smartphone, brýle | Headset (HoloLens, Vision Pro) |
| Příklady | Beat Saber, Half-Life Alyx | Pokémon GO, IKEA Place | HoloLens průmysl, Vision Pro |
| Zakotvení v prostoru | Ne | Omezeně | Ano (spatial anchors) |

### XR – Extended Reality
Zastřešující termín pro VR, AR a MR – **Extended Reality (rozšířená/rozšiřující realita)** jako celá kategorie technologií.

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(2 min)** Reality-Virtuality Continuum – spektrum od AR po VR; definice VR, AR, MR
2. **(3 min)** VR principy – immerze, presence, FOV, latence (<20ms), 6DoF, inside-out tracking
3. **(3 min)** Hardware a SW – Quest 3, Valve Index, Vision Pro; Unity, Unreal, OpenXR; workflow tvorby
4. **(3 min)** Interakce – kontrolery, hand tracking, eye tracking, haptika; simulátory (piloti, chirurgie)
5. **(2 min)** AR – marker-based vs. SLAM, ARKit/ARCore; příklady (Pokémon GO, IKEA Place, průmysl)
6. **(2 min)** MR vs. AR rozdíl – zakotvení v prostoru, HoloLens, Vision Pro; XR zastřešující termín
