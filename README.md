# App Ref. Card 01
Standalone Spring Boot Application

---
title: App Ref. Card 01
author: Rinaldo Lanza, BBW
date: 12. Februar 2023
---


Link zur Übersicht:<br/>
https://gitlab.com/bbwrl/m347-ref-card-overview


## Installation der benötigten Werkzeuge

Maven Tutorial for Beginners<br/>
https://www.simplilearn.com/tutorials/maven-tutorial


### Projekt bauen und starten
Die Ausführung der Befehle erfolgt im Projektordner.

Builden mit Maven:
```powershell
mvn clean package
```

Das Projekt wird gebaut und die Jar-Datei im Ordner `target` erstellt (Artefakt).
Die erstellte Datei kann nun direkt mit Java gestartet werden:
```powershell
java -jar target/app-refcard-01-0.0.1-SNAPSHOT.jar
```

Die App kann im Browser unter der URL `http://localhost:8080` betrachtet werden.


### Inbetriebnahme mit Docker Container
Docker Image lokal bauen:
```powershell
docker build -t app-refcard-01:latest .
```

Container starten:
```powershell
docker run --rm -p 8080:8080 --name app-refcard-01 app-refcard-01:latest
```

Danach ist die Web-Anwendung wieder unter `http://localhost:8080` erreichbar.


### GitHub CI/CD
Im Ordner `.github/workflows/` liegt der Workflow `ci-cd.yml`.
Er macht bei Push und Pull Request:
- Maven-Testlauf
- Docker-Hub-Image-Build und Push bei Push auf `main` oder `master`
- Push nach `ghcr.io` bei Push auf `main` oder `master`


### Benötigte Secrets auf GitHub
Lege in deinem Repository unter **Settings > Secrets and variables > Actions** diese Secrets an:
- `DOCKERHUB_USERNAME`
- `DOCKERHUB_TOKEN`

Für `ghcr.io` braucht der Workflow kein zusätzliches Secret; er nutzt `GITHUB_TOKEN`.


### Was du wann und wo tun sollst
1. **Lokal:** Projekt ändern, dann testen mit `mvn clean test`.
2. **GitHub:** Repository pushen.
3. **GitHub > Settings:** Docker-Hub-Secrets setzen.
4. **GitHub > Actions:** Workflow erfolgreich laufen lassen.
5. **Docker Hub:** Erfolgreichen Image-Upload screenshoten.
6. **Lokal:** Container mit `docker run` starten und `docker ps` screenshotten.
7. **Browser:** Webseite unter `http://localhost:8080` öffnen und screenshotten.
8. **GitHub Packages / ghcr.io:** Optionalen Upload dort ebenfalls screenshotten.


### Für die Abgabe benötigte Screenshots
- Erfolgreich durchgelaufener Workflow auf GitHub mit sichtbarem User, Repo und Datum
- Erfolgreicher Upload auf Docker Hub mit sichtbarem User, Image und Datum
- Laufender Container der Web-Site
- Geöffnete Web-Site im Browser
- Optional: erfolgreicher Upload auf `ghcr.io` mit sichtbarem User, Image und Datum


### Hinweise
Falls dein GitHub-Branch `main` nicht `master` heisst, passe den Workflow entsprechend an.
Falls dein Docker-Hub-Username anders lautet, ändere die Image-Namen im Workflow.
