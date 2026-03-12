# 16. Metody pro řízení rizik v oblasti kybernetické bezpečnosti

> Souvisí s: [[14_Bezpecnost_HW_SW]] | [[15_Kyberneticka_kriminalita]] | [[17_Kyberneticke_utoky]] | [[08_Cloud_computing]]

---

## a) Vybrané metody analýzy rizik

### Co je analýza rizik?
**Analýza rizik** je proces identifikace, hodnocení a prioritizace potenciálních hrozeb a zranitelností, které mohou negativně ovlivnit aktiva organizace.

Výstup: **Risk Register** – seznam identifikovaných rizik s hodnocením a plány na jejich ošetření.

### Kvantitativní metody

**ALE (Annualized Loss Expectancy) – metoda:**
- Matematické vyjádření rizika v penězích.
- **SLE (Single Loss Expectancy):** finanční ztráta při jednom výskytu rizika. `SLE = Asset Value × Exposure Factor`
- **ARO (Annual Rate of Occurrence):** očekávaný počet výskytů za rok.
- **ALE = SLE × ARO** – roční očekávaná ztráta.
- Příklad: Server hodnoty 100 000 Kč, 50% pravděpodobnost poškození (EF=0,5) → SLE = 50 000 Kč. ARO = 0,1 (jednou za 10 let) → ALE = 5 000 Kč/rok.
- Výhoda: srovnání nákladů na opatření vs. ALE (stojí-li opatření méně než ALE, je efektivní).

**CVSS (Common Vulnerability Scoring System):**
- Standardizované skóre 0–10 pro závažnost zranitelností.
- **Base Score:** technické vlastnosti zranitelnosti (vektor útoku, složitost, dopad).
- **Temporal Score:** exploitovatelnost, patch dostupnost.
- **Environmental Score:** specifika prostředí organizace.
- Kritické = CVSS 9–10, Vysoké = 7–8,9, Střední = 4–6,9, Nízké = 0,1–3,9.

### Kvalitativní metody

**Matice rizik (Risk Matrix):**
- Vizualizace rizik na základě dvou parametrů: **Pravděpodobnost × Dopad**.
- Výsledné riziko = kombinace obou dimenzí → barevná mapa (zelená/žlutá/oranžová/červená).
- Intuitivní, rychlá, ale subjektivní.

```
Dopad:       Nízký   Střední   Vysoký   Kritický
Téměř jistý: Střed.  Vysoké    Kritické Kritické
Pravděpod.:  Nízké   Střed.    Vysoké   Kritické
Nepravděp.:  Nízké   Nízké     Střed.   Vysoké
Vzácný:      Nízké   Nízké     Nízké    Střed.
```

**FMEA (Failure Mode and Effects Analysis):**
- Systematická identifikace způsobů selhání systémů a jejich dopadů.
- Hodnocení: Závažnost × Pravděpodobnost × Detekovatelnost = RPN (Risk Priority Number).
- Původ: letecký průmysl, dnes široce používána v IT (FMECA).

**OCTAVE (Operationally Critical Threat, Asset, and Vulnerability Evaluation):**
- Organizačně zaměřená metoda – identifikuje klíčová aktiva a s nimi spojená rizika.
- Varianty: OCTAVE Allegro (zjednodušená), OCTAVE-S (malé organizace).

**STRIDE (Microsoft):**
- Threat modeling framework pro software: Spoofing, Tampering, Repudiation, Information disclosure, Denial of Service, Elevation of privilege.

**PASTA (Process for Attack Simulation and Threat Analysis):**
- 7-krokový proces kombinující technický a business pohled.

**ISO/IEC 27005:2022:**
- Viz [[15_Kyberneticka_kriminalita]] – norma pro řízení rizik v ISMS.
- Iterativní proces: Identifikace → Analýza → Hodnocení → Ošetření → Monitorování.

---

## b) Hrozba, riziko, aktivum v kybernetické bezpečnosti

### Klíčové pojmy

**Aktivum (Asset):**
- Cokoliv hodnotného pro organizaci, co potřebuje ochranu.
- **Hmotná aktiva:** hardware (servery, laptopy), fyzické záznamy.
- **Nehmotná aktiva:** software, data (databáze zákazníků, know-how), reputace.
- **Lidská aktiva:** zaměstnanci, jejich znalosti.
- **Procesní aktiva:** kritické obchodní procesy.
- Aktiva jsou **inventarizována a klasifikována** podle důležitosti (kritická/důležitá/podpůrná).

**Hrozba (Threat):**
- Potenciální příčina nežádoucího incidentu, která může poškodit aktivum.
- **Přírodní hrozby:** povodeň, zemětřesení, požár, bouřka.
- **Technické hrozby:** hardwarová porucha, výpadek napájení, software bug.
- **Lidské hrozby (záměrné):** hacker, insider, ransomware gang, APT.
- **Lidské hrozby (nezáměrné):** chyba administrátora, neúmyslné smazání dat, phishing oběť.

**Zranitelnost (Vulnerability):**
- Slabina systému, procesu nebo osoby, kterou může hrozba využít.
- Příklady: neopatchovaný OS, slabé heslo, nezabezpečený Wi-Fi, nezaškolení zaměstnanci, nesprávná konfigurace.
- Zranitelnosti evidovány v **CVE (Common Vulnerabilities and Exposures)** databázi (NVD – National Vulnerability Database).

**Riziko (Risk):**
- Pravděpodobnost, že hrozba využije zranitelnost a způsobí dopad na aktivum.
- **Riziko = Hrozba × Zranitelnost × Dopad (Hodnota aktiva)**
- Riziko ≠ hrozba (hrozba existuje, i když není riziko; riziko kombinuje všechny faktory).

**Incident (bezpečnostní):**
- Realizace rizika – faktický výskyt nežádoucí události.
- Příklady: ransomware útok, únik dat, výpadek systému.

### Ošetření rizik (Risk Treatment)
Po identifikaci a hodnocení má organizace 4 možnosti:

1. **Redukce rizika (Mitigate):** implementace bezpečnostních opatření ke snížení pravděpodobnosti nebo dopadu.
2. **Přenos rizika (Transfer):** pojištění kybernetického rizika, outsourcing bezpečnosti (MSSP).
3. **Akceptace rizika (Accept):** vědomé rozhodnutí riziko přijmout (pokud náklady na opatření > ALE).
4. **Vyhnutí se riziku (Avoid):** eliminace aktiva nebo procesu, který riziko generuje.

---

## c) PDCA cyklus, ITIL, COBIT

### PDCA cyklus (Demingův cyklus)

**Plan-Do-Check-Act** – základní cyklus neustálého zlepšování, aplikovaný v ISMS (ISO 27001), ITIL, i řízení rizik.

```
   ┌──────────────────────────────────┐
   │         PLAN (Plánuj)            │
   │ - Identifikuj cíle               │
   │ - Hodnoť rizika                  │
   │ - Navrhni bezpečnostní opatření  │
   └──────────────┬───────────────────┘
                  ↓
   ┌──────────────────────────────────┐
   │         DO (Dělej)               │
   │ - Implementuj opatření           │
   │ - Trénuj zaměstnance             │
   │ - Provozuj ISMS                  │
   └──────────────┬───────────────────┘
                  ↓
   ┌──────────────────────────────────┐
   │         CHECK (Kontroluj)        │
   │ - Monitoruj výkon opatření       │
   │ - Interní audity                 │
   │ - Měř KPI bezpečnosti            │
   └──────────────┬───────────────────┘
                  ↓
   ┌──────────────────────────────────┐
   │         ACT (Jednej)             │
   │ - Nápravná opatření              │
   │ - Aktualizuj politiky            │
   │ - Zlepšuj ISMS                   │
   └──────────────┬───────────────────┘
                  ↑ (cyklus se opakuje)
```

---

### ITIL (IT Infrastructure Library)

**ITIL** je rámec (framework) best practices pro správu IT služeb (ITSM – IT Service Management).

**Aktuální verze: ITIL 4 (2019)**

**Klíčové koncepty ITIL 4:**
- **SVS (Service Value System):** celkový systém vytváření hodnoty z IT služeb.
- **Service Value Chain:** aktivity transformující poptávku na hodnotu (Plan → Improve → Engage → Design & Transition → Obtain/Build → Deliver & Support).
- **34 management practices** (dříve procesy):
  - **Incident Management:** rychlá obnova normálního provozu po incidentu.
  - **Problem Management:** eliminace kořenových příčin opakujících se incidentů.
  - **Change Enablement:** řízené provádění změn v IT prostředí.
  - **Service Desk:** centrální kontaktní bod pro uživatele.
  - **Information Security Management:** integrace bezpečnosti do ITSM.
  - **Configuration Management (CMDB):** evidence IT aktiv a jejich vztahů.

**ITIL certifikace:** Foundation → Practitioner → Strategic Leader / Managing Professional.

---

### COBIT (Control Objectives for Information and Related Technologies)

**COBIT** (vydává ISACA) je rámec pro IT governance a správu IT, zaměřený na propojení IT s byznysovými cíli a řízením rizik.

**Aktuální verze: COBIT 2019**

**Klíčové principy COBIT:**
1. Splnění požadavků zainteresovaných stran.
2. Pokrytí celé organizace end-to-end.
3. Aplikace jednotného integrovaného rámce.
4. Umožnění holistického přístupu.
5. Oddělení governance od managementu.

