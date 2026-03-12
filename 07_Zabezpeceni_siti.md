# 7. Zabezpečení počítačových sítí a diagnostika problémů

> Souvisí s: [[05_Pocitacove_site]] | [[06_Sitova_zarizeni]] | [[14_Bezpecnost_HW_SW]] | [[15_Kyberneticka_kriminalita]] | [[16_Rizeni_rizik]]

---

## a) Význam ochrany počítačových sítí a základní principy

### Proč chránit sítě?
Počítačové sítě jsou páteří moderní digitální společnosti – útoky na sítě mohou způsobit:
- Finanční ztráty (výpadky služeb, krádež dat, ransomware).
- Únik citlivých dat (osobní údaje, obchodní tajemství).
- Narušení kritické infrastruktury (nemocnice, energetika, bankovnictví).
- Reputační škody.

### Základní principy bezpečnosti (CIA triáda)
- **Confidentiality (Důvěrnost):** data jsou přístupná pouze oprávněným osobám (šifrování, přístupová práva).
- **Integrity (Integrita):** data nejsou neoprávněně modifikována (hashe, digitální podpisy).
- **Availability (Dostupnost):** systémy jsou dostupné oprávněným uživatelům, kdy je potřebují (redundance, ochrana proti DoS).

Rozšíření: **AAA model** – Authentication (Autentizace), Authorization (Autorizace), Accounting (Auditování).

### Principy ochrany sítě
- **Defense in Depth (vícevrstvá obrana):** více bezpečnostních vrstev – jedna vrstva nestačí.
- **Princip minimálních oprávnění (Least Privilege):** každý uživatel/systém má jen nutná práva.
- **Segmentace sítě:** rozdělení sítě na zóny (VLAN, DMZ) – omezení šíření útoku.
- **Zero Trust:** „never trust, always verify" – každý přístup je ověřen, i z interní sítě.
- **Patch management:** pravidelné aktualizace OS a software eliminují známé zranitelnosti.

---

## b) Nejčastější hrozby v síti

### MITM – Man-in-the-Middle útok
- Útočník se **vloží mezi dvě komunikující strany**, aniž to vědí.
- Zachycuje a může modifikovat veškerou komunikaci.
- Techniky:
  - **ARP Spoofing/Poisoning:** falešné ARP odpovědi → provoz přesměrován přes útočníka (LAN).
  - **DNS Spoofing:** falešné DNS odpovědi → uživatel přesměrován na podvodnou stránku.
  - **SSL Stripping:** downgrade HTTPS na HTTP.
- Ochrana: HTTPS, HSTS, DNSSEC, SSH místo Telnetu, VPN.

### DoS / DDoS (Denial of Service / Distributed DoS)
- **DoS:** zahlcení cíle požadavky/pakety → nedostupnost pro legitimní uživatele.
- **DDoS:** útok z tisíců/milionů kompromitovaných zařízení (botnet) simultánně.
- Typy:
  - **Volumetrické útoky:** zahlcení bandwidth (UDP flood, ICMP flood) – terabity za sekundu.
  - **Protokolové útoky:** exploitace slabostí protokolů (SYN flood – vyčerpání TCP tabulky).
  - **Aplikační útoky (L7):** HTTP flood, Slowloris – zahlcení webserveru.
- Ochrana: Anti-DDoS služby (Cloudflare, Akamai), rate limiting, blackholing, scrubbing centers.

### Spoofing
- Falšování identity (IP, MAC, e-mail, caller ID).
- **IP Spoofing:** falešná zdrojová IP → ztížení sledování útočníka, DRDoS (zesilovací DDoS).
- **MAC Spoofing:** falešná MAC adresa → obejití MAC filtrování.
- **E-mail Spoofing:** falešná odesílatelská adresa → phishing (viz [[17_Kyberneticke_utoky]]).
- Ochrana: SPF, DKIM, DMARC (e-mail), port security na switchi (MAC).

### Phishing
- Sociální inženýrství + falešná identita → podvod k získání přihlašovacích údajů, platebních dat.
- Varianty: spear phishing (cílený), whaling (na management), smishing (SMS), vishing (telefon).
- Viz [[17_Kyberneticke_utoky]] pro detail.

### Další hrozby
- **Port scanning:** zjišťování otevřených portů (Nmap) – recon fáze útoku.
- **Packet sniffing:** zachytávání nešifrované komunikace (Wireshark) na sdíleném médiu.
- **Rogue AP:** falešný Wi-Fi Access Point lákající uživatele (Evil Twin útok).

---

## c) Ochrana sítě

### Firewall
- Filtruje síťový provoz na základě **pravidel (ACL – Access Control List)**.
- **Paketový filtr (Stateless):** zkoumá jednotlivé pakety (IP, port, protokol) bez kontextu. Rychlý, ale omezený.
- **Stavový firewall (Stateful):** sleduje stav TCP spojení, rozumí konverzaci. Standard.
- **Aplikační firewall (L7/NGFW – Next Generation Firewall):** DPI (Deep Packet Inspection), identifikace aplikací, uživatelů, URL filtrování. Příklady: Palo Alto, Fortinet, Cisco Firepower.
- **WAF (Web Application Firewall):** ochrana webových aplikací (SQL injection, XSS) – Cloudflare, AWS WAF.
- **Umístění:** perimetr sítě (mezi LAN a WAN), inter-VLAN, hostitelský firewall (Windows Defender Firewall, iptables).

