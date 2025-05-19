# Was ist CI/CD ? 

## Allgemein 

**CI/CD** steht für **Continuous Integration** und **Continuous Delivery** bzw. **Continuous Deployment** – zwei zentrale Konzepte in der modernen Softwareentwicklung.

---

### 🧪 **CI – Continuous Integration**

> Automatisches Testen und Zusammenführen von Code-Änderungen.

* Entwickler\:innen arbeiten gemeinsam am Code.
* Sobald jemand etwas „pusht“, wird automatisch geprüft:

  * Funktioniert der Code? (z. B. durch Unit Tests)
  * Lässt sich das Projekt bauen (Build)?
* Ziel: Fehler frühzeitig erkennen, weniger Integrationstress.

---

### 🚀 **CD – Continuous Delivery / Deployment**

#### 1. **Continuous Delivery**

> Der Code ist jederzeit bereit für ein manuelles Deployment.

* Nach erfolgreich bestandenem CI-Prozess wird der Code automatisch „bereitgestellt“, z. B. als Docker-Image.
* Das Deployment erfolgt per Knopfdruck oder Approval.

#### 2. **Continuous Deployment**

> Noch ein Schritt weiter: Änderungen gehen automatisch live, sobald sie durch die Tests kommen.

* Vollständige Automatisierung bis zum Produktionssystem.
* Typisch für Microservices und Cloud-native Architekturen.

---

### 📦 Beispiel in GitHub Actions

Ein typischer CI/CD-Workflow:

```yaml
on: push
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: npm install
      - run: npm test

  deploy:
    needs: test
    runs-on: ubuntu-latest
    steps:
      - run: echo "Deploying to production..."
```

---

