# 6. Síťová zařízení a bezdrátové sítě

> Souvisí s: [[05_Pocitacove_site]] | [[07_Zabezpeceni_siti]] | [[08_Cloud_computing]]

---

## a) Základní přenosová média

Přenosová média slouží k fyzickému přenosu dat mezi zařízeními. Dělíme je na **kabelová** (vedená) a **bezdrátová** (nevedená).

### Kroucená dvoulinka (Twisted Pair)
- Nejrozšířenější kabelové médium pro LAN.
- Páry vodičů jsou zakrouceny – snižuje elektromagnetické rušení (EMI).
- **UTP (Unshielded Twisted Pair):** bez stínění, levnější, nejběžnější (domácnosti, kanceláře).
- **STP/FTP (Shielded/Foiled Twisted Pair):** s stíněním – průmyslové prostředí s vyšším rušením.
- Kategorie:
  - **Cat5e:** 1 Gbit/s, 100 MHz, max 100 m – stále rozšířená.
  - **Cat6:** 1 Gbit/s (10 Gbit/s do 55 m), 250 MHz.
  - **Cat6a:** 10 Gbit/s, 500 MHz, max 100 m.
  - **Cat7/8:** 25–40 Gbit/s, datová centra.
- Konektor: **RJ-45**, standardy zapojení T568A/T568B.

### Koaxiální kabel
- Centrální vodič obklopený izolací, stíněním a pláštěm.
- Historicky LAN (10BASE2 – „thinnet"), dnes kabelová TV, internet od kabelového operátora (DOCSIS), anténní rozvody.

### Optický kabel (Fiber Optic)
- Přenos dat pomocí **světelných pulzů** v skleněném nebo plastovém vláknu.
- Imunní vůči EMI, bezpečnější (nelze odposlouchávat indukcí), obrovská přenosová kapacita.
- **Jednovidové (Single-mode, SMF):** úzké jádro (~9 µm), jeden paprsek, vzdálenosti až stovky km. Laser. Použití: páteřní sítě, ISP.
- **Vícevidové (Multi-mode, MMF):** širší jádro (~50/62,5 µm), více paprsků, max ~550 m. LED nebo laser. Použití: datová centra, campus sítě.
- Konektory: LC, SC, ST, MPO.
- Přenosové rychlosti: 1 Gbit/s → 400 Gbit/s → Tbit/s.

### Bezdrátová média
- Rádiové vlny (Wi-Fi, Bluetooth, Zigbee, LTE/5G), infračervené záření (IR dálkové ovladače), mikrovlny (satelit, WiMAX).

---

## b) Switch, Router, Hub, Access Point

### Hub (rozbočovač)
- Pracuje na **vrstvě 1 (fyzické)** modelu OSI.
- Přijatý signál **rozesílá na všechny porty** (broadcast) – sdílené médium.
- Kolize (CSMA/CD), veškerá zařízení sdílejí bandwidth.
- **Dnes již prakticky nepoužívaný** – nahrazen switchem.

### Switch (přepínač)
- Pracuje na **vrstvě 2 (linková)** – někdy vrstva 3 (L3 switch).
- Pamatuje si **MAC adresy** zařízení na jednotlivých portech (CAM/MAC tabulka).
- Posílá data **pouze na cílový port** – ne broadcast (kromě neznámých MAC = flood).
- **Full-duplex:** každý port má dedikovaný bandwidth → eliminace kolizí.
- **VLAN (Virtual LAN):** logické rozdělení sítě na switchi – oddělení provozu bez fyzického oddělení.
- **PoE (Power over Ethernet):** napájení zařízení (AP, IP kamery, IP telefony) přes síťový kabel.
- Příklady: Cisco Catalyst, HPE Aruba, Mikrotik CRS.

### Router (směrovač)
- Pracuje na **vrstvě 3 (síťová)** – pracuje s IP adresami.
- **Směruje pakety** mezi různými sítěmi (LAN, WAN, internet).
- Udržuje **směrovací tabulku** – nejlepší cesta k cílové síti.
- Funkce: NAT, DHCP server, firewall (základní), VPN, QoS.
- **Statické směrování:** manuálně nakonfigurované trasy.
- **Dynamické směrování:** protokoly RIP, OSPF, BGP – routery si vyměňují informace o sítích.
- Domácí router: kombinace router + switch + Wi-Fi AP + DHCP + NAT v jednom zařízení.

### Access Point (přístupový bod, AP)
- Pracuje na **vrstvě 2** – bezdrátový ekvivalent switche.
- Propojuje bezdrátové klienty s drátovou sítí.
- **Autonomous AP:** funguje samostatně, konfigurován individuálně.
- **Lightweight/Managed AP:** řízeno centrálním kontrolérem (WLC – Wireless LAN Controller). Standard pro enterprise sítě (Cisco, Meraki, Ubiquiti UniFi).
- **Mesh AP:** AP spolupracují a vytváří bezešvou Wi-Fi síť bez nutnosti kabeláže (Eero, Google Nest, TP-Link Deco).

### Firewall
Viz [[07_Zabezpeceni_siti]] – filtruje síťový provoz.

### Modem
- Modulátor/demodulátor – převádí digitální signál na analogový a zpět.
- DSL modem (telefonní linka), kabelový modem (koax), optický ONT/ONU (GPON).

---

## c) Kabelové a bezdrátové technologie

### Kabelové technologie
- **Ethernet (IEEE 802.3):** nejrozšířenější standard pro kabelové LAN. Varianty:
  - 100BASE-TX: Fast Ethernet (100 Mbit/s)
  - 1000BASE-T: Gigabit Ethernet (1 Gbit/s) – dnes standard pro domácnosti/kanceláře
  - 10GBASE-T: 10 Gbit/s přes Cat6a – datová centra, servery
  - 25G/40G/100G/400G Ethernet – datová centra, ISP páteřní sítě
- **Power Line Communication (PLC):** přenos dat přes elektrické rozvody – HomePlug, G.hn.
- **Optická vlákna:** viz sekce a) – páteřní sítě, FTTH (Fiber to the Home).

