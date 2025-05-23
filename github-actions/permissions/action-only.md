# Nur bestimmte teams oder Nutzer dürfen den Workflow starten 

## Protected environments 

### Baustein 1

  * Stichwort: Specific environment 

```
name: Deploy

on:
  workflow_dispatch:  # Manual trigger only

jobs:
  deploy:
    name: Restricted Deploy
    runs-on: ubuntu-latest
    environment:
      name: production  # Must match the protected environment in repo settings
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Deploy step
        run: echo "Deploying to production..."
```


### Baustein 2: Environment anlegen 

![image](https://github.com/user-attachments/assets/644d2bd7-7d22-4126-a15b-17c74a5f6b74)

![image](https://github.com/user-attachments/assets/d24063cc-660c-45a3-9b0d-1be0884194d8)

### Frage: Wer darf den Workflow ausführen ?

  * Keiner ohne Schreibrechte kann den Workflow triggern
  * Und nur festgelegte review können approven und den workflow from Action Tab startet 
