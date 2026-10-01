# 2026-09-30 — ThinkCentre M920q: Abnahme vor Proxmox

## Ziel

Einen gebrauchten Lenovo ThinkCentre M920q vollständig prüfen, **bevor** das vorinstallierte Windows überschrieben, zusätzliche Hardware eingebaut oder Proxmox installiert wird.

Die zentrale Regel war:

> Erst Lieferzustand und Funktionsfähigkeit belegen, dann umbauen und reprovisionieren.

## Ausgangskonfiguration

Der getestete Tiny-PC entsprach der vorgesehenen Home-Server-Klasse:

- Intel Core i5-8500T
- 16 GB DDR4-2667
- 256-GB-NVMe
- Intel Gigabit Ethernet
- Intel Wi-Fi
- TPM
- Windows Pro als vorhandenes Ausgangssystem

Geräteseriennummern, MAC-Adressen und Lizenzdaten wurden für diese öffentliche Dokumentation entfernt.

## Schritt 1 — Hardwareinventar

Windows/CIM wurde zunächst genutzt, um CPU, RAM, Datenträger und Netzwerkadapter zu erfassen.

Ergebnis:

- CPU: 6 Kerne / 6 Threads
- RAM: 16 GB als einzelnes 16-GB-Modul
- NVMe: Samsung MZVLB256HAHQ-000L7, 256 GB
- NVMe: Healthy
- Wear-Indikator während der Prüfung: 0
- NVMe-Temperatur während der Prüfung: 48 °C

Der einzelne 16-GB-Riegel ist für das Lab praktisch, weil eine spätere 32-GB-Erweiterung ohne vollständigen Austausch der Bestückung möglich ist.

## Schritt 2 — Windows-Aktivierung und Reprovisioning-Sicherheit

Vor dem Löschen des Systems wurde geprüft:

- Windows Professional ist dauerhaft aktiviert.
- Ein Firmware-/OA3-Key ist vorhanden.
- BitLocker ist nicht aktiv.
- Das Systemvolume ist vollständig entschlüsselt.
- TPM ist vorhanden, bereit, aktiviert und provisioniert.

Der vollständige Produktschlüssel wurde **nicht** in Git übernommen.

## Schritt 3 — Versionsquirk bei Windows

Eine Standardabfrage meldete weiterhin den String `Windows 10 Pro`.

Gleichzeitig ergaben:

- `DisplayVersion = 25H2`
- Build `26200.9457`

Die Lehre daraus: Für reproduzierbares Inventar nicht nur `ProductName` speichern, sondern mindestens Edition, DisplayVersion und Build zusammen erfassen.

## Schritt 4 — BIOS aktualisieren

Das Gerät lief zunächst mit BIOS `M1UKT77A`.

Noch unter dem funktionierenden Windows wurde das offizielle Lenovo-BIOS-Update durchgeführt.

Danach:

- BIOS: `M1UKT79A`
- Machine Type und Seriennummer wurden im Updater **nicht** verändert.

Dieser Zeitpunkt ist günstig für Firmware-Updates: Das vorhandene Betriebssystem funktioniert noch, BitLocker wurde geprüft und das System ist noch nicht reprovisioniert.

## Schritt 5 — Virtualisierung aktivieren

Im Lenovo-BIOS lag die Einstellung unter:

```text
Advanced
└── CPU Setup
    ├── Intel(R) Virtualization Technology -> Enabled
    └── VT-d                              -> Enabled
```

## Problem 1 — WMI meldet trotzdem drei False-Werte

Nach BIOS-Änderung und selbst nach einem Kaltstart meldete:

```powershell
Get-CimInstance Win32_Processor |
  Format-List Name,VirtualizationFirmwareEnabled,VMMonitorModeExtensions,SecondLevelAddressTranslationExtensions
```

weiterhin `False`.

Die zusätzliche Prüfung mit:

```powershell
systeminfo
```

zeigte jedoch, dass Windows bereits einen Hypervisor erkannt hatte und Virtualization Based Security lief.

Device Guard bestätigte ebenfalls aktives VBS.

