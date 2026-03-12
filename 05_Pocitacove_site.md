# 5. Počítačové sítě

> Souvisí s: [[06_Sitova_zarizeni]] | [[07_Zabezpeceni_siti]] | [[08_Cloud_computing]] | [[03_Operacni_systemy]]

---

## a) Základní terminologie, rozdělení sítí dle rozsahu a přístupu

### Základní pojmy
- **Počítačová síť:** systém vzájemně propojených zařízení (uzlů), která mohou komunikovat a sdílet prostředky.
- **Uzel (node):** jakékoliv zařízení v síti – počítač, server, tiskárna, smartphone, router.
- **Bandwidth (šířka pásma):** maximální přenosová kapacita linky (Mbit/s, Gbit/s).
- **Latence:** zpoždění přenosu dat (ms) – důležité pro real-time aplikace (VoIP, gaming, videokonference).
- **Protokol:** soubor pravidel pro komunikaci mezi zařízeními.
- **Paket:** základní přenosová jednotka dat v síti (záhlaví + data + patička).

### Rozdělení sítí dle rozsahu (geografický)

| Typ | Název | Rozsah | Příklad |
|---|---|---|---|
| **PAN** | Personal Area Network | < 10 m | Bluetooth sluchátka, NFC platba |
| **LAN** | Local Area Network | Budova/kampus | Domácí Wi-Fi, firemní síť |
| **MAN** | Metropolitan Area Network | Město | Městský optický rozvod |
| **WAN** | Wide Area Network | Kontinent/svět | Internet, firemní VPN propojení |
| **GAN** | Global Area Network | Celý svět | Internet (ISP páteřní sítě) |

### Rozdělení dle přístupu
- **Privátní (soukromá) síť:** přístup omezen na oprávněné uživatele (domácí síť, firemní intranet).
- **Veřejná síť:** přístupná bez omezení (internet, veřejné Wi-Fi hotspoty).
- **VPN (Virtual Private Network):** privátní síť tunelovaná přes veřejnou infrastrukturu – viz [[07_Zabezpeceni_siti]].

---

## b) Topologie sítí

Topologie popisuje fyzické nebo logické uspořádání uzlů v síti.

### Fyzická topologie
- **Sběrnicová (Bus):** všechna zařízení připojena na jeden kabel (koaxiál). Kolize, jedno přerušení = výpadek celé sítě. Historická (10BASE2 Ethernet). Výhoda: jednoduchost, nízká cena.
- **Hvězdicová (Star):** každé zařízení připojeno přímo k centrálnímu prvku (switch/hub). Nejrozšířenější topologie dnes. Výhoda: výpadek jednoho uzlu neovlivní ostatní. Nevýhoda: výpadek centrálního prvku.
- **Kruhová (Ring):** data cirkulují jedním směrem po kruhu (token ring). Výhoda: deterministický přístup. Nevýhoda: jedno přerušení = výpadek. Historická (IBM Token Ring).
- **Stromová (Tree):** hierarchická struktura hvězdic – páteřní switch + distribuční switche + přístupové switche. Standard v enterprise sítích.
- **Mesh (síťová):** každý uzel spojen s více dalšími uzly. Redundance, odolnost. Drahé na kabeláž. Použití: páteřní sítě ISP, vojenskéSítě, Wi-Fi mesh systémy.
- **Hybridní:** kombinace výše uvedených (nejčastější v praxi).

---

## c) Síťové modely: ISO/OSI a TCP/IP

### Model ISO/OSI (7 vrstev)
Referenční model pro síťovou komunikaci (ISO, 1984). Každá vrstva zajišťuje specifické funkce a komunikuje pouze se sousedními vrstvami.

| Vrstva | Název | Funkce | Příklady protokolů/zařízení |
|---|---|---|---|
| 7 | **Aplikační** | Rozhraní pro aplikace | HTTP, FTP, SMTP, DNS, SSH |
| 6 | **Prezentační** | Kódování, šifrování, komprese | SSL/TLS, JPEG, ASCII, UTF-8 |
| 5 | **Relační** | Správa relací (session) | NetBIOS, RPC, SQL |
| 4 | **Transportní** | End-to-end přenos, řízení toku | TCP, UDP |
| 3 | **Síťová** | Logická adresace, směrování | IP, ICMP, RIP, OSPF – Router |
| 2 | **Linková** | Fyzická adresace (MAC), přístup na médium | Ethernet, Wi-Fi, Switch |
| 1 | **Fyzická** | Přenos bitů přes médium | Kabely, optika, Radio |

### Model TCP/IP (4 vrstvy)
Praktický model používaný pro internet (DARPA, 70. léta). Odpovídá implementaci internetu.

