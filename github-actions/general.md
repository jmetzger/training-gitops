# General 

## Komponenten 

  * workflows 
  * jobs
  * steps
  * events
  * actions

## Workflows 

  * ENV (Umgebungsvariablen, Variablen) 
  * Jobs -> Steps 
  * Events

## Events 

  * Events sind Ereignisse die stattfinden (man könnte auch sagen -> Trigger)
  * Ref: https://docs.github.com/en/actions/using-workflows/events-that-trigger-workflows

### Beispiele für Typen von Events  

  * pull_request
    * if no activity types are specified, the workflow runs when a pull request is opened or reopened or when the head branch of the pull request is updated
   
## Actions 

  * Bei einer **action** handelt es sich um eine benutzerdefinierte Anwendung für die GitHub Actions-Plattform zur Ausführung einer komplexen und häufig ausgeführten Aufgabe
  * Beispiele von **actions** in github actions


| Action                      | Zweck                                                                   |
| --------------------------- | ----------------------------------------------------------------------- |
| `actions/checkout`          | Checkt den Repository-Code aus, um damit arbeiten zu können             |
| `actions/setup-node`        | Installiert Node.js in einer bestimmten Version                         |
| `actions/setup-python`      | Installiert Python in einer bestimmten Version                          |
| `actions/setup-java`        | Installiert Java / JDK                                                  |
| `actions/cache`             | Caching von Abhängigkeiten (z. B. `node_modules`) für schnellere Builds |
| `actions/upload-artifact`   | Speichert Build-Ergebnisse (z. B. Testberichte)                         |
| `actions/download-artifact` | Lädt gespeicherte Artefakte in späteren Jobs                            |
| `docker/build-push-action`  | Baut und pusht ein Docker-Image zu DockerHub oder GHCR                  |
| `github/codeql-action/init` | Startet CodeQL-Analyse für Sicherheitsscans                             |
| `actions/github-script`     | Führt beliebige JavaScript-Befehle mit Zugriff auf das GitHub-API aus   |

  * Beispiele von von github actions aus der community

| Action                                 | Zweck                                                     |
| -------------------------------------- | --------------------------------------------------------- |
| `peter-evans/create-pull-request`      | Erstellt automatisch PRs, z. B. für aktualisierte Konfigs |
| `JamesIves/github-pages-deploy-action` | Deployment auf GitHub Pages                               |
| `Azure/k8s-deploy`                     | Deployment zu Kubernetes (AKS etc.)                       |
| `softprops/action-gh-release`          | Erstellt Releases inkl. Assets in GitHub                  |

 

