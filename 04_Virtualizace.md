# 4. Virtualizace – princip a výhody v IT infrastruktuře

> Souvisí s: [[03_Operacni_systemy]] | [[02_Datova_uloziste]] | [[08_Cloud_computing]] | [[05_Pocitacove_site]]

---

## a) Princip virtualizace

**Virtualizace** je technologie, která umožňuje vytvořit abstraktní (virtuální) verzi počítačového zdroje – procesoru, paměti, síťového rozhraní, úložiště nebo celého počítače – oddělenou od fyzického hardwaru.

### Základní myšlenka
Na jednom fyzickém serveru (host) lze provozovat **více logicky oddělených systémů (guests)** současně, přičemž každý z nich „si myslí", že má přístup k dedikovanému hardwaru.

### Klíčové pojmy
- **Host (fyzický stroj):** skutečný hardware, na kterém virtualizace běží.
- **Guest (virtuální stroj, VM – Virtual Machine):** virtuální počítač s vlastním OS a aplikacemi.
- **Hypervisor (Virtual Machine Monitor, VMM):** software řídící virtualizaci, přiděluje hardwarové zdroje VM.
- **Snapshot:** okamžitá záloha stavu VM – lze obnovit ke konkrétnímu bodu.
- **Live Migration:** přesun běžící VM na jiný fyzický server bez výpadku.

### Historický kontext
- Virtualizace existuje od 60. let (IBM mainframe, CP/CMS – 1967).
- Moderní renesance: VMware (1999), Xen (2003), KVM (2007), Docker (2013).

---

## b) Význam virtualizace v ICT, výhody a nevýhody

### Výhody virtualizace

1. **Konsolidace serverů:** místo 20 fyzických serverů (každý využit na 10 %) stačí 2–3 výkonné servery s plným vytížením. Úspora nákladů na hardware, energii, chlazení, prostor.
2. **Izolace:** každá VM je oddělená – problém v jedné VM neovlivní ostatní. Bezpečnostní sandbox.
3. **Snapshoty a zálohy:** okamžité zálohy stavu VM, rychlé obnovení po havárii (Disaster Recovery).
4. **Rychlé nasazení:** novou VM lze spustit za minuty (vs. dny u fyzického serveru).
5. **Testovací prostředí:** bezpečné testování softwaru, OS, síťových konfigurací bez rizika pro produkci.
6. **Live Migration:** přesun VM bez výpadku – usnadňuje údržbu hardware.
7. **Škálovatelnost:** dynamické přidávání/ubírání zdrojů (CPU, RAM) VM bez restartu.
8. **Multiplatformní testování:** vývoj a testování na různých OS současně na jednom stroji.

### Nevýhody virtualizace

1. **Výkonnostní overhead:** hypervisor spotřebovává část výkonu. U plné virtualizace až 5–15 % overhead (závisí na workloadu).
2. **Složitost správy:** více VM = komplexnější monitoring, síťování, bezpečnost.
3. **Single point of failure:** výpadek fyzického hostitele způsobí výpadek všech VM (mitigace: clustering, HA).
4. **Licenční náklady:** VMware vSphere, Windows Server licence pro virtualizaci jsou drahé.
5. **Bezpečnost:** VM escape (útočník z VM proniká na host) – vzácné, ale závažné.

### Srovnání s jinými přístupy

| Přístup | Izolace | Výkon | Overhead | Rychlost startu |
|---|---|---|---|---|
| Fyzický server | Absolutní | 100 % | 0 % | Minuty |
| VM (hypervisor) | Vysoká | ~90 % | 5–15 % | Sekundy–minuty |
| Kontejner (Docker) | Střední | ~98 % | ~2 % | Milisekundy |
| Serverless | Nízká | Variabilní | Variabilní | Milisekundy |

---

## c) Typy virtualizace

### 1. Plná virtualizace (Full Virtualization)
- Hypervisor emuluje kompletní hardware, guest OS **neví, že je virtualizován**.
- Guest OS nevyžaduje žádné úpravy.
- Využívá hardwarovou podporu: **Intel VT-x** (Vanderpool), **AMD-V** (AMD Virtualization).
- Příklady: VMware Workstation, Oracle VirtualBox, Microsoft Hyper-V (v certain modes), KVM.

### 2. Paravirtualizace (Paravirtualization)
- Guest OS je **upraven** (patched) a ví, že běží ve virtuálním prostředí.
- Komunikuje přímo s hypervisorem přes speciální API (hypercalls) místo emulace hardware.
- **Výhody:** vyšší výkon (nižší overhead) – není třeba emulovat veškerý hardware.
- **Nevýhody:** vyžaduje modifikaci guest OS – nelze použít nemodifikované Windows starší verze.
- Příklady: **Xen** (Amazon EC2 historicky), KVM s VirtIO drivery.

