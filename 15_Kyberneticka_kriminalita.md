# 15. Kybernetická kriminalita

> Souvisí s: [[14_Bezpecnost_HW_SW]] | [[16_Rizeni_rizik]] | [[17_Kyberneticke_utoky]] | [[07_Zabezpeceni_siti]]

---

## a) Prevence, typy trestných činů

### Typy kybernetických trestných činů

**Trestné činy páchané pomocí počítačů (computer-assisted crimes):**
- Klasické trestné činy usnadněné digitálními technologiemi.
- **Kybernetický podvod:** phishing, online podvody, fake eshopy.
- **Kybernetická krádež:** krádež identity, kreditních karet, bankovních přihlašovacích údajů.
- **CSAM (Child Sexual Abuse Material):** šíření dětské pornografie online.
- **Kybernetická stalking a harassement:** pronásledování a obtěžování online.
- **Porušení autorských práv:** nelegální sdílení softwaru, filmů, hudby.

**Trestné činy zaměřené na počítače (computer-targeted crimes):**
- Cílem je přímo IT systém nebo síť.
- **Neoprávněný přístup do systému (hacking):** § 230 TZ ČR – neoprávněný přístup k počítačovému systému.
- **Šíření malwaru:** ransomware, viry, worms – § 230 TZ.
- **DDoS útoky:** znepřístupnění služby.
- **Sabotáž kritické infrastruktury:** elektrorozvodné sítě, vodovody, nemocniční systémy.
- **Kybernetická špionáž:** krádež státních nebo firemních tajemství.

**Hybridní hrozby a kyberkriminalita jako služba (CaaS):**
- **Ransomware-as-a-Service (RaaS):** zločinecké skupiny nabízejí ransomware jako službu (LockBit, REvil, DarkSide).
- **Initial Access Brokers:** prodej přístupu k napadeným systémům na dark webu.
- **Bulletproof hosting:** hostingové služby ignorující žádosti o spolupráci orgánů činných v trestním řízení (Rusko, jiné jurisdikce).

### Prevence

**Technická prevence:**
- Pravidelné aktualizace OS a softwaru (patch management).
- MFA pro všechny citlivé účty.
- Síťová segmentace a firewall pravidla.
- Zálohy podle pravidla **3-2-1** (3 kopie, 2 media, 1 offsite).
- EDR/XDR řešení pro detekci pokročilých hrozeb.
- Penetrační testování a vulnerability management.

**Organizační prevence:**
- Bezpečnostní školení zaměstnanců (phishing simulations).
- Bezpečnostní politiky a procedury.
- Incident response plan.
- Pojištění kybernetického rizika.

**Legislativní prevence:**
- Trestní odpovědnost odrazuje potenciální útočníky.
- Mezinárodní spolupráce (Europol, Interpol, EC3 – European Cybercrime Centre).

---

## b) Aktuální právní normy v ČR

### Zákon o kybernetické bezpečnosti

**Zákon č. 181/2014 Sb. (původní ZKB) – nyní nahrazen:**
- Definoval povinnosti pro provozovatele kritické informační infrastruktury (KII) a informační systémy kritické infrastruktury (ISZKI).
- Orgánem dohledu: **NÚKIB (Národní úřad pro kybernetickou a informační bezpečnost)** – zřízen 2017.

**Zákon č. 205/2025 Sb. (nový zákon o kybernetické bezpečnosti):**
- Transponuje směrnici **NIS2** do českého práva (platnost od 2025).
- Rozšiřuje okruh povinných subjektů (viz NIS2 sekce c).
- Zavádí přísnější povinnosti a vyšší sankce.

**Trestní zákoník (zákon č. 40/2009 Sb.):**
- **§ 230 – Neoprávněný přístup k počítačovému systému a nosiči informací:** až 3 roky odnětí svobody (nebo 5 let při způsobení škody, 8 let při napadení kritické infrastruktury).
- **§ 231 – Opatření a přechovávání přístupového zařízení a hesla k počítačovému systému:** přípravné jednání pro hacking.
- **§ 232 – Poškození záznamu v počítačovém systému:** modifikace, smazání dat.
- **§ 270 – Porušení autorského práva:** nelegální software, šíření autorsky chráněného obsahu.
- **§ 182 – Porušení tajemství dopravovaných zpráv:** neoprávněné čtení komunikace.

**Zákon o zpravodajských službách, GDPR** – viz [[08_Cloud_computing]].

### Prováděcí předpisy
- **Vyhláška č. 82/2018 Sb.** (o bezpečnostních opatřeních) – konkrétní technická a organizační opatření pro povinné subjekty.
- **Vyhláška č. 317/2014 Sb.** – o ISVS (Informační systémy veřejné správy) a jejich bezpečnosti.
- **Nařízení vlády č. 315/2021 Sb.** – seznam prvků kritické infrastruktury.

---

## c) Směrnice NIS2, normy ISO/IEC

### Směrnice NIS2 (EU 2022/2555)

**NIS = Network and Information Systems**. NIS2 je aktualizace původní NIS směrnice (2016), platná od ledna 2023 s povinností transpozice do října 2024.