**EDM vs. APO (Governance vs. Management):**
- **Governance (EDM):** Evaluate, Direct, Monitor – strategické rozhodování (C-level).
- **Management (APO, BAI, DSS, MEA):** plánování, budování, provoz, monitorování IT.

**COBIT doménový model (5 domén):**
- **EDM (Evaluate, Direct, Monitor):** governance
- **APO (Align, Plan, Organise):** alignment s byznysem
- **BAI (Build, Acquire, Implement):** budování a implementace
- **DSS (Deliver, Service, Support):** provoz a podpora
- **MEA (Monitor, Evaluate, Assess):** monitorování a hodnocení

**COBIT vs. ITIL:**
- COBIT: governance a management IT (co dělat, proč), compliance, audit.
- ITIL: best practices pro provoz IT služeb (jak dělat).
- Komplementární – organizace používají obojí.

---

## d) Vícevrstvá bezpečnost informačních systémů

### Defense in Depth (Hloubková obrana)
Princip vícevrstvé obrany – pokud selže jedna vrstva, další stále chrání. Vychází z vojenské strategie.

**Vrstvy bezpečnosti:**

```
┌─────────────────────────────────────┐
│         LIDÉ (Users)                │ ← školení, phishing povědomí, politiky
├─────────────────────────────────────┤
│       FYZICKÁ BEZPEČNOST            │ ← mantrap, CCTV, trezory
├─────────────────────────────────────┤
│        PERIMETR SÍTĚ                │ ← firewall, IPS, DMZ
├─────────────────────────────────────┤
│          INTERNÍ SÍŤ                │ ← VLAN, microsegmentace, IDS
├─────────────────────────────────────┤
│             HOST                    │ ← EDR, patch management, host firewall
├─────────────────────────────────────┤
│          APLIKACE                   │ ← WAF, SAST/DAST, secure coding
├─────────────────────────────────────┤
│             DATA                    │ ← šifrování, DLP, backup 3-2-1
└─────────────────────────────────────┘
```

### Bezpečnostní perimetr a jeho transformace

**Tradiční perimetr:**
- Ostrá hranice mezi „důvěryhodnou" interní sítí a „nedůvěryhodným" internetem.
- Firewall na perimetru chrání vše uvnitř.
- **Problém:** insider threats, vzdálení pracovníci, cloud aplikace, BYOD – tradiční perimetr se rozostřil.

**Zero Trust Architecture:**
- „Never trust, always verify" – žádná implicitní důvěra na základě lokace v síti.
- **Principy:**
  - Ověřovat identitu explicitně (MFA, device compliance).
  - Používat Least Privilege přístup.
  - Předpokládat kompromitaci – minimalizovat blast radius.
- **Implementace:** Microsoft Entra ID (Conditional Access), Google BeyondCorp, ZTNA řešení (Zscaler, Cloudflare Access).

### Technologie, procesy a lidé jako tři pilíře bezpečnosti

**Technologie (Tools):**
- SIEM (Security Information and Event Management) – centrální log agregace a korelace událostí. Splunk, Microsoft Sentinel, IBM QRadar.
- SOC (Security Operations Center) – tým monitorující bezpečnostní události 24/7.
- SOAR (Security Orchestration, Automation and Response) – automatizace odpovědi na incidenty.
- XDR (Extended Detection and Response) – integrovaná detekce přes endpoint, síť, cloud.

**Procesy:**
- ISMS dle ISO 27001, PDCA cyklus.
- Incident response procedury.
- Vulnerability management proces.
- Third-party risk management (hodnocení bezpečnosti dodavatelů).

**Lidé:**
- **Bezpečnostní kultura:** zaměstnanci jsou první a poslední linie obrany.
- **CISO (Chief Information Security Officer):** zodpovědnost za bezpečnostní strategii.
- **Security awareness training:** phishing simulace, e-learningové kurzy.
- **Red Team / Blue Team / Purple Team:**
  - Red Team: ofenzivní tým (útočníci) – hledá slabiny.
  - Blue Team: defenzivní tým – detekuje a reaguje.
  - Purple Team: spolupráce obou pro zlepšení obrany.

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(3 min)** Metody analýzy rizik – ALE (SLE×ARO), matice rizik, CVSS; kvantitativní vs. kvalitativní
2. **(3 min)** Aktivum, hrozba, zranitelnost, riziko – definice, vztahy, 4 způsoby ošetření rizika
3. **(2 min)** PDCA cyklus – Plan/Do/Check/Act, aplikace v ISMS
4. **(3 min)** ITIL 4 – SVS, Service Value Chain, klíčové praktiky (Incident, Problem, Change)
5. **(2 min)** COBIT 2019 – governance vs. management, 5 domén, COBIT vs. ITIL
6. **(2 min)** Defense in Depth – 7 vrstev, Zero Trust architektura, technologie/procesy/lidé
