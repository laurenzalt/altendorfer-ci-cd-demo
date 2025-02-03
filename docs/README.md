# Continuous Delivery Techdemo

Dieses Repository demonstriert eine CI/CD-Pipeline mit **GitHub Actions** und **Docker** zur Bereitstellung einer REST API.

## Projektstruktur

```
altendorfer-ci-cd-demo/
├── .github/              # GitHub Actions Workflows
├── src/                  # Haupt-Quellcode der REST API
├── test/                 # Tests für die API
├── Dockerfile            # Docker Image Konfiguration
├── docker-compose.yml    # Multi-Container Setup
├── .env.example          # Beispiel-Umgebungsvariablen
├── package.json          # Node.js Abhängigkeiten
├── CHECKLIST.md          # Prüfliste zur Entwicklung
└── README.md             # Diese Datei
```

## Einrichtung

### Voraussetzungen

- **Docker & Docker Compose**
- **Node.js & npm**
- **GitHub Account** (für CI/CD)

### Installation & Start

1. `.env`-Datei aus Vorlage erstellen:
   ```sh
   cp .env.example .env
   ```
2. Abhängigkeiten installieren:
   ```sh
   npm install
   ```
3. Anwendung lokal starten:
   ```sh
   docker-compose up --build
   ```

## CI/CD mit GitHub Actions

Das Repository nutzt **GitHub Actions** für:

- Automatische Tests & Linting
- Docker Image Build & Deployment

Workflows befinden sich in `.github/workflows/`.

## Tests ausführen

```sh
npm test
```

