# 17. Charakteristika vybraných kybernetických útoků a jejich dopadů

> Souvisí s: [[14_Bezpecnost_HW_SW]] | [[15_Kyberneticka_kriminalita]] | [[16_Rizeni_rizik]] | [[07_Zabezpeceni_siti]]

---

## a) Phishing, Ransomware, Malware

### Malware (Malicious Software)
Zastřešující termín pro veškerý škodlivý software. Kategorie:

**Virus:**
- Připojuje se k legitimnímu souboru/programu, šíří se jeho spuštěním.
- Potřebuje aktivní akci uživatele (spuštění infikovaného souboru).
- Příklady: historické viry na DOS (Elk Cloner, 1982 – první PC virus).

**Červ (Worm):**
- Šíří se **samostatně** přes síť bez zásahu uživatele – exploituje zranitelnosti.
- Může napadnout tisíce/miliony systémů rychle.
- Příklady: **WannaCry (2017)** – exploitoval EternalBlue (NSA exploit, SMB protokol). **Stuxnet (2010)** – sofistikovaný červ (USA/Izrael) zaměřený na íránské centrifugy.

**Trojský kůň (Trojan):**
- Maskuje se za legitimní software, ale obsahuje škodlivou část.
- Nevytváří kopie sebe sama (nevirový), ale otevírá „zadní vrátka" (backdoor).
- Příklady: **RAT (Remote Access Trojan)** – útočník ovládá počítač vzdáleně.

**Rootkit:**
- Skrývá přítomnost malwaru nebo útočníka na systému – modifikuje OS.
- Velmi obtížně detekovatelný (někdy nutná reinstalace OS nebo čistý obraz).
- Bootkity – rootkit v MBR/UEFI.

**Spyware:**
- Tajně sbírá informace – klávesy (keylogger), screenshoty, přihlašovací údaje, přístupy k webkameře.
- Příklady: **Pegasus** (NSO Group) – komerční spyware pro vlády.

**Adware:**
- Zobrazuje nevyžádanou reklamu, může sbírat browsing data.

**Botnet:**
- Síť kompromitovaných zařízení (bots/zombies) ovládaných útočníkem přes C2 (Command & Control) server.
- Použití: DDoS útoky, spam kampaně, kryptoměna mining, ransomware distribuce.
- Příklady: **Mirai** (2016) – IoT botnet způsobil masivní DDoS na Dyn DNS (výpadek Twitteru, Netflixu).

---

### Ransomware
- Zašifruje soubory oběti a požaduje **výkupné (ransom)** za dešifrovací klíč.
- Platba typicky v kryptoměnách (Bitcoin, Monero) kvůli anonymitě.
- **Průměrné výkupné (2023):** přes 1 milion USD.

**Typy ransomwaru:**
- **Locker Ransomware:** zamkne přístup k OS/zařízení (nezašifruje data).
- **Crypto Ransomware:** zašifruje soubory pomocí AES-256 + RSA-2048.
- **Double Extortion (dvojité vydírání):** nejen šifrování, ale i krádež dat + hrozba zveřejnění.
- **Triple Extortion:** + DDoS útok + kontaktování zákazníků oběti.
- **RaaS (Ransomware-as-a-Service):** zločinecká skupina poskytuje nástroje affiliátům za podíl z výkupného.

**Životní cyklus ransomware útoku:**
1. **Initial Access:** phishing e-mail, exploitace zranitelnosti (VPN, RDP), kompromitovaný dodavatel.
2. **Persistence:** malware se zakotví v systému (registry, scheduled tasks).
3. **Privilege Escalation:** získání admin/SYSTEM oprávnění.
4. **Lateral Movement:** šíření po síti, napadení dalších systémů.
5. **Data Exfiltration:** krádež dat před šifrováním (double extortion).
6. **Encryption:** zašifrování souborů, smazání stínových kopií (Shadow Copies).
7. **Ransom Demand:** zobrazení výzvy k zaplacení, kontakt na dark web.

**Ochrana:**
- Zálohy 3-2-1 **offsite a offline** (vzduchová mezera).
- Patch management – WannaCry fungoval měsíc po vydání patche.
- EDR a network segmentace – zpomalení šíření.
- Privileged Access Management.
- **Nikdy neplatit výkupné** – není záruka dešifrování, financuje další útoky.

**Historické případy:**
- **WannaCry (2017):** 300 000+ počítačů, NHS, Boeing, Deutsche Bahn. EternalBlue exploit.
- **Colonial Pipeline (2021):** DarkSide ransomware, 5-denní výpadek dodávek pohonných hmot USA.
- **Kaseya VSA (2021):** supply chain ransomware (REvil) – 1 500 firem najednou.
- **ČSSZ/SZÚ/nemocnice ČR:** české nemocnice napadeny v průběhu 2020–2023.

---

