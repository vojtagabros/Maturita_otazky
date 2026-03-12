# 3. Operační systémy a jejich dělení

> Souvisí s: [[01_Architektura_PC]] | [[04_Virtualizace]] | [[05_Pocitacove_site]] | [[08_Cloud_computing]]

---

## a) Definice OS, základní funkce, historický vývoj

### Definice
**Operační systém (OS)** je systémový software, který spravuje hardwarové a softwarové prostředky počítače a poskytuje základní služby pro aplikační programy. Tvoří **vrstvu abstrakce mezi hardwarem a uživatelem**.

Bez OS by každý program musel sám řídit hardware – OS tuto zodpovědnost centralizuje a zprostředkovává.

### Základní funkce OS

1. **Správa procesů** – plánování přístupu CPU (scheduling), vytváření/ukončování procesů, přepínání kontextu, multitasking, meziprocesová komunikace (IPC).
2. **Správa paměti** – alokace RAM procesům, ochrana paměťových prostorů, virtuální paměť (swap/stránkování), garbage collection na úrovni OS.
3. **Správa souborového systému** – organizace dat v souborech a adresářích, práva přístupu, žurnálování. FS: NTFS, ext4, FAT32, APFS, Btrfs.
4. **Správa zařízení** – komunikace s hardwarem přes ovladače (drivery), správa I/O operací, plug and play.
5. **Správa uživatelů** – autentizace, přístupová práva (ACL), uživatelské profily, skupiny.
6. **Síťové funkce** – TCP/IP stack, sdílení zdrojů, DNS resolver – viz [[05_Pocitacove_site]].
7. **Bezpečnost** – firewall (OS-level), šifrování souborového systému (BitLocker, FileVault), audit logů – viz [[14_Bezpecnost_HW_SW]].
8. **Uživatelské rozhraní** – CLI (příkazová řádka: bash, PowerShell) nebo GUI (grafické prostředí: GNOME, KDE, Explorer).

### Historický vývoj

- **50. léta:** žádný OS, programátor obsluhoval počítač přímo (dávkové zpracování na děrné štítky).
- **60. léta:** CTSS (MIT) – time-sharing. **UNIX (Bell Labs, 1969)** – klíčový milník, filozofie „vše je soubor", modularita, víceuživatelský systém. Psán v jazyce C.
- **70. léta:** UNIX se šíří na univerzity, vznik CP/M (první OS pro mikropočítače).
- **80. léta:** **MS-DOS (1981, Microsoft)** pro IBM PC. Apple Lisa (1983) – první komerční GUI. **Macintosh (1984).** Windows 1.0 (1985) – GUI nadstavba nad DOS. **GNU projekt** (Richard Stallman, 1983) – svobodný software.
- **90. léta:** Windows 95 (průlom – plug and play, 32bit, Start menu). **Linux (Linus Torvalds, 1991)** – open-source UNIX-like jádro. macOS předchůdce (Mac OS X, 2001). Windows NT – stabilní architektura pro profesionály.
- **2000. léta:** Windows XP (nejúspěšnější verze), Vista (nepopulární), macOS X Panther/Tiger. Linux dominuje na serverech.
- **2010. léta:** Windows 7 (oblíbený), Windows 8 (nepopulární), Windows 10. **Android (2008)** a **iOS (2007)** – mobilní revoluce. Kontejnerizace (Docker, 2013) – viz [[04_Virtualizace]].
- **Dnes:** Windows 11, macOS Sequoia, Ubuntu 24.04 LTS. AI integrace do OS (Copilot, Apple Intelligence).

---

## b) Významní zástupci OS

### Windows (Microsoft)
- Nejrozšířenější desktopový OS (~70 % desktopového trhu).
- Evoluce: 95 → 98 → XP → Vista → 7 → 8 → 10 → 11.
- Jádro: **Windows NT** (hybridní mikrokernel – HAL, kernel, subsystémy).
- Souborový systém: **NTFS** (žurnálování, šifrování EFS, přístupová práva, velké soubory).
- Aktivní adresář (Active Directory) – správa firemních sítí.

### Linux
- Open-source, UNIX-like kernel (Linus Torvalds, 1991).
- Distribuce (distro): **Ubuntu, Debian** (uživatelsky přívětivé), **Fedora, RHEL** (enterprise), **Arch Linux** (pokročilí uživatelé), **Android** (mobilní).
- **Trh:** ~96 % webserverů, 100 % Top500 superpočítačů, ~72 % mobilních zařízení (přes Android).
- Souborový systém: **ext4** (nejrozšířenější), **Btrfs** (snapshoty, RAID), **XFS** (velké objemy).
- Správce balíčků: apt (Debian/Ubuntu), dnf/yum (Fedora/RHEL), pacman (Arch).

### macOS (Apple)
- **UNIX-based** (Darwin kernel = XNU = Mach microkernel + BSD), certifikovaný UNIX.
- Výhradně pro Apple hardware (Intel → Apple Silicon M-series).
- Verze: Big Sur → Monterey → Ventura → Sonoma → Sequoia.
- Souborový systém: **APFS** (Apple File System – optimalizovaný pro SSD, snapshoty, šifrování).
- Homebrew – neoficiální správce balíčků.