### Antivirový software
- Detekce a eliminace malware.
- Metody detekce: **signaturová** (databáze známého malware), **heuristická** (analýza chování), **sandboxing** (spouštění v izolovaném prostředí).
- Dnes: **EDR (Endpoint Detection and Response)** – pokročilá ochrana koncových stanic (CrowdStrike Falcon, Microsoft Defender ATP).

### IDS / IPS
- **IDS (Intrusion Detection System):** monitoruje síťový provoz, **detekuje** anomálie a útoky, ale **nezasahuje** – pouze alarmuje.
- **IPS (Intrusion Prevention System):** detekuje **a aktivně blokuje** podezřelý provoz v reálném čase.
- Typy: Network-based (NIDS/NIPS) – pasivní tap na síti; Host-based (HIDS/HIPS) – na koncové stanici.
- Příklady: Snort (open-source), Suricata, Zeek.

### VPN (Virtual Private Network)
- Vytvoří **šifrovaný tunel** přes veřejnou síť – bezpečná komunikace jako v privátní síti.
- Protokoly:
  - **IPsec:** standard pro site-to-site VPN, silné šifrování (AES), autentizace (IKEv2).
  - **OpenVPN:** open-source, TLS, flexibilní, multiplatformní.
  - **WireGuard:** moderní, rychlý, jednoduchý kód, nízká latence – dnes preferovaný.
  - **SSL VPN / TLS VPN:** přes prohlížeč nebo klienta (port 443 – prochází většinou firewallů).
- **Site-to-site VPN:** propojení dvou sítí (pobočky firmy).
- **Remote Access VPN:** vzdálené připojení zaměstnanců k firemní síti.

### Šifrování komunikace
- **TLS (Transport Layer Security):** šifrování aplikačních protokolů (HTTPS = HTTP + TLS, SMTPS, IMAPS). Verze: TLS 1.2 (akceptovatelné), TLS 1.3 (aktuální standard).
- **End-to-end šifrování (E2E):** zprávy šifrované od odesílatele k příjemci, ani server provozovatele je nevidí (Signal, WhatsApp, iMessage).
- **Certifikáty (PKI):** ověření identity serveru přes certifikáty vydané CA (Certificate Authority). Let's Encrypt – zdarma.

### Segmentace a DMZ
- **DMZ (Demilitarized Zone):** izolovaná síťová zóna pro servery přístupné z internetu (webserver, mailserver) – oddělena od interní LAN firewallema.
- **VLAN segmentace:** oddělení provozu různých oddělení (IT, HR, Finance) na jedné fyzické infrastruktuře.
- **Microsegmentace:** jemnozrnné politiky i uvnitř datového centra (Zero Trust).

---

## d) Diagnostické nástroje a příkazy

### ping
```
ping 8.8.8.8          # Test dostupnosti hostitele
ping -c 4 google.com  # Linux: 4 pakety
ping -t google.com    # Windows: nepřetržitě
```
- Odesílá **ICMP Echo Request** a čeká na **ICMP Echo Reply**.
- Zobrazuje: odezvu (RTT v ms), ztrátu paketů (%), TTL.
- Diagnostika: dostupnost hostitele, síťová konektivita, DNS rozlišení.

### tracert / traceroute
```
tracert google.com      # Windows
traceroute google.com   # Linux
```
- Zobrazuje **cestu paketů sítí** (každý hop = router).
- Využívá TTL (Time to Live) – postupně inkrementuje TTL, každý router sníží TTL o 1, při TTL=0 odešle ICMP Time Exceeded.
- Diagnostika: kde dochází ke zpomalení nebo výpadku, routing loops.

### netstat
```
netstat -an     # Všechna aktivní spojení a otevřené porty
netstat -r      # Směrovací tabulka
netstat -s      # Statistiky protokolů
ss -tulnp       # Moderní alternativa na Linuxu
```
- Zobrazuje aktivní TCP/UDP spojení, naslouchající porty, statistiky.
- Diagnostika: jaké procesy naslouchají na kterých portech, aktivní spojení.

### nslookup / dig
```
nslookup google.com     # DNS dotaz
dig google.com A        # Detailní DNS dotaz (Linux)
```
- Diagnostika DNS – zjišťuje IP adresu pro doménu, ověřuje DNS záznamy.

### ipconfig / ip / ifconfig
```
ipconfig /all       # Windows – síťová konfigurace
ipconfig /flushdns  # Vyčistit DNS cache
ip addr show        # Linux – IP adresy
ip route show       # Linux – směrovací tabulka
```

### Wireshark
- GUI packet analyzer – zachycuje a analyzuje síťový provoz.
- Diagnostika: analýza protokolů, odhalení nešifrované komunikace, troubleshooting.

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(2 min)** CIA triáda – důvěrnost, integrita, dostupnost; proč chránit sítě
2. **(3 min)** Hrozby – MITM (ARP spoofing), DoS/DDoS (volumetrické/SYN flood), spoofing, phishing
3. **(2 min)** Firewall – paketový filtr, stavový, NGFW, WAF; umístění
4. **(3 min)** IDS/IPS, VPN (WireGuard/IPsec/OpenVPN), TLS šifrování
5. **(3 min)** Segmentace – DMZ, VLAN, Zero Trust; antivirový SW a EDR
6. **(2 min)** Diagnostika – ping, tracert, netstat; co diagnostikují
