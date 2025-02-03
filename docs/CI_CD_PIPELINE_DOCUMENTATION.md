# CI/CD Pipeline Dokumentation

Dieses Dokument beschreibt die CI/CD-Pipeline, die in diesem Projekt mit GitHub Actions umgesetzt wird.

## Übersicht

Die Pipeline umfasst folgende Hauptschritte:
1. **Lint:**  
   Code-Qualitätsprüfung mit ESLint.
2. **Test:**  
   Ausführung der Unit-Tests und Erfassung der Test-Coverage.
3. **Audit:**  
   Sicherheitsüberprüfung der Abhängigkeiten mittels `npm audit`.
4. **Docker Build & Push:**  
   Erstellung eines Docker-Images und Upload in ein Docker Registry.
5. **Deployment & Security Scan:**  
   - **Deployment:** (Option A – lokales Deployment auf dem Runner; Option B – Remote-Deployment auf einem echten Server)  
   - **Security Scan:** Durchführung eines OWASP ZAP Scans auf der bereitgestellten Anwendung.

## Pipeline Flowchart
![Pipeline](/docs/screenshots/Screenshot%202025-02-03%20181032.png)

## Verwendete Tools und Aktionen
- GitHub Actions
- Wichtige Actions:
  - `actions/checkout@v3`
  - `actions/setup-node@v3`
  - `actions/cache@v3`
  - `docker/login-action@v2`
  - `appleboy/ssh-action@v0.1.5`
  - `actions/upload-artifact@v4`
- Docker
- OWASP ZAP

## Konfigurationen
- GitHub Secrets: 
  - `DOCKER_USERNAME` & `DOCKER_PASSWORD` für den Zugriff auf das Docker Registry
  - `DIGITALOCEAN_IP`, `DIGITALOCEAN_SSH_KEY` und `DIGITALOCEAN_USER` für Deployment

# Zusammenfassung der Pipeline-Schritte

## Lint Job

- Repository auschecken
- Node.js einrichten
- Caching des `node_modules`-Ordners
- Abhängigkeiten installieren
  (Befehl: `npm install`)
- Ausführen von ESLint
  (Befehl: `npm run lint`)

## Test Job

- Repository auschecken
- Node.js einrichten
- Caching des `node_modules`-Ordners
- Abhängigkeiten installieren
- Ausführen der Tests
  (Befehl: `npm test`)
- Optional:** Ausführen der Coverage-Tests  
  (Befehl: `NODE_ENV=test npm run coverage`)
- Upload des Coverage-Reports als Artefakt

## Audit Job

- Repository auschecken
- Node.js einrichten
- Caching des `node_modules`-Ordners
- Abhängigkeiten installieren
- Ausführen von npm audit
  (Befehl: `npm audit --audit-level=moderate`)

## Docker Build & Push Job

- Repository auschecken
- Anmeldung beim Docker Registry
- Docker-Image bauen:
  ```bash
  docker build -t <DOCKER_USERNAME>/ci-cd-demo:${{ github.sha }} .
  ```

## Deployment (Remote oder Lokal)
- Remote-Deployment:
  
  Verbindung zum Zielserver via SSH herstellen, das neue Image pullen, eventuell alten Container stoppen und den neuen Container starten.
- Lokales Deployment auf dem Runner:

    Der Container wird direkt gestartet, um die Anwendung temporär verfügbar zu machen.

## Security Scan
- Sicherstellen, dass die Anwendung über die definierte URL erreichbar ist.
- Installation von OWASP ZAP (zum Beispiel über Snap).
- Durchführung des Quick-Scans:
  ```bash
  zaproxy -cmd -quickurl http://<DIGITALOCEAN_IP> -quickout /tmp/zap-report.html
  ```
