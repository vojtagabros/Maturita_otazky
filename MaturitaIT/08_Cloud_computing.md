# 8. Cloud computing

> Souvisí s: [[02_Datova_uloziste]] | [[04_Virtualizace]] | [[05_Pocitacove_site]] | [[09_Informacni_systemy]] | [[14_Bezpecnost_HW_SW]]

---

## a) Hlavní charakteristiky, právní normy

### Definice
**Cloud computing** je model poskytování IT zdrojů (výpočetní výkon, úložiště, aplikace) přes internet na vyžádání, s platbou za skutečné využití (pay-as-you-go). Zdroje jsou spravovány poskytovatelem, uživatel se nestará o fyzický hardware.

### 5 základních charakteristik (NIST definice)
1. **On-demand self-service:** zdroje lze zřídit okamžitě bez interakce s poskytovatelem.
2. **Broad network access:** přístup přes standardní síťová rozhraní (internet, API) z jakéhokoliv zařízení.
3. **Resource pooling:** zdroje sdíleny mezi více zákazníky (multi-tenancy), dynamicky přiděleny.
4. **Rapid elasticity:** rychlé škálování (nahoru i dolů) podle aktuální potřeby.
5. **Measured service:** využití je měřeno a účtováno (transparentní billing).

### Modely nasazení
- **Veřejný cloud (Public Cloud):** infrastruktura sdílena, vlastněna a provozována poskytovatelem. AWS, Azure, Google Cloud (GCP). Nejekonomičtější.
- **Soukromý cloud (Private Cloud):** dedikovaná infrastruktura pro jednu organizaci (on-premises nebo u poskytovatele). Větší kontrola, vyšší náklady. VMware vSphere, OpenStack, Nutanix.
- **Hybridní cloud (Hybrid Cloud):** kombinace veřejného a soukromého cloudu s orchestrací mezi nimi. Citlivá data on-premises, burst workloady ve veřejném cloudu.
- **Multi-cloud:** využití více veřejných cloudových poskytovatelů současně – snižuje závislost (vendor lock-in).
- **Community Cloud:** sdílená infrastruktura pro specifickou komunitu organizací (vládní cloud, akademická sféra).

### Servisní modely

| Model | Co poskytuje | Zákazník spravuje | Příklady |
|---|---|---|---|
| **IaaS** (Infrastructure as a Service) | Virtuální stroje, úložiště, sítě | OS, middleware, aplikace | AWS EC2, Azure VM, GCP Compute Engine |
| **PaaS** (Platform as a Service) | OS + middleware + runtime | Aplikace, data | Heroku, Azure App Service, Google App Engine |
| **SaaS** (Software as a Service) | Kompletní aplikace | Pouze nastavení | Gmail, Microsoft 365, Salesforce, Dropbox |
| **FaaS/Serverless** | Spuštění funkcí na event | Pouze kód funkcí | AWS Lambda, Azure Functions |

### Právní normy

**Zákon o kybernetické bezpečnosti (ZKB) – zákon č. 181/2014 Sb. + zákon č. 205/2025 Sb.:**
- Povinnosti pro provozovatele kritické infrastruktury a ISVS (Informační systémy veřejné správy).
- Vyhláška č. 82/2018 Sb. (nová vyhláška KB) – bezpečnostní opatření.

**Zákon 190/2023 Sb.:**
- Zákon o cloud computingu pro veřejnou správu ČR.
- Zavádí **katalog cloud computingu** – certifikace cloudových služeb pro státní správu.
- Definuje požadavky na bezpečnost, suverenitu dat, dostupnost.

**GDPR (Nařízení EU 2016/679):**
- Osobní data EU občanů nesmí být přenášena do zemí bez odpovídající ochrany (mimo EU/EEA) bez zvláštních opatření (SCC – Standard Contractual Clauses).
- Zpracovatel dat (cloud provider) musí mít uzavřenu **DPA (Data Processing Agreement)**.
- Právo na výmaz, přenositelnost dat.

**NIS2 Směrnice (viz [[15_Kyberneticka_kriminalita]]):** bezpečnostní požadavky pro cloud providers v kritické infrastruktuře.

---

## b) Identity management v cloudu, GDPR, autentizace

### IAM – Identity and Access Management
**IDM (Identity Management)** je soubor procesů a technologií pro správu digitálních identit v organizaci.

**Komponenty IAM:**
- **Autentizace (Authentication – AuthN):** ověření identity – „Kdo jsi?" (heslo, MFA, certifikát).
- **Autorizace (Authorization – AuthZ):** ověření oprávnění – „Co smíš dělat?" (role, permissions).
- **Provisioning/Deprovisioning:** vytváření a rušení účtů (životní cyklus identity).
- **SSO (Single Sign-On):** jedno přihlášení pro přístup k více systémům (SAML 2.0, OAuth 2.0, OpenID Connect).
- **Directory Services:** centrální databáze identit – Microsoft Active Directory, Azure AD (Entra ID), LDAP.

**Životní cyklus identity:**
1. **Vznik:** nový zaměstnanec → vytvoření účtu, přiřazení rolí.
2. **Provoz:** správa přístupů, revize oprávnění (Access Review).
3. **Změna:** změna pracovní pozice → aktualizace rolí (Joiner/Mover/Leaver).
4. **Zánik:** odchod zaměstnance → okamžité zrušení všech přístupů.

