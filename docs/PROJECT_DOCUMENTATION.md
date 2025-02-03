# Projekt-Dokumentation

## Projektübersicht

**Beschreibung:**  
Dieses Projekt ist eine Node.js-basierte Anwendung, mit ein paar simplen Endpunkten. Die Anwendung nutzt Express für die Serverlogik, Sequelize für den Datenbankzugriff und Swagger zur API-Dokumentation. Zu den Hauptfunktionen gehören unter anderem:

- Bereitstellung eines Health-Checks über `/health`
- Verwaltung von Nutzern über die Endpunkte unter `/api/users`
- Automatisierte Tests, Sicherheitsüberprüfungen und Container-Builds via CI/CD

## Verwendete Technologien und Tools

- **Programmiersprache:** Node.js (JavaScript)
- **Framework:** Express
- **Datenbank:** SQLite (über Sequelize)
- **API-Dokumentation:** Swagger (OpenAPI 3.0)
- **Containerisierung:** Docker
- **CI/CD:** GitHub Actions
- **Code-Qualität:** ESLint, npm audit
- **Testing:** Unit-Tests (z. B. Jest oder Mocha), Code Coverage Tools


## Einrichtung und Installation

### Voraussetzungen

- Node.js (v18 oder höher)
- Docker (für containerbasierte Deployments)
- Git

### Lokale Einrichtung

1. Repository klonen:
   ```bash
   git clone https://github.com/laurenzalt/altendorfer-ci-cd-demo.git
   ```
2. Ins Projektverzeichnis wechseln:
    ```bash
    cd altendorfer-ci-cd-demo
    ```
3. Abhängigkeiten installieren:
    ```bash
    npm install
    ```
 4. Anwendung starten:
    ```bash
    npm start
    ```
5. API-Dokumentation ansehen:
   
    Öffne im Browser http://localhost:3000/api-docs

  