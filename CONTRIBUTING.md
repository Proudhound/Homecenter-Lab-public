# Contributing to HomeCenter Lab Public

[Deutsch](#deutsch) · [English](#english)

## Deutsch

Danke für dein Interesse an HomeCenter Lab Public. Beiträge sind willkommen, wenn sie das Projekt nachvollziehbarer, sicherer, nützlicher oder besser reproduzierbar machen.

HomeCenter Lab Public ist die bewusst bereinigte Veröffentlichungsschicht eines real betriebenen privaten Home-Labs. Deshalb gilt neben technischer Qualität ein besonders strenges **Publication Security Gate**.

### Was willkommen ist

Geeignete Beiträge sind insbesondere:

- Verbesserungen und Korrekturen der Dokumentation
- Fehlerkorrekturen
- reproduzierbare Home-Assistant-Beispiele und Automationen
- Verbesserungen an Architektur-, Backup-, Netzwerk- und Security-Konzepten
- sinnvolle Integrationsvorschläge
- nachvollziehbare Hardware-Erfahrungen und Kompatibilitätshinweise
- Local-first-, Energie-, Monitoring-, KI- und Voice-Ansätze
- Verbesserungen an Beispielen, Diagrammen und Anleitungen

Nicht geeignet sind insbesondere:

- Zugangsdaten, Secrets, Tokens oder Schlüssel
- reale private IP- oder MAC-Adressen
- Seriennummern oder eindeutige private Gerätekennungen
- interne Hostnamen oder private DNS-Namen
- exakte private Sicherheits- oder Kamerapositionen
- private Kameraaufnahmen oder Snapshots
- personenbezogene Haushalts-, Familien- oder Standortdaten
- ungeprüfte Copy-Paste-Konfigurationen ohne Kontext
- Inhalte, für deren Veröffentlichung keine Rechte bestehen

### Bevor du beginnst

**Kleine Änderungen** wie Tippfehler, kaputte Links oder eindeutig begrenzte Dokumentationskorrekturen können direkt als Pull Request eingereicht werden.

Bitte eröffne **vor größeren Änderungen ein Issue**, insbesondere bei:

- neuen Funktionen oder Integrationen
- Architekturänderungen
- größeren Automationen
- neuen Abhängigkeiten
- Hardwareempfehlungen mit Auswirkungen auf die Zielarchitektur
- Änderungen an Security-, Privacy- oder Publication-Regeln
- umfangreichen Umstrukturierungen der Dokumentation

So kann vor der Umsetzung geklärt werden, ob die Änderung zur Roadmap und zu den Projektprinzipien passt.

### Grundprinzipien

Beiträge sollten die Projektprinzipien respektieren:

1. **Family first** – konkreter Alltagsnutzen vor Technik um der Technik willen.
2. **Local first** – lokale Verarbeitung bevorzugen, wenn sinnvoll.
3. **Integrate before replace** – funktionierende Systeme zuerst integrieren.
4. **Manual control survives** – grundlegende Hausfunktionen bleiben unabhängig bedienbar.
5. **Security by publication design** – veröffentlichte Inhalte dürfen die reale private Infrastruktur nicht unnötig offenlegen.
6. **Reproducible where possible** – Beispiele sollen verständlich und nachbaubar sein.
7. **Deterministic safety** – sicherheitskritische Funktionen dürfen nicht allein von LLMs oder externen KI-Diensten abhängen.

### Sprache

Deutsch ist die bevorzugte Projektsprache. Englische Issues und Pull Requests sind ebenfalls willkommen.

Kerninhalte sollen langfristig deutsch und englisch verfügbar sein. Ein Beitrag muss jedoch nicht zwingend bereits beide Sprachversionen enthalten. Übersetzungen können getrennt ergänzt werden.

### Dokumentationsstandard

Dokumentationsbeiträge sollten:

- aussagekräftige Überschriften verwenden
- Voraussetzungen nennen
- Befehle und Konfigurationen kopierbar darstellen
- relevante Software-/Hardwareversionen nennen, wenn das Verhalten versionsabhängig ist
- Annahmen und Grenzen kenntlich machen
- getestete und ungetestete Aussagen unterscheiden
- Screenshots nur verwenden, wenn sie einen tatsächlichen Mehrwert bieten
- keine sensiblen Informationen enthalten

### Publication Security Gate

Vor jedem Pull Request und vor jedem Merge muss geprüft werden, ob versehentlich sensible Informationen enthalten sind.

Prüfe insbesondere auf:

- IP-Adressen
- MAC-Adressen
- Seriennummern
- eindeutige Geräte-IDs
- interne Hostnamen
- WLAN-Daten
- API-Keys
- Tokens
- Passwörter
- VPN-Schlüssel
- Recovery-Secrets
- interne Dateipfade mit personenbezogenen Informationen
- Standortinformationen
- private Kamera- oder Sicherheitsdetails
- personenbezogene Daten

Für technische Beispiele sollen Dokumentationsbereiche wie `192.0.2.0/24`, `198.51.100.0/24` oder `203.0.113.0/24` und generische Namen wie `SERVER-01`, `HA-VM` oder `NAS-01` verwendet werden.

**Im Zweifel wird eine Information nicht veröffentlicht.**

Wenn du glaubst, bereits veröffentlichte Inhalte enthielten sensible Informationen, wiederhole diese Daten nicht vollständig in einem öffentlichen Issue. Siehe [SECURITY.md](SECURITY.md).

### Pull-Request-Workflow

1. Repository forken und einen eigenen Branch erstellen.
2. Änderung möglichst klein und thematisch klar halten.
3. Dokumentation, Beispiele und gegebenenfalls Tests aktualisieren.
4. Publication Security Gate durchführen.
5. Pull Request mit verständlicher Beschreibung eröffnen.
6. Review-Kommentare bearbeiten.
7. Merge erfolgt nach Maintainer-Review.

Externe Beiträge werden nicht direkt auf `main` geschrieben.

Ein Pull Request begründet keinen Anspruch auf Übernahme. Änderungen können aus Gründen von Scope, Architektur, Sicherheit, Wartbarkeit oder Roadmap abgelehnt oder für später zurückgestellt werden.

### Commits

Es gibt derzeit keinen verpflichtenden Commit-Standard. Commit-Nachrichten sollen jedoch kurz und verständlich beschreiben, **was** geändert wurde.

Beispiele:

```text
docs: clarify Proxmox backup prerequisites
fix: correct Home Assistant example
feat: add generic UPS shutdown concept
```

### Lizenzierung von Beiträgen

Code in diesem Repository steht grundsätzlich unter der [MIT License](LICENSE).

Dokumentation steht, soweit nicht anders gekennzeichnet, unter [CC BY 4.0](LICENSE-DOCS).

Mit dem Einreichen eines Beitrags bestätigst du, dass du berechtigt bist, diesen Inhalt beizutragen, und dass dein Beitrag unter der jeweils für den betroffenen Repository-Bereich geltenden Lizenz veröffentlicht werden darf.

Für das Projekt ist derzeit kein Contributor License Agreement (CLA) erforderlich.

### Verhalten

Sachliche Diskussion, konstruktive Kritik und unterschiedliche technische Ansätze sind ausdrücklich willkommen. Persönliche Angriffe, Belästigung, Diskriminierung, Spam oder absichtlich irreführende Beiträge werden nicht akzeptiert.

---

## English

Thank you for your interest in HomeCenter Lab Public. Contributions are welcome when they make the project safer, clearer, more useful or more reproducible.

HomeCenter Lab Public is a deliberately sanitized public layer of a real private home lab. Technical quality therefore goes hand in hand with a strict **Publication Security Gate**.

### Welcome contributions

Examples include:

- documentation improvements and corrections
- bug fixes
- reproducible Home Assistant examples and automations
- architecture, backup, networking and security improvements
- useful integration proposals
- reproducible hardware experience and compatibility notes
- local-first, energy, monitoring, AI and voice concepts
- improvements to examples, diagrams and guides

Do not submit credentials, secrets, real private IP/MAC addresses, serial numbers, private hostnames, precise security-device locations, camera footage, personal household/location data, unverified copy-paste configurations or material you do not have the right to publish.

### Before starting

Small fixes may be submitted directly as a pull request.

For substantial features, integrations, architecture changes, dependencies, security/privacy changes, hardware proposals affecting the target architecture or major documentation restructuring, please open an issue first.

### Project principles

Contributions should respect:

1. Family first
2. Local first
3. Integrate before replace
4. Manual control survives
5. Security by publication design
6. Reproducible where possible
7. Deterministic safety for critical functions

### Language

German is the preferred project language. English issues and pull requests are welcome.

Core documentation should gradually become bilingual, but contributors are not required to provide both languages in every contribution.

### Documentation standard

State prerequisites, use copyable commands, identify relevant versions where needed, distinguish tested from untested claims, explain limitations and never include sensitive data.

### Publication Security Gate

Before submitting or merging, check for IP/MAC addresses, serial numbers, unique device IDs, internal hostnames, credentials, tokens, keys, recovery secrets, personal file paths, location information and private camera/security details.

Use documentation ranges such as `192.0.2.0/24`, `198.51.100.0/24` or `203.0.113.0/24`, and generic names such as `SERVER-01`, `HA-VM` and `NAS-01`.

**When in doubt, do not publish the information.**

See [SECURITY.md](SECURITY.md) for sensitive disclosures.

### Pull request workflow

1. Fork the repository and create a dedicated branch.
2. Keep the change focused.
3. Update documentation/examples/tests where relevant.
4. Perform the Publication Security Gate.
5. Open a pull request with a clear explanation.
6. Address review feedback.
7. Merge follows maintainer review.

External contributors do not push directly to `main`. Submission does not guarantee acceptance; changes may be declined or deferred for scope, architecture, security, maintenance or roadmap reasons.

### Licensing

Code is generally licensed under the [MIT License](LICENSE). Documentation is generally licensed under [CC BY 4.0](LICENSE-DOCS).

By submitting a contribution, you confirm that you have the right to contribute it and agree that it may be distributed under the applicable repository license.

No Contributor License Agreement (CLA) is currently required.

### Conduct

Constructive technical discussion and disagreement are welcome. Personal attacks, harassment, discrimination, spam and intentionally misleading contributions are not.
