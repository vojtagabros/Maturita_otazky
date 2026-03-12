# 14. Metody a prostředky zajištění bezpečnosti HW a SW komponent

> Souvisí s: [[07_Zabezpeceni_siti]] | [[15_Kyberneticka_kriminalita]] | [[16_Rizeni_rizik]] | [[17_Kyberneticke_utoky]] | [[08_Cloud_computing]]

---

## a) Základní principy ochrany, typy kybernetických hrozeb

### Bezpečnostní triáda – CIA
- **Confidentiality (Důvěrnost):** informace jsou dostupné pouze oprávněným osobám. Šifrování, přístupová práva.
- **Integrity (Integrita):** data nejsou neoprávněně změněna. Hashe (SHA-256), digitální podpisy, verzování.
- **Availability (Dostupnost):** systémy jsou dostupné, kdy jsou potřeba. Redundance, zálohování, anti-DoS.

Rozšíření: **Non-repudiation (Nepopiratelnost):** odesílatel nemůže popřít odeslání zprávy (digitální podpis).

### Principy bezpečného návrhu
- **Defense in Depth:** vícevrstvá obrana – perimetr, síť, aplikace, data, uživatel.
- **Least Privilege:** každý subjekt má pouze minimálně nutná oprávnění.
- **Need-to-know:** přístup k informacím jen těm, kdo je pro svou práci potřebují.
- **Zero Trust:** žádná důvěra na základě lokace – vždy ověřovat identitu a autorizaci.
- **Fail Secure / Fail Safe:** při selhání systém přechází do bezpečného stavu (ne do otevřeného).
- **Security by Design:** bezpečnost zabudována od počátku vývoje (SDLC), ne přidána ex-post.
- **Privacy by Design:** ochrana soukromí zabudována do systémů (GDPR požadavek).

### Typy kybernetických hrozeb
- **Malware:** škodlivý software – viry, červi, trojské koně, ransomware, spyware, adware, rootkity.
- **Phishing / Sociální inženýrství:** klamání uživatelů k prozrazení citlivých informací.
- **APT (Advanced Persistent Threat):** sofistikované, dlouhodobé cílené útoky (státní aktéři).
- **Zero-Day exploity:** zneužití dosud neznámých/neopravených zranitelností.
- **Insider Threat:** hrozba od zaměstnanců (úmyslná nebo neúmyslná).
- **DoS/DDoS:** viz [[07_Zabezpeceni_siti]].
- **Supply Chain Attack:** kompromitace dodavatelského řetězce (SolarWinds 2020).
- Viz [[17_Kyberneticke_utoky]] pro detailní typy útoků.

---

## b) Kybernetická bezpečnost

### Definice
**Kybernetická bezpečnost** je soubor opatření, postupů a technologií chránících počítačové systémy, sítě, programy a data před útoky, poškozením nebo neoprávněným přístupem v kybernetickém prostoru.

### Ochrana na úrovni softwaru

**Bezpečný vývoj softwaru (Secure SDLC):**
- **SAST (Static Application Security Testing):** analýza zdrojového kódu bez spuštění (Snyk Code, SonarQube, Checkmarx).
- **DAST (Dynamic Application Security Testing):** testování běžící aplikace (OWASP ZAP, Burp Suite).
- **Penetrační testování (Pentest):** etické hackování – imitace útoku za účelem nalezení zranitelností.
- **Vulnerability scanning:** automatické skenování zranitelností (Nessus, OpenVAS, Qualys).
- **Code review:** manuální nebo automatizovaná kontrola kódu.

**OWASP Top 10** – nejkritičtější zranitelnosti webových aplikací:
1. **Broken Access Control** – neoprávněný přístup k funkcím/datům.
2. **Cryptographic Failures** – slabé šifrování, nešifrovaná citlivá data.
3. **Injection (SQL, NoSQL, LDAP)** – vložení škodlivého kódu do dotazů.
4. **Insecure Design** – chyby v architektuře.
5. **Security Misconfiguration** – výchozí hesla, zbytečně otevřené porty.
6. **Vulnerable Components** – zastaralé knihovny s CVE.
7. **Authentication Failures** – slabá autentizace, chybějící MFA.
8. **Integrity Failures** – deserializace, kompromitace CI/CD pipeline.
9. **Logging Failures** – nedostatečné logování pro detekci incidentů.
10. **SSRF (Server-Side Request Forgery)** – server odesílá požadavky na interní systémy.