### Phishing
Viz [[07_Zabezpeceni_siti]] pro síťový aspekt. Detailně:

**Typy phishingu:**
- **Mass Phishing:** hromadné e-maily imitující banky, PayPal, Microsoft (low effort, nízká přesnost).
- **Spear Phishing:** cílený útok na konkrétní osobu/organizaci (high effort, vysoká úspěšnost). Útočník sbírá info z LinkedIn, sociálních sítí – **OSINT (Open Source Intelligence)**.
- **Whaling:** spear phishing zaměřený na vrcholový management (CEO, CFO).
- **Business Email Compromise (BEC):** kompromitace firemního e-mailu → podvodné příkazy k platbě.
- **Smishing:** phishing přes SMS zprávy.
- **Vishing:** phishing přes telefonní hovor.
- **Quishing:** phishing přes QR kódy (přesměrování na podvodný web).

**Techniky:**
- Doménovédomain spoofing: `paypa1.com`, `microsoft-support.xyz`.
- **Typosquatting:** registrace domén s překlepy.
- **Look-alike domains:** `rn` vypadá jako `m` (netsecurity.com vs. netsecunty.com).
- HTTPS phishing: i podvodné weby mají dnes SSL certifikát (falešná záruka bezpečnosti).

**Ochrana:**
- E-mailové autentizační protokoly: **SPF, DKIM, DMARC**.
- Security awareness training, phishing simulace.
- Anti-phishing filtry (Microsoft Defender for Office 365, Proofpoint).
- MFA – i získané heslo nestačí útočníkovi.
- **FIDO2/Passkeys** – phishing-resistant autentizace.

---

## b) Kybernetické útoky založené na AI

AI přináší nové možnosti pro útočníky (lowering barriers) i obránce.

### AI pro útočníky

**AI-generovaný phishing (AI-enhanced SE):**
- LLM (ChatGPT, Claude, místní modely) generují přesvědčivé phishing e-maily bez gramatických chyb.
- **Deepfake voice/video:** imitace hlasu nebo videa vedoucích pracovníků pro BEC útoky.
  - Případ: CFO hongkongské firmy okraden o $25 mil. po deepfake video konferenci (2024).
- Personalizace útoku na základě OSINT dat zpracovaných AI.

**AI-asistovaný vývoj malwaru:**
- LLM mohou generovat kód, který útočníci upravují pro malware (FraudGPT, WormGPT – dark web LLM).
- Automatické vyhledávání zranitelností (fuzzing s AI).
- Polymorfní malware generovaný AI – mění svůj kód, aby obešel signatury.

**AI-driven útoky:**
- Automatizované testování přihlašovacích údajů (credential stuffing) s AI prioritizací.
- AI analýza ukradených dat (e-mailů, dokumentů) pro cílené exploitation.
- **Adversarial AI:** útoky na ML modely – poisoning (trénování na škodlivých datech), evasion (obejití AI detektoru).

### AI pro obránce

**AI v kybernetické bezpečnosti:**
- **Anomaly Detection:** ML detekuje odchylky od normálního chování uživatelů/systémů (UEBA – User Entity Behavior Analytics).
- **Threat Intelligence:** AI zpracovává obrovské množství threat feeds a identifikuje IoC (Indicators of Compromise).
- **Automatická odpověď (SOAR + AI):** automatická izolace infikovaného zařízení při detekci.
- **AI-powered SIEM:** Microsoft Sentinel, Splunk Enterprise Security – AI korelace событий.
- **LLM pro Security Analysts:** Microsoft Copilot for Security, Google Security AI Workbench – asistenti pro analytiky SOC.

---

## c) Sociální sítě a kybernetické útoky

### Hrozby spojené se sociálními sítěmi

**OSINT (Open Source Intelligence):**
- Útočníci sbírají veřejně dostupné informace z LinkedIn, Facebooku, Instagramu, GitHub.
- Informace: pracovní pozice, kolegové, technologie ve firmě, dovolené → targetovaný phishing.
- **Doxxing:** zveřejnění soukromých informací o osobě online s cílem způsobit újmu.

**Sociální inženýrství přes sítě:**
- Falešné profily (fake accounts) pro budování důvěry → extrakce informací.
- **Romance scams:** dlouhodobá budování falešného vztahu → finanční podvod.
- **Pig Butchering scam:** falešné investiční příležitosti (kryptoměny) přes falešné přátele.

**Dezinformace a disinformace:**
- Koordinované kampaně šíření falešných zpráv (state-sponsored, political).
- Deepfake video/audio – politici říkají věci, co nikdy neřekli.
- **Astroturfing:** koordinovaný dojem organické podpory (boti, farmy komentářů).

**Malware distribuce přes sociální sítě:**
- Škodlivé přílohy/odkazy v DM, podvodné aplikace, malvertising (škodlivá reklama).