**Aplikační role a pravidla řízení identit:**
- **RBAC (Role-Based Access Control):** přístup podle přiřazených rolí (Admin, User, ReadOnly).
- **ABAC (Attribute-Based Access Control):** podmínky na základě atributů (oddělení, lokalita, čas).
- **PAM (Privileged Access Management):** správa privilegovaných účtů (administrátoři) – CyberArk, BeyondTrust.

**GDPR a IDM v cloudu:**
- Osobní data (jméno, e-mail, IP adresa) = osobní údaje pod GDPR.
- Cloud provider = zpracovatel; zákazník = správce (controller).
- Minimalizace dat: jen nezbytné informace v identitách.
- Logování přístupů k osobním datům (audit trail).

---

## c) Vícefaktorová autentizace (MFA)

### Faktory autentizace
1. **Znalostní faktor (Something you know):** heslo, PIN, bezpečnostní otázka.
2. **Vlastnostnické faktor (Something you have):** fyzický klíč, čipová karta, smartphone (OTP), hardware token (YubiKey).
3. **Biometrický faktor (Something you are):** otisk prstu, sken obličeje, duhovka, hlas.
4. **Lokační faktor (Somewhere you are):** IP adresa, GPS poloha.
5. **Časový faktor (Something you do):** typický vzor chování.

**MFA (Multi-Factor Authentication):** kombinace 2+ různých faktorů.
**2FA (Two-Factor Authentication):** nejběžnější forma MFA.

### Metody MFA
- **TOTP (Time-based One-Time Password):** 6místný kód generovaný každých 30 sekund. Apps: Google Authenticator, Microsoft Authenticator, Authy. Standard RFC 6238.
- **Push notifikace:** schválení přihlášení v mobilní appce (Duo Security, Microsoft Authenticator).
- **SMS/Email OTP:** jednorázový kód zaslaný zprávou – **méně bezpečné** (SIM swapping, phishing).
- **Hardware token:** YubiKey (FIDO2/WebAuthn), RSA SecurID.
- **Passkeys (FIDO2):** kryptografické klíče vázané na zařízení – náhrada hesel, phishing-resistant. Podporováno: Apple, Google, Microsoft.

### MFA u cloudových poskytovatelů

**Microsoft Azure / Microsoft 365:**
- **Entra ID (Azure AD) MFA:** TOTP, Microsoft Authenticator (push), FIDO2, Windows Hello.
- **Conditional Access Policies:** MFA požadováno jen v rizikových situacích (cizí lokace, nové zařízení).
- **Entra ID Protection:** detekce rizikových přihlášení pomocí AI.

**Google (Google Workspace / GCP):**
- **Google 2-Step Verification:** Google Authenticator, push, SMS, hardware keys.
- **Google Advanced Protection Program:** pro vysoce rizikové účty – pouze fyzické FIDO2 klíče.
- **Context-Aware Access:** přístup podmíněn stavem zařízení (BeyondCorp model = Zero Trust).

---

## d) Virtualizace v cloud computingu

Cloud computing je z velké části postaven na virtualizaci – viz [[04_Virtualizace]].

### Jak virtualizace pohání cloud
- IaaS = virtuální stroje (hypervisor – KVM, VMware ESXi, Hyper-V) na fyzickém hardware poskytovatele.
- Zákazník dostane VM s garantovanými zdroji (vCPU, RAM, disk) bez přístupu k fyzickému serveru.

### Kontejnery v cloudu
- **Docker + Kubernetes (K8s):** standard pro PaaS a moderní aplikace.
- **AWS EKS, Azure AKS, Google GKE:** managed Kubernetes – poskytovatel spravuje K8s cluster.
- **Serverless/FaaS:** ještě vyšší abstrakce – kód spuštěn v kontejneru na vyžádání, fakturace za ms.

### Klíčové cloudové koncepty
- **Auto-scaling:** automatické přidávání/odebírání VM/kontejnerů podle zatížení.
- **Load balancing:** distribuce provozu mezi více instancí.
- **CDN (Content Delivery Network):** doručování obsahu z geograficky blízkých serverů (Cloudflare, AWS CloudFront).
- **High Availability (HA):** replikace přes více AZ (Availability Zones) nebo regionů.
- **Disaster Recovery (DR):** záloha do jiného regionu, RTO a RPO metriky.

### Hlavní cloudoví poskytovatelé
- **AWS (Amazon Web Services):** největší trh, 200+ služeb, největší ekosystém. EC2, S3, RDS, Lambda.
- **Microsoft Azure:** 2. místo, silná integrace s Microsoft produkty (M365, AD), hybridní cloud (Azure Arc).
- **Google Cloud Platform (GCP):** síla v datech a AI/ML (BigQuery, Vertex AI, TensorFlow).
- **Menší:** Oracle Cloud, IBM Cloud, Alibaba Cloud, DigitalOcean.

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(2 min)** Definice cloud computingu – 5 charakteristik NIST, servisní modely IaaS/PaaS/SaaS
2. **(2 min)** Modely nasazení – veřejný, soukromý, hybridní; právní normy (ZKB, zákon 190/2023, GDPR)
3. **(3 min)** IAM – autentizace vs. autorizace, SSO, životní cyklus identity, RBAC, PAM
4. **(3 min)** MFA – faktory, TOTP, FIDO2/Passkeys, implementace u Microsoft a Google
5. **(3 min)** Virtualizace v cloudu – VM a kontejnery jako základ cloudu, Kubernetes, serverless
6. **(2 min)** Cloudoví poskytovatelé – AWS, Azure, GCP; auto-scaling, HA, CDN
