# HomeCenter Lab Public

[Deutsch](#deutsch) · [English](#english)

## Deutsch

**HomeCenter Lab Public** ist die öffentlich freigegebene Dokumentations- und Open-Source-Schicht meines privaten Home-Labs.

Ziel ist, den Aufbau eines alltagstauglichen, local-first Home-Labs nachvollziehbar zu dokumentieren: von Home Assistant und Proxmox über Netzwerk, Automatisierung, Energie und Backups bis hin zu lokalen KI- und Sprachdiensten.

### Grundprinzipien

- **Family first** – Technik muss einen konkreten Nutzen im Alltag haben.
- **Local first** – lokale Verarbeitung wird bevorzugt, wo sie sinnvoll ist.
- **Integrate before replace** – funktionierende Systeme werden zuerst integriert statt ersetzt.
- **Manual control survives** – kritische Hausfunktionen bleiben manuell bedienbar.
- **Security by publication design** – keine Zugangsdaten, IP-Adressen, MAC-Adressen, Seriennummern, privaten Schlüssel, internen Hostnamen oder personenbezogenen Detaildaten.
- **Reproducible where possible** – veröffentlichte Anleitungen und Konfigurationen sollen ohne private Infrastrukturdetails verständlich und nachbaubar sein.

### Bereiche

- **Family** – Family Board, Kalender, Einkauf, Tagesübersicht und einfache Aktionen
- **Automate** – Home Assistant, Szenen, Regeln und lokale Automationen
- **Ops** – Server, Netzwerk, Backups, Inventar, Monitoring und Wartung
- **Intelligence** – lokale Sprache, Suche, Zusammenfassungen, Second Brain und KI-Experimente
- **Energy** – PV, Speicher, Hauslast und herstellerneutrale Energieansichten

### Repository-Struktur

```text
.
├── README.md
├── README_EN.md
├── LICENSE
├── LICENSE-DOCS
├── ROADMAP.md
├── SECURITY.md
└── docs/
    ├── architecture/
    ├── product/
    ├── hardware/
    ├── networking/
    ├── automation/
    ├── energy/
    ├── security/
    └── ai-voice/
```

### Was bewusst nicht veröffentlicht wird

Das private Home-Lab-Repository enthält zusätzliche Betriebs- und Inventardaten. Diese bleiben privat. Nicht veröffentlicht werden insbesondere:

- IP- und MAC-Adressen
- Seriennummern und eindeutige Gerätekennungen
- WLAN-, VPN- und API-Zugangsdaten
- Schlüssel, Tokens und Secrets
- exakte interne Netz- und Hostdetails
- private Kamerabilder und Rohdaten
- personenbezogene Familien- und Standortdetails

### Status

Das Projekt befindet sich im aktiven Aufbau. Inhalte werden schrittweise aus dem privaten Home-Lab in bereinigter Form übernommen.

---

## English

**HomeCenter Lab Public** is the public documentation and open-source layer of my private home lab.

The goal is to document the build-out of a practical, local-first home lab in a reproducible way: from Home Assistant and Proxmox to networking, automation, energy, backups, local AI and voice services.

### Core principles

- **Family first** – technology must provide clear everyday value.
- **Local first** – local processing is preferred where practical.
- **Integrate before replace** – working systems are integrated before being replaced.
- **Manual control survives** – critical home functions remain manually operable.
- **Security by publication design** – no credentials, IP addresses, MAC addresses, serial numbers, private keys, internal hostnames or personal detail data are published.
- **Reproducible where possible** – public guides and configurations should remain understandable without exposing private infrastructure.

### Areas

- **Family** – family board, calendars, shopping, daily overview and simple actions
- **Automate** – Home Assistant, scenes, rules and local automation
- **Ops** – servers, networking, backups, inventory, monitoring and maintenance
- **Intelligence** – local voice, search, summaries, second brain and AI experiments
- **Energy** – PV, storage, household load and vendor-neutral energy views

### What is intentionally not published

The private HomeCenter repository contains additional operational and inventory data. Those remain private, including IP and MAC addresses, device serial numbers, Wi-Fi/VPN/API credentials, secrets, internal host details, camera footage and personal household information.

### Status

The project is under active development. Public-safe material is gradually mirrored from the private lab into this repository.