**Klíčové změny oproti NIS1:**
- **Výrazné rozšíření okruhu povinných subjektů:** od cca 1 000 subjektů v ČR na přibližně 6 000+.
- **Nové sektory:** potravinářství, výroba, odpadové hospodářství, poštovní služby, digitální infrastruktura.
- **Dvě kategorie:**
  - **Základní subjekty (Essential Entities):** energetika, doprava, bankovnictví, zdravotnictví, digitální infrastruktura, vesmír. Přísnější povinnosti, aktivní dohled.
  - **Důležité subjekty (Important Entities):** výroba, potravinářství, poštovní, chemický průmysl. Reaktivní dohled.
- **Přísnější sankce:** až 10 milionů EUR nebo 2 % světového obratu (základní subjekty); 7 milionů EUR nebo 1,4 % (důležité).
- **Supply chain bezpečnost:** povinnost řídit bezpečnost dodavatelského řetězce.
- **Hlášení incidentů:** 24 hodin (early warning) → 72 hodin (hlášení) → 1 měsíc (závěrečná zpráva).
- **Odpovědnost managementu:** vedení organizace osobně zodpovídá za dodržování NIS2.

---

### ISO/IEC 27001:2022

**Mezinárodní norma** pro systémy řízení bezpečnosti informací (ISMS – Information Security Management System).

**Klíčové aspekty:**
- Procesní přístup: PDCA cyklus (Plan-Do-Check-Act) – viz [[16_Rizeni_rizik]].
- Hodnocení rizik → výběr vhodných bezpečnostních kontrol.
- **Annex A:** 93 bezpečnostních kontrol ve 4 kategoriích:
  - Organizační kontroly (37) – politiky, role, odpovědnosti.
  - Lidé (8) – přijímání zaměstnanců, školení, disciplinární řízení.
  - Fyzické kontroly (14) – zabezpečení prostor, čisté stoly.
  - Technologické kontroly (34) – autentizace, šifrování, logování, patch management.
- **Certifikace:** organizace mohou být certifikovány akreditovaným certifikačním orgánem.
- **Aktualizace 2022:** přidány nové kontroly pro cloud security, threat intelligence, ICT supply chain.

---

### ISO/IEC 27002:2022

**Implementační příručka** pro bezpečnostní kontroly definované v ISO 27001 Annex A. Poskytuje detailní návod, jak každou kontrolu implementovat.
- Není certifikovatelná (na rozdíl od 27001) – pouze doporučení.
- Popisuje 93 kontrol s cíli, doporučeními a implementačními návody.

---

### ISO/IEC 27005:2022

**Norma pro řízení rizik** v kontextu informační bezpečnosti. Viz [[16_Rizeni_rizik]] pro detail.
- Poskytuje rámec pro identifikaci, analýzu, hodnocení a ošetření rizik.
- Aktualizace 2022: lepší integrace s ISO 31000 (obecné řízení rizik), explicitnější event-based přístup vs. asset-based.

---

## d) Význam kybernetické bezpečnosti v ICT

### Ekonomické dopady
- Celosvětové náklady na kyberkriminalitu: odhadovány na **8 bilionů USD v roce 2023**, očekávány na 10,5 bilionu USD v 2025 (Cybersecurity Ventures).
- Průměrné náklady na datový průnik (data breach): **4,45 milionu USD** (IBM Cost of a Data Breach Report 2023).
- Ransomware: průměrná výplata výkupného přesáhla milion USD (2023).

### Dopad na kritickou infrastrukturu
- **Colonial Pipeline (2021, USA):** ransomware útok (DarkSide) zastavil dodávky pohonných hmot pro východní pobřeží USA na 6 dní. Výkupné $4,4 mil.
- **Kyjevská elektrosíť (2016):** BlackEnergy malware (ruský APT) způsobil výpadek elektřiny pro 230 000 domácností.
- **WannaCry (2017):** ransomware napadl NHS (britské zdravotnictví), přes 300 000 počítačů v 150 zemích, ~$4 mld. škody.
- **Notpetya (2017):** nejdražší kybernetický útok v historii (~$10 mld.), původně cílen na Ukrajinu.

### Kybernetická bezpečnost jako součást národní bezpečnosti
- Kybernetický prostor je **5. válečná doména** (vedle pevniny, moře, vzduchu, vesmíru).
- NATO Kybernetická obrana: čl. 5 může být aplikován na kybernetické útoky.
- **NÚKIB (ČR):** vydává varování, koordinuje odezvu na incidenty, metodická podpora.
- **ENISA (EU):** Agentura EU pro kybernetickou bezpečnost.
- **CISA (USA):** Cybersecurity and Infrastructure Security Agency.

### Nedostatek odborníků
- Globální deficit ~3,5 milionu odborníků na kybernetickou bezpečnost (ISC² 2023).
- Kybernetická bezpečnost je jednou z nejperspektivnějších IT kariér – vysoká poptávka, nedostatek nabídky.

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(2 min)** Typy kybernetických trestných činů – počítačem asistované vs. zaměřené na počítač; RaaS
2. **(2 min)** Prevence – technická (zálohy 3-2-1, MFA, EDR) + organizační (školení, politiky)
3. **(3 min)** Česká legislativa – ZKB (zákon 205/2025), TZ §230-232, NÚKIB
4. **(4 min)** NIS2 – co je, rozšíření subjektů, 2 kategorie, sankce, hlášení incidentů, supply chain
5. **(2 min)** ISO 27001/27002/27005 – co každá norma řeší, ISMS, Annex A
6. **(2 min)** Ekonomické dopady – čísla, Colonial Pipeline, WannaCry; kybernetický prostor jako 5. válečná doména