**Lernpunkt:** Bei Virtualisierungsdiagnosen nicht ein einzelnes WMI-Feld zum alleinigen Gate machen. BIOS-Zustand, `systeminfo` und Hypervisor/VBS-Status gemeinsam bewerten.

## Problem 2 — Win32_DeviceGuard im falschen Namespace

Der direkte Aufruf:

```powershell
Get-CimInstance Win32_DeviceGuard
```

lieferte „Ungültige Klasse“.

Korrekt war:

```powershell
Get-CimInstance -Namespace root\Microsoft\Windows\DeviceGuard -ClassName Win32_DeviceGuard
```

Damit konnte der VBS-Status erfolgreich bestätigt werden.

## Schritt 6 — Arbeitsspeicher testen

Vor dem Öffnen des Rechners wurde die Windows-Speicherdiagnose ausgeführt.

Ergebnis:

- Diagnose abgeschlossen
- keine Speicherfehler festgestellt

Damit existiert ein sauberer RAM-Baseline-Test **vor** jedem Hardwareumbau.

## Schritt 7 — Sekundären Datenträger vorbereiten

Eine vorhandene 1-TB-SATA-HDD wurde separat vorgetestet:

- Health: Healthy
- Temperatur beim Test: 37 °C
- Betriebsstunden: rund 17.800 h
- keine gemeldeten Lesefehler

Wegen der bereits hohen Betriebszeit ist ihre geplante Rolle bewusst:

- Backups
- ISO-Images
- Templates
- Archiv-/Bulk-Daten

und **nicht**:

- primäre Datenbank
- latency-sensitive VM-Datenträger
- einziger Speicher wichtiger Daten

## Storage-Entscheidung

```text
NVMe
  -> Proxmox
  -> aktive VMs/Container
  -> schnelle Daten

SATA-HDD
  -> Backup
  -> ISO/Templates
  -> Archiv/Bulk
```

Nach dem Einbau soll zunächst geprüft werden, ob beide Laufwerke gemeinsam korrekt erkannt werden.

Für die eigentliche Proxmox-Installation wird die zweite HDD anschließend optional wieder kurz getrennt. Dadurch kann der Installer physisch nur die NVMe als Ziel auswählen.

## Noch offen

- internen Zustand und SATA-Caddy/Kabel prüfen
- zweite HDD einbauen und gemeinsam mit NVMe testen
- Onboard-Gigabit-LAN praktisch testen
- relevante USB-/Display-Ports testen
- Last-/Temperatur-/Lüftertest
- Wake-on-LAN und Power-Recovery
- Proxmox installieren
- Post-Install-Baseline für Netzwerk, Storage und Backups dokumentieren

## Fazit des Tages

Die Erstabnahme wurde bewusst **vor** dem Umbau durchgeführt. Das hat bereits zwei Diagnosefallen sichtbar gemacht — den irreführenden Windows-Produktnamen und die widersprüchlich wirkenden Virtualisierungs-WMI-Werte — ohne dass dabei die originale Installation oder der Lieferzustand verloren ging.


## Fortsetzung — Innenraum-Sichtprüfung

Vor dem Einbau des sekundären Datenträgers wurde der Tiny-PC stromlos geöffnet und die Oberseite fotografisch geprüft.

Ergebnis:

- 2,5-Zoll-Laufwerksbracket vorhanden und leer
- SATA-Flachbandkabel vorhanden und am vorgesehenen Mainboard-SATA-Anschluss angeschlossen
- Laufwerksanschluss im Bracket-Bereich vorhanden
- WLAN-Modul und Antennenverkabelung vorhanden
- Lüfter/Kühlmodul vollständig
- keine offensichtlichen Brandstellen, Korrosion, gebrochenen Stecker oder losen Kabel sichtbar
- nur leichte Staub-/Gebrauchsspuren

Damit ist die notwendige Hardware für den geplanten 2,5-Zoll-SATA-Einbau vorhanden. RAM und NVMe befinden sich auf der Unterseite des Tiny und waren für diesen Arbeitsschritt nicht zu öffnen; beide waren bereits zuvor softwareseitig verifiziert worden.