### Android (Google)
- Mobilní OS na bázi **Linux kernelu**, open-source (AOSP – Android Open Source Project).
- ~72 % celosvětového mobilního trhu.
- Google služby (Play Store, Gmail, Maps) jsou proprietární nadstavba.
- Souborový systém: **ext4**, F2FS (Flash-Friendly File System).

### iOS / iPadOS (Apple)
- Uzavřený mobilní OS pro iPhone a iPad, jádro **XNU** (stejné jako macOS).
- ~27 % mobilního trhu, vyšší průměrná hodnota segmentu.
- Striktní ekosystém (App Store, sandboxing aplikací) = vyšší bezpečnost.
- Dlouhá podpora aktualizací (5–6 let pro starší zařízení).

---

## c) Klasifikace OS

### Podle počtu uživatelů
- **Jednouživatelský (Single-user):** jeden uživatel v danou chvíli. Příklad: MS-DOS, starší Windows verze.
- **Víceuživatelský (Multi-user):** více uživatelů současně, každý s izolovaným prostředím. Příklad: Linux/UNIX servery, Windows Server s Active Directory.

### Podle počtu procesů
- **Jednoúlohový (Single-tasking):** jeden program najednou. Příklad: MS-DOS.
- **Víceúlohový (Multi-tasking):**
  - **Kooperativní:** programy samy uvolňují CPU (Windows 3.x, Mac OS 9). Problém: jeden zamrzlý program zablokuje celý systém.
  - **Preemptivní:** OS násilně přerušuje procesy a přiděluje CPU ostatním podle priorit (všechny moderní OS).

### Podle prostředí
- **Real-time OS (RTOS):** deterministická odezva, pevné časové limity (hard real-time / soft real-time). Použití: průmyslové řízení (PLC), avionika, lékařské přístroje, automotive. Příklady: **FreeRTOS**, **VxWorks**, **QNX**, **RTEMS**.
- **Mobilní OS:** optimalizovaný pro dotykové ovládání, ARM procesory, nízkou spotřebu baterie, senzory. Příklady: Android, iOS, HarmonyOS (Huawei).
- **Serverové OS:** stabilita, bezpečnost, správa stovek uživatelů a služeb, 24/7 dostupnost. Příklady: **Windows Server 2022**, **Ubuntu Server 24.04 LTS**, **RHEL 9**.
- **Embedded OS:** minimalistické OS pro vestavěné systémy bez monitoru. Příklady: Yocto Linux (Raspberry Pi), RTOS varianty, FreeRTOS na mikrokontrolérech.
- **Cloud OS / Hypervisor:** správa virtuálních strojů – viz [[04_Virtualizace]]. Příklady: VMware ESXi, Microsoft Hyper-V.

---

## d) Srovnání hlavních OS

| Vlastnost | Windows 11 | Linux (Ubuntu) | macOS | Android | iOS |
|---|---|---|---|---|---|
| Typ | Proprietární | Open-source | Proprietární | Open-source (AOSP) | Proprietární |
| Trh | Desktop 70 % | Server 96 % | Desktop 15 % | Mobil 72 % | Mobil 27 % |
| Jádro | NT Kernel | Linux Kernel | XNU (Darwin) | Linux Kernel | XNU |
| FS | NTFS | ext4, Btrfs | APFS | ext4, F2FS | APFS |
| Cena | ~130 EUR | Zdarma | Zdarma (s HW) | Zdarma | Zdarma (s HW) |
| Shell | PowerShell, CMD | bash, zsh | zsh, bash | — | — |

### Windows – detail
- **Výhody:** nejširší kompatibilita softwaru a her, firemní ekosystém (AD, Azure), plug and play.
- **Nevýhody:** náchylnější na malware (největší cíl kvůli tržnímu podílu), telemetrie/soukromí, cena, bloatware.

### Linux – detail
- **Výhody:** zdarma, velmi bezpečný, konfigurovatelný, ideální pro servery, vývoj a DevOps, komunita.
- **Nevýhody:** menší podpora komerčního softwaru (Adobe, starší hry), vyšší learning curve pro běžné uživatele, fragmentace distribucí.

### macOS – detail
- **Výhody:** UNIX základ (terminál, vývojářské nástroje), špičková integrace s Apple ekosystémem (iPhone, iPad, AirPods), stabilita, Apple M-series výkon.
- **Nevýhody:** uzavřený ekosystém, vysoká cena hardwaru, omezená konfigurovatelnost, závislost na Apple.

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(2 min)** Definice OS – proč ho potřebujeme, vrstva abstrakce
2. **(3 min)** Funkce OS – správa procesů, paměti, souborů, zařízení, bezpečnosti
3. **(2 min)** Historie – UNIX (1969), MS-DOS, Windows 95, Linux (1991), mobilní OS
4. **(3 min)** Klasifikace – jednouživatelský/víceuživatelský, multitasking, RTOS, mobilní
5. **(3 min)** Srovnání Windows/Linux/macOS – výhody, nevýhody, tržní podíly
6. **(2 min)** Android vs. iOS – otevřenost, bezpečnost, podpora