| TCP/IP vrstva | Odpovídá OSI vrstvám | Protokoly |
|---|---|---|
| **Aplikační** | 5–7 | HTTP, HTTPS, FTP, SSH, DNS, DHCP, SMTP |
| **Transportní** | 4 | TCP, UDP |
| **Síťová (Internet)** | 3 | IPv4, IPv6, ICMP, ARP |
| **Síťového přístupu** | 1–2 | Ethernet, Wi-Fi (802.11), ARP |

### Klíčové protokoly

**HTTP/HTTPS (port 80/443):** přenos webových stránek. HTTPS = HTTP + TLS šifrování.
**FTP (port 21):** přenos souborů. Nezabezpečený → dnes spíše SFTP/FTPS.
**DNS (port 53):** překlad doménových jmen na IP adresy (domain → IP). Hierarch: root → TLD (.cz, .com) → autoritativní DNS.
**DHCP (port 67/68):** automatické přidělování IP adres zařízením v síti.
**SMTP (port 25/587):** odesílání e-mailů. POP3 (110) / IMAP (143) – příjem.
**SSH (port 22):** zabezpečené vzdálené připojení k serveru (náhrada za Telnet).
**TCP (Transmission Control Protocol):** spojově orientovaný, spolehlivý přenos, kontrola chyb, řízení toku. 3-way handshake (SYN → SYN-ACK → ACK). Použití: web, e-mail, FTP.
**UDP (User Datagram Protocol):** nespojový, nespolehlivý, ale rychlý. Bez potvrzení. Použití: DNS, VoIP, streaming, online hry, DHCP.

---

## d) IP adresy – IPv4, IPv6, Subnetting

### IPv4
- 32bitová adresa, zapsaná jako 4 oktetů oddělených tečkami: `192.168.1.1`.
- Celkem ~4,3 miliardy adres (2³²) – **vyčerpány** (IANA 2011).
- **Třídy adres** (historické, dnes CIDR):
  - Třída A: 1.0.0.0 – 126.255.255.255 (velké sítě)
  - Třída B: 128.0.0.0 – 191.255.255.255 (střední sítě)
  - Třída C: 192.0.0.0 – 223.255.255.255 (malé sítě)

**Privátní IP adresy (RFC 1918) – nepoužívané na internetu:**
- 10.0.0.0 – 10.255.255.255 (/8)
- 172.16.0.0 – 172.31.255.255 (/12)
- 192.168.0.0 – 192.168.255.255 (/16) – domácí sítě

**Speciální adresy:**
- 127.0.0.1 – loopback (localhost)
- 0.0.0.0 – defaultní route, neurčená adresa
- 255.255.255.255 – broadcast

### Maska sítě (Subnet Mask) a CIDR
- Určuje, která část IP adresy je síťová část a která hostitelská.
- Zápis: `255.255.255.0` nebo CIDR: `/24`
- Příklad: `192.168.1.0/24` = síť s 254 použitelnými hosty (256 – síťová – broadcast).

**Subnetting (rozdělení sítě):**
- Rozdělení velké sítě na menší podsítě pro lepší organizaci a bezpečnost.
- Příklad: `192.168.1.0/24` → rozdělení na 4 podsítě /26 (každá 62 hostů).
- CIDR (Classless Inter-Domain Routing) – flexibilní přidělování adres bez pevných tříd.

### NAT (Network Address Translation)
- Překlad privátních IP na veřejnou IP (a zpět) na routeru.
- Umožňuje sdílení jedné veřejné IP celou sítí → „prodloužení" IPv4.

### IPv6
- 128bitová adresa, zapsaná jako 8 skupin po 4 hex číslicích: `2001:0db8:85a3::8a2e:0370:7334`.
- Celkem ~3,4 × 10³⁸ adres – prakticky nevyčerpatelné.
- **Výhody oproti IPv4:** obrovský adresní prostor, integrovaná bezpečnost (IPsec), lepší QoS, automatická konfigurace (SLAAC), není potřeba NAT.
- **Přechod IPv4 → IPv6:** dual-stack (zařízení podporuje obojí), tunelování (6to4, Teredo).
- Stav: ~45 % internetového provozu je již IPv6 (Google statistiky 2024).

**Speciální IPv6 adresy:**
- `::1` – loopback (localhost)
- `fe80::/10` – link-local adresy (automaticky přiděleny v LAN)
- `2000::/3` – globální unicast (veřejné IPv6)

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(2 min)** Základní pojmy – síť, uzel, paket, protokol; rozdělení PAN/LAN/MAN/WAN
2. **(2 min)** Topologie – sběrnicová, hvězdicová, mesh; výhody/nevýhody
3. **(3 min)** OSI model – 7 vrstev, funkce každé vrstvy, příklady protokolů
4. **(3 min)** TCP/IP model – 4 vrstvy, klíčové protokoly (HTTP, DNS, DHCP, TCP vs. UDP)
5. **(3 min)** IPv4 – adresace, privátní vs. veřejné adresy, maska sítě, NAT, subnetting
6. **(2 min)** IPv6 – proč existuje, formát, výhody, přechod
