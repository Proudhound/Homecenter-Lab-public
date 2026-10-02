# Gaming-PC / Windows-Pilot-Host

Stand: 2026-10-02

Diese Seite dokumentiert den Gaming-PC als leistungsstarken Windows-Client im HomeCenter-Lab und als ersten Pilot-Host für Windows-/Desktop-Tests, unter anderem für Curator Local.

> **Publication Security Gate:** Die zugrunde liegende `msinfo32`-Aufnahme wurde vor der Veröffentlichung sanitisiert. Rechnername, Benutzername, eindeutige IDs, Seriennummern, private Pfade und andere personenbezogene bzw. infrastrukturspezifische Angaben werden hier bewusst nicht veröffentlicht.

## Hardware

| Komponente | Stand |
|---|---|
| Hersteller | MSI / Micro-Star International |
| Systemmodell | B360 Gaming Infinite A (`MS-B915`) |
| Architektur | x86-64 |
| CPU | Intel Core i7-9700F @ 3.00 GHz |
| CPU-Kerne / Threads | 8 / 8 |
| RAM | 16 GB DDR4-2666 |
| GPU | NVIDIA GeForce RTX 2070 SUPER, 8 GB VRAM |
| Mainboard | MSI B360M BAZOOKA (`MS-7B24`), Rev. 1.0 |
| BIOS | American Megatrends B.50, 2019-04-09 |
| SMBIOS | 2.8 |
| Firmware-Modus | UEFI |
| Secure Boot | aktiviert |
| Gesamtspeicher | ca. 1,38 TB, mehrere lokale Laufwerke; detaillierte Datenträger-Inventarisierung separat |

## Virtualisierung

Die Systemübersicht bestätigt die wesentlichen CPU-/Firmware-Voraussetzungen für Hyper-V-artige Virtualisierung:

- VM-Monitor-Modus-Erweiterungen vorhanden
- Second Level Address Translation (SLAT) vorhanden
- Virtualisierung in der Firmware aktiviert
- Hardwareunterstützung für Datenausführungsverhinderung vorhanden

Damit eignet sich der Rechner neben Gaming auch für lokale Test-VMs und isolierte Windows-Pilotumgebungen.

## Windows-Pilotstatus

Für Desktop-/Installer-Tests wird dieser Rechner als erster realer Windows-Pilot verwendet.

Aus der sanitisierten Systemübersicht ist die Windows-/NT-Build-Familie `26100` erkennbar. Die genaue Edition und der vollständige Versionsstand werden bei Bedarf als separates, nicht-personenbezogenes Testmerkmal ergänzt.

Dieser Host ist **kein Clean-Machine-Ersatz**: Entwicklungssoftware und bestehende Konfigurationen können vorhanden sein. Clean-Machine-Tests müssen deshalb zusätzlich in einer frischen Windows-VM oder auf einem separaten, nicht vorbereiteten Windows-Gerät erfolgen.

## Geplante Rollen im HomeCenter-Lab

- primärer Gaming-PC
- Sunshine-Host für Moonlight-Streaming auf geeignete Clients
- leistungsstärkerer lokaler Entwicklungsrechner für Aufgaben, die den Laptop überfordern
- Windows-Pilot für Desktop-/Installer-Tests
- temporärer Testhost für Curator Local
- optionaler Virtualisierungs-/VM-Testhost

## Noch zu vervollständigen

Die folgenden Punkte sind im öffentlichen Inventar noch nicht vollständig erfasst bzw. werden erst nach sanitisiertem Gegencheck ergänzt:

- genaue RAM-Modulbelegung und Hersteller
- vollständige interne SSD-/HDD-Liste samt Kapazitäten und Schnittstellen
- Netzwerkkarten / Link-Geschwindigkeiten
- Netzteil und Gehäuse-/Kühlungsdaten
- genaue Windows-Edition und Versionsbezeichnung
- relevante Treiberstände für reproduzierbare GPU-/Streaming-Tests

## Quelle

- sanitisiert aus einer lokalen Windows-`msinfo32`-Systemübersicht vom 2026-10-02
- ergänzt um bereits verifizierte Geräteinventar-Daten des HomeCenter-Projekts