**Útoky na přihlašovací údaje:**
- Credential stuffing: přihlašovací údaje z uniklých databází (Have I Been Pwned).
- Account takeover (ATO): přístup k účtu → spam, podvod, krádež identity.

### Ochrana na sociálních sítích
- Minimalizace sdílených informací (OPSEC – Operational Security).
- Silné unique heslo + MFA pro každý účet.
- Opatrnost při přijímání neznámých přátel/followů.
- Soukromé nastavení profilů.

---

## d) Internet věcí (IoT) a kybernetické hrozby

### Co je IoT?
**Internet of Things (Internet věcí)** = síť fyzických zařízení vybavených senzory, softwarem a konektivitou, schopných sbírat a vyměňovat data bez lidské interakce.

**Typy IoT zařízení:**
- **Spotřebitelské:** chytré televize, reproduktory (Amazon Echo, Google Home), termostaty, žárovky, pračky, baby monitory, bezpečnostní kamery, nositelná elektronika.
- **Průmyslové (IIoT):** SCADA systémy, PLC (Programmable Logic Controllers), průmyslové senzory, roboti, smart grid (chytrá energetická síť).
- **Zdravotnické (IoMT):** implantovatelné defibrilátory, inzulínové pumpy, nemocniční monitory.
- **Smart City:** chytré parkování, odpadkové koše, dopravní senzory, pouliční osvětlení.

### Proč je IoT nebezpečné?

1. **Slabá výchozí konfigurace:** výchozí hesla (admin/admin), nešifrovaná komunikace, otevřené služby.
2. **Omezené výpočetní zdroje:** slabý procesor/paměť → nelze spustit plnohodnotný bezpečnostní SW, šifrování.
3. **Dlouhá životnost bez aktualizací:** IoT zařízení nasazena na 10–20 let, výrobci přestanou vydávat patche.
4. **Velká plocha útoku (Attack Surface):** miliardy zařízení, různí výrobci, různé protokoly (MQTT, CoAP, Zigbee, Z-Wave).
5. **Přímý přístup k fyzickému světu:** kompromitovaná průmyslová zařízení mohou způsobit fyzické škody.

### IoT útoky

**Mirai Botnet (2016):**
- Malware skenoval internet pro IoT zařízení s výchozími hesly (Telnet), infikoval je.
- Vytvořil botnet z IP kamer, routerů, NVR rekordérů → masivní DDoS útok (620 Gbit/s).
- Napadl Dyn DNS (major provider) → výpadek Twitteru, Netflixu, Redditu, GitHubu.
- Zdrojový kód byl zveřejněn → desítky variant (Miori, Satori, Okiru).

**Průmyslové útoky (OT/ICS):**
- **Stuxnet (2010):** zničil íránské centrifugy pro obohacování uranu – první kybernetická zbraň způsobující fyzické škody.
- **Triton/TRISIS (2017):** útok na Safety Instrumented Systems (SIS) petrochemické firmy (Saúdská Arábie) – pokus způsobit fyzickou katastrofu.
- **Ukrainian Power Grid (2015, 2016):** BlackEnergy/Industroyer – výpadek elektřiny.

**Zdravotnické IoT:**
- Vzdálené hacknutí implantovatelných defibrilátorů/kardiostimulátorů – demonstroval bezpečnostní výzkumník.
- Johnson & Johnson inzulínová pumpa – zranitelnost pro vzdálené změny dávkování.

### Ochrana IoT
- **Segmentace sítě:** IoT zařízení v izolovaném VLAN/subnet – nelze se z nich dostat do firemní sítě.
- **Změna výchozích hesel** – první krok.
- **Firmwarové aktualizace:** automatické nebo pravidelné ruční aktualizace.
- **Deaktivace nepotřebných služeb** (Telnet, UPnP).
- **IoT bezpečnostní standardy:** ETSI EN 303 645 (spotřebitelské IoT), IEC 62443 (průmyslové).
- **PSA Certified, IoXT:** certifikace bezpečnosti IoT zařízení.
- **Zero Trust pro IoT:** ověřovat i interní IoT zařízení.

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(3 min)** Malware typy – virus vs. červ vs. trojský kůň vs. ransomware; WannaCry, Mirai jako příklady
2. **(3 min)** Ransomware – šifrování, double extortion, RaaS, životní cyklus útoku, Colonial Pipeline; ochrana
3. **(2 min)** Phishing – mass vs. spear vs. whaling; BEC, deepfake; SPF/DKIM/DMARC ochrana
4. **(2 min)** AI útoky – deepfake, AI phishing, polymorfní malware; AI v obraně (UEBA, SOAR)
5. **(2 min)** Sociální sítě – OSINT, doxxing, dezinformace, credential stuffing
6. **(3 min)** IoT hrozby – proč IoT nebezpečné, Mirai botnet, Stuxnet; průmyslové útoky; ochrana (VLAN, segmentace)