**Patch management:**
- Pravidelná aktualizace OS a softwaru – eliminace známých CVE (Common Vulnerabilities and Exposures).
- **CVE/CVSS:** standardizované identifikátory a skóre závažnosti zranitelností (0–10).

**Šifrování:**
- **Symetrické šifrování (AES-256):** stejný klíč pro šifrování i dešifrování. Rychlé. Problém: distribuce klíče.
- **Asymetrické šifrování (RSA, ECC):** veřejný klíč (šifrování) + soukromý klíč (dešifrování). PKI infrastruktura.
- **Hašovací funkce (SHA-256, SHA-3, bcrypt):** jednosměrná transformace – ověření integrity, ukládání hesel.
- **TLS 1.3:** šifrování síťové komunikace – viz [[07_Zabezpeceni_siti]].
- **Šifrování disku:** BitLocker (Windows), FileVault (macOS), LUKS (Linux), VeraCrypt.
- **End-to-end šifrování (E2EE):** Signal, WhatsApp, iMessage.

**Správa hesel a identit:**
- Správce hesel: Bitwarden, 1Password, KeePass – každý účet unique heslo.
- MFA – viz [[08_Cloud_computing]].
- PAM (Privileged Access Management) – viz [[08_Cloud_computing]].

---

## c) Informační bezpečnost

### Definice
**Informační bezpečnost (Information Security, InfoSec)** je širší pojem než kybernetická bezpečnost – zahrnuje ochranu veškerých informací bez ohledu na formu (digitální, papírovou, verbální).

### ISMS – Information Security Management System
Systém řízení bezpečnosti informací dle **ISO/IEC 27001** – viz [[15_Kyberneticka_kriminalita]].

**Klíčové procesy ISMS:**
- **Identifikace aktiv:** co chráníme? (data, systémy, procesy, lidé).
- **Hodnocení rizik:** pravděpodobnost × dopad = riziko. Viz [[16_Rizeni_rizik]].
- **Výběr bezpečnostních opatření:** z Annex A ISO 27001 (93 kontrol v ISO 27002).
- **Implementace opatření.**
- **Monitorování a audit:** kontinuální sledování, interní audity.
- **Neustálé zlepšování:** PDCA cyklus.

### Klasifikace informací
Systém označování citlivosti informací:
- **Veřejné (Public):** bez omezení sdílení.
- **Interní (Internal):** jen pro zaměstnance.
- **Důvěrné (Confidential):** omezený okruh osob.
- **Přísně tajné (Secret/Top Secret):** kritické informace, státní tajemství.
- Klasifikace určuje, jak s informacemi zacházet (ukládání, přenos, likvidace).

### DLP – Data Loss Prevention
- Technologie a procesy zabraňující neoprávněnému úniku dat.
- Monitorování e-mailů, USB přenosů, cloudových nahrávání.
- Příklady: Microsoft Purview DLP, Symantec DLP.

### Bezpečnostní politiky a směrnice
- **Bezpečnostní politika:** vysokoúrovňový dokument definující přístup organizace k bezpečnosti.
- **Acceptable Use Policy (AUP):** pravidla pro používání IT prostředků zaměstnanci.
- **Incident Response Plan:** postup při bezpečnostním incidentu (detekce → izolace → eradikace → obnova → post-mortem).
- **BCP/DRP (Business Continuity Plan / Disaster Recovery Plan):** plán pro obnovu po havárii.

---

## d) Fyzická bezpečnost

### Proč fyzická bezpečnost v IT?
I nejlépe zabezpečený software je bezcenný, pokud útočník může fyzicky přistoupit k serveru, odcizit laptop nebo zničit zálohy. **Fyzická bezpečnost je základ** – bez ní selhávají všechna ostatní opatření.

### Fyzická ochrana datových center
- **Perimetrická ochrana:** ploty, strážní věže, bezpečnostní kamery (CCTV), osvětlení.
- **Přístupové systémy:**
  - **Karty/čipy (RFID/NFC):** přístupové karty, čipové klíče.
  - **Biometrie:** otisk prstu, sken obličeje, skenování sítnice.
  - **PIN kódy:** v kombinaci s kartou (2-faktorový fyzický přístup).
  - **Mantrap (vzduchová propust):** dvoje dveře – první se musí zavřít, než se otevřou druhé.
  - **Bezpečnostní záznamy (audit trail):** kdo vstoupil, kdy a kam.
- **Fyzická segmentace:** oddělené místnosti pro různé úrovně citlivosti (server room, data center tier).
- **Tier klasifikace datových center (Uptime Institute):**
  - **Tier I:** 99,671 % dostupnost, žádná redundance.
  - **Tier II:** 99,741 %, základní redundance.
  - **Tier III:** 99,982 %, N+1 redundance, souběžná údržba.
  - **Tier IV:** 99,995 %, plná fault tolerance.

### Ochrana hardware
- **Kabelové zámky (Kensington Lock):** laptopy, monitory.
- **Trezory a uzamykatelné skříně (server racks):** fyzické zabezpečení serveru.
- **Asset tagging:** sledování majetku (RFID, čárové kódy).
- **TPM (Trusted Platform Module):** bezpečnostní čip na základní desce – ukládá šifrovací klíče (BitLocker), ověřuje integritu OS (Secure Boot).
- **Secure Boot (UEFI):** ověřuje digitální podpis bootloaderu – prevence bootkitů.
- **Tamper-evident/resistant hardware:** fyzická ochrana před neoprávněným otevřením (HSM – Hardware Security Module).

### Ochrana před fyzickými hrozbami prostředí
- **Halon/FM-200/NOVEC 1230:** plynové hasicí systémy pro server rooms (nezničí hardware vodou).
- **Záložní napájení:**
  - **UPS (Uninterruptible Power Supply):** okamžitá záloha při výpadku proudu (minuty).
  - **Agregáty (Diesel generators):** dlouhodobé záložní napájení (hodiny/dny).
  - **Redundantní napájení:** dvě nezávislé napájecí linky z různých rozvoden.
- **Klimatizace a chlazení:** udržení optimální teploty (18–27 °C), vlhkosti (40–60 %).
- **Záplava:** sensory úniku vody, vyvýšené podlahy (raised floor), geograficky bezpečná lokalita.

### Fyzická bezpečnost uživatelů a zařízení
- **Čisté stoly (Clean Desk Policy):** dokumenty a hesla neleží volně na stole.
- **Uzamykání obrazovky:** automatické uzamčení po nečinnosti.
- **Zákaz BYOD nebo BYOD politika:** řízení soukromých zařízení v podnikové síti.
- **Šifrování disků:** ochrana dat i při fyzické krádeži zařízení (BitLocker, FileVault).
- **Vzdálené smazání (Remote Wipe):** ztracený/odcizený laptop/telefon lze na dálku vymazat (MDM – Mobile Device Management).
- **Kamerový systém (CCTV):** monitorování prostor, detekce pohybu.

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(2 min)** CIA triáda + základní principy (Defense in Depth, Least Privilege, Zero Trust)
2. **(3 min)** Kybernetická bezpečnost – SDLC, OWASP Top 10, šifrování (AES/RSA/TLS), patch management
3. **(3 min)** Informační bezpečnost – ISMS, klasifikace dat, DLP, incident response, BCP/DRP
4. **(4 min)** Fyzická bezpečnost – datacenter tiers, přístupové systémy (mantrap, biometrie), TPM/Secure Boot
5. **(3 min)** Fyzické hrozby prostředí – UPS, agregáty, chlazení, hasicí systémy; Clean Desk, Remote Wipe
