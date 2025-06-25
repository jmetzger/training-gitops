# Was kann github actions ? 

GitHub Actions ist eine sehr leistungsfähige CI/CD- und Automatisierungsplattform direkt in GitHub integriert. Du kannst damit so ziemlich alles automatisieren, was mit deinem Code zu tun hat. Hier sind die wichtigsten **Features** und **Möglichkeiten**:

---

### 🚀 **Kern-Features von GitHub Actions**

| Feature                                     | Beschreibung                                                                                          |
| ------------------------------------------- | ----------------------------------------------------------------------------------------------------- |
| **Workflows**                               | YAML-basierte Automatisierungen, die auf Events wie `push`, `pull_request` oder `schedule` reagieren. |
| **Jobs & Steps**                            | Workflows bestehen aus Jobs (z. B. "build", "deploy"), die wiederum aus Steps bestehen.               |
| **Self-hosted & GitHub-hosted Runner**      | Du kannst eigene Runner verwenden oder die von GitHub bereitgestellten virtuellen Maschinen.          |
| **Matrix Builds**                           | Erlaubt dir, Tests parallel mit verschiedenen Parametern laufen zu lassen (z. B. Node-Versionen, OS). |
| **Secrets & Umgebungsvariablen**            | Verwaltung sensibler Daten wie API-Keys sicher innerhalb von Repos/Organisationen.                    |
| **Artifact Handling**                       | Build-Artefakte speichern, herunterladen oder zwischen Jobs teilen.                                   |
| **Caching**                                 | Caching von z. B. `npm install` oder `pip`-Dependencies zur Beschleunigung von Builds.                |
| **Reusable Workflows**                      | Wiederverwendbare Workflows via `workflow_call`.                                                      |
| **Manueller Trigger (`workflow_dispatch`)** | Starte Workflows manuell – auch mit Formularfeldern (Inputs).                                         |
| **Scheduled Workflows (`schedule`)**        | Cron-basierte Zeitsteuerung.                                                                          |
| **Docker Support**                          | Docker-Container können direkt gebaut, gepusht und genutzt werden.                                    |
| **Matrix Builds**                           | Automatische Variation von Builds durch definierte Matrix-Werte.                                      |
| **Integration mit GitHub APIs**             | Durch `gh` CLI oder REST/GraphQL APIs.                                                                |
| **Marketplace Actions**                     | Tausende vorgefertigte Actions im [GitHub Marketplace](https://github.com/marketplace?type=actions).  |

---

### 💡 **Typische Anwendungsfälle / Möglichkeiten**

| Bereich                      | Beispiele                                                                     |
| ---------------------------- | ----------------------------------------------------------------------------- |
| **Build & Test**             | Automatisches Bauen und Testen von Code bei jedem Push/PR.                    |
| **Deployments**              | Automatisierte Deployments zu Cloud-Anbietern (AWS, Azure, GCP, Vercel etc.). |
| **Release-Automatisierung**  | Tags erstellen, Releases publishen, Changelogs generieren.                    |
| **Code-Qualität**            | Linting, Formatierung, statische Codeanalyse, Security-Scans.                 |
| **CI/CD**                    | Komplette CI/CD-Pipelines für Webservices, Microservices etc.                 |
| **Issue- und PR-Automation** | Automatisches Labeln, Kommentieren, Zuweisen.                                 |
| **Cron-Jobs**                | Regelmäßige Aufgaben (z. B. tägliche Backups, Cleanup-Skripte).               |
| **Container Management**     | Docker-Images bauen, testen und in Registries pushen.                         |
| **Monorepo Management**      | Selektives Ausführen von Tests/Builds abhängig vom betroffenen Verzeichnis.   |
| **Multi-Repo Workflows**     | Controller-Repositories, Trigger über `repository_dispatch`.                  |

---

### ✅ Vorteile von GitHub Actions

* Keine externe CI/CD-Plattform notwendig
* Nahtlose GitHub-Integration
* Pay-as-you-go auf GitHub-hosted Runners
* Sehr flexibel dank Shell, Docker, eigene Actions
* Open-Source Marketplace mit riesiger Auswahl

---