### Bezdrátové technologie
- **Wi-Fi (IEEE 802.11):** viz sekce d).
- **Bluetooth (IEEE 802.15.1):** PAN, dosah ~10–100 m. BT 5.0/5.3 – vyšší rychlost a dosah. BLE (Low Energy) pro IoT a wearables.
- **Zigbee (IEEE 802.15.4):** nízká spotřeba, mesh topologie, IoT/smart home (Philips Hue, Amazon Sidewalk).
- **Z-Wave:** proprietární, smart home, mesh, nižší rušení (868 MHz v EU).
- **NFC (Near Field Communication):** dosah ~4 cm, bezkontaktní platby, přihlašování.
- **RFID:** identifikace na vzdálenosti cm až m, logistika, přístupové karty.
- **Mobilní sítě:** 4G LTE (až 150 Mbit/s), 5G (až 10 Gbit/s, latence < 1 ms) – průmysl 4.0, IoT, autonmní vozidla.
- **Satelitní internet:** Starlink (SpaceX) – LEO (Low Earth Orbit), latence ~20 ms, rychlost 50–500 Mbit/s.

---

## d) Wi-Fi standardy, šifrování

### Standardy Wi-Fi (IEEE 802.11)

| Standard | Rok | Frekv. pásmo | Max. rychlost | Název Wi-Fi |
|---|---|---|---|---|
| 802.11b | 1999 | 2,4 GHz | 11 Mbit/s | Wi-Fi 1 |
| 802.11a | 1999 | 5 GHz | 54 Mbit/s | Wi-Fi 2 |
| 802.11g | 2003 | 2,4 GHz | 54 Mbit/s | Wi-Fi 3 |
| 802.11n | 2009 | 2,4/5 GHz | 600 Mbit/s | Wi-Fi 4 |
| 802.11ac | 2014 | 5 GHz | 6 933 Mbit/s | Wi-Fi 5 |
| 802.11ax | 2019 | 2,4/5/6 GHz | 9 608 Mbit/s | Wi-Fi 6/6E |
| 802.11be | 2024 | 2,4/5/6 GHz | 46 120 Mbit/s | Wi-Fi 7 |

**Klíčové techniky zvyšování výkonu:**
- **MIMO (Multiple Input Multiple Output):** více antén pro paralelní přenos.
- **MU-MIMO (Multi-User MIMO):** Wi-Fi 5/6 – komunikace s více zařízeními současně.
- **OFDMA (Orthogonal Frequency Division Multiple Access):** Wi-Fi 6 – efektivní využití kanálu pro mnoho klientů.
- **BSS Coloring (Wi-Fi 6):** snižuje interferenci v hustě osídlených oblastech.
- **2,4 GHz:** lepší dosah a průnik stěnami, pomalejší, přeplněnější (Bluetooth, mikrovlnky).
- **5 GHz:** rychlejší, kratší dosah, méně rušení.
- **6 GHz (Wi-Fi 6E/7):** nové pásmo, méně rušení, vysoká rychlost, krátký dosah.

### Šifrování Wi-Fi

**WEP (Wired Equivalent Privacy):**
- Zastaralý standard (1997), 40/128bitový klíč RC4.
- **Prolomitelný za minuty** – dnes zcela nevhodný.

**WPA (Wi-Fi Protected Access):**
- Přechodový standard (2003), TKIP šifrování (stále RC4, ale lepší správa klíčů).
- Stále zranitelný (útoky na TKIP) – nevhodný.

**WPA2 (IEEE 802.11i, 2004):**
- AES-CCMP šifrování – bezpečný standard po mnoho let.
- **Osobní (PSK):** heslo sdílené všemi uživateli – domácnosti.
- **Enterprise (802.1X):** každý uživatel má vlastní přihlašovací údaje (RADIUS server) – firmy.
- Zranitelnost: **KRACK attack (2017)** – napadá 4-way handshake (opraveno patchem).
- Slabé heslo = náchylné na slovníkové útoky.

**WPA3 (2018):**
- **SAE (Simultaneous Authentication of Equals)** místo PSK – odolné vůči slovníkovým útokům (i offline).
- **Forward Secrecy:** kompromitování jednoho klíče neodhalí historický provoz.
- **WPA3-Enterprise 192-bit:** pro vládní a citlivé prostředí.
- **Enhanced Open (OWE):** šifrování i bez hesla (otevřené sítě) – ochrana na veřejných hotspotechek.
- Dnes doporučený standard pro nové nasazení.

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(2 min)** Přenosová média – UTP kategorie, koaxiál, optika (SMF vs. MMF)
2. **(3 min)** Hub vs. Switch vs. Router vs. AP – vrstvy OSI, funkce, rozdíly
3. **(2 min)** Kabelové technologie – Ethernet standardy (100M/1G/10G), optika FTTH
4. **(2 min)** Bezdrátové technologie – Bluetooth, Zigbee, NFC, 5G
5. **(3 min)** Wi-Fi standardy – 802.11b/g/n/ac/ax/be, frekvence, rychlosti, Wi-Fi 6
6. **(3 min)** Šifrování Wi-Fi – WEP (slabý), WPA, WPA2 (AES), WPA3 (SAE), Enterprise vs. Personal
