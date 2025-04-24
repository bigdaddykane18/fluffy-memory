# Kristall-CI

Dieses Repository enthält die Konfiguration für Kristall-CI, einen Continuous Integration (CI) Workflow, der mit GitHub Actions für ein Projekt, das die Crystal Programmiersprache verwendet, eingerichtet ist.

## Workflow Übersicht

Der CI-Workflow wird ausgelöst, wenn Änderungen in den Branch `Hauptseite` gepusht oder Pull Requests gegen den `Hauptseite` Branch erstellt werden.

### Jobs

Der Workflow enthält einen Job namens `build`, der auf einem Ubuntu-Latest-Runner ausgeführt wird und einen Crystal Docker Container verwendet.

#### Schritte des `build` Jobs

1. **Checkout Code**: Der Code wird mit `actions/checkout@v4` ausgecheckt.
2. **Install Crystal**: Crystal wird in den Versionen 0.35.1, latest und nightly mittels `crystal-lang/install-crystal@v1` installiert.
3. **Cache Dependencies**: Abhängigkeiten werden gecacht, um die Build-Zeit zu verbessern.
4. **Install Dependencies**: Abhängigkeiten werden mit `shards install` installiert.
5. **Run Tests**: Tests werden mit `crystal spec` ausgeführt.
6. **Upload Test Results**: Testergebnisse werden als Artefakte hochgeladen.
7. **Download Test Results**: Testergebnisse werden heruntergeladen und lokal gespeichert.

### Konfigurationsdateien

- `.github/workflows/crystal.yml`: Enthält die Konfiguration des GitHub Actions Workflows.

## Lokale Entwicklung

Um dieses Projekt lokal zu entwickeln, stellen Sie sicher, dass Sie Crystal und Shards installiert haben. Sie können Abhängigkeiten installieren und Tests lokal mit den folgenden Befehlen ausführen:

```bash
shards install
crystal spec