### 3. Kontejnerizace (OS-level Virtualization)
- Kontejnery sdílejí **jádro (kernel) hostitelského OS**, ale mají izolovaný souborový systém, procesy, síť.
- Žádná emulace hardwaru → minimální overhead.
- **Výhody:** extrémně rychlý start (ms), malá velikost (MB vs. GB u VM), ideální pro mikroservisy.
- **Nevýhody:** nižší izolace (sdílený kernel), všechny kontejnery musí mít stejný typ OS jako host (Linux kontejner na Linux hostu).
- Technologie: **cgroups** (omezení zdrojů) + **namespaces** (izolace procesů/sítě/souborového systému) v Linuxu.
- Příklady: **Docker, Podman, LXC/LXD**.

### Porovnání VM vs. kontejner

```
Fyzický server
├── Hypervisor (VMware, KVM)
│   ├── VM 1: [Guest OS 1] + [App A] + [App B]
│   └── VM 2: [Guest OS 2] + [App C]
│
└── Container Runtime (Docker)
    ├── [Host OS kernel (sdílený)]
    ├── Container 1: [Libs] + [App A]
    ├── Container 2: [Libs] + [App B]
    └── Container 3: [Libs] + [App C]
```

### 4. Další typy virtualizace
- **Síťová virtualizace (SDN – Software Defined Networking):** virtuální sítě, VLAN, overlay sítě.
- **Virtualizace úložiště:** SAN, NAS, abstrakce fyzického úložiště do logických poolů.
- **Desktopová virtualizace (VDI – Virtual Desktop Infrastructure):** uživatelé přistupují ke vzdáleným VM (Citrix, VMware Horizon).
- **Aplikační virtualizace:** aplikace běží v izolovaném prostředí (Microsoft App-V, Flatpak na Linuxu).

---

## d) Aktuální virtualizační technologie

### VMware (nyní Broadcom)
- **VMware vSphere/ESXi:** typ 1 hypervisor (bare-metal) – průmyslový standard pro enterprise.
- **VMware Workstation/Fusion:** typ 2 hypervisor (hostovaný) pro pracovní stanice.
- **vCenter Server:** centrální správa VMware infrastruktury.
- Pozn.: Broadcom (2023) změnil licenční model – kontroverzní přechod na předplatné.

### VirtualBox (Oracle)
- Typ 2 hypervisor (hostovaný), open-source, multiplatformní (Windows/Linux/macOS).
- Ideální pro testovaání, vzdělávání, vývoj. Podpora snapshot, sdílených složek, síťových módů.
- Méně výkonný než VMware, ale zdarma.

### KVM (Kernel-based Virtual Machine)
- Vestavěný hypervisor v Linux kernelu (od verze 2.6.20, 2007). Typ 1.5 (využívá host OS kernel).
- Součást většiny Linux distribucí, základ pro OpenStack, RHEV, oVirt.
- Správa: **virt-manager** (GUI), **virsh** (CLI), **QEMU** (emulace hardware pro KVM).
- Používán Linuxovými cloudy (AWS historicky, OpenStack).

### Docker
- Kontejnerizační platforma (Solomon Hykes, 2013) – revoluční dopad na DevOps.
- **Docker Engine** (runtime) + **Docker Hub** (registry obrazů) + **Docker Compose** (multi-kontejner).
- **Dockerfile** – textový soubor definující obsah kontejnerového obrazu.
- **Kubernetes (K8s):** orchestrátor kontejnerů – automatické nasazení, škálování, správa kontejnerů v clusteru. Standard pro produkční cloudové prostředí. Viz [[08_Cloud_computing]].

### Hyper-V (Microsoft)
- Typ 1 hypervisor integrovaný ve Windows Server a Windows 10/11 Pro.
- Základ pro Azure virtuální stroje.
- **Windows Subsystem for Linux 2 (WSL2):** využívá Hyper-V pro spuštění Linuxového kernelu ve Windows.

---

## Shrnutí – osnova ústní zkoušky (15 minut)

1. **(2 min)** Co je virtualizace – definice, host/guest/hypervisor, historický kontext
2. **(3 min)** Výhody – konsolidace, snapshoty, rychlé nasazení, izolace; nevýhody
3. **(2 min)** Plná virtualizace – Intel VT-x/AMD-V, VMware, VirtualBox
4. **(2 min)** Paravirtualizace – Xen, hypercalls, výhody oproti plné virtualizaci
5. **(3 min)** Kontejnerizace – Docker, cgroups/namespaces, VM vs. kontejner srovnání
6. **(3 min)** Technologie – VMware ESXi, KVM, Docker + Kubernetes, Hyper-V
