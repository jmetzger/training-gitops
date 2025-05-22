# Tag automatisch erstellen und nächsten Schritt setzen 

## Vorbereitung 

  * Der GITHUB_TOKEN wird von Github automatisch erstellt, aber du musst dafür Sorge tragen, dass die Schreibrechte auch im Workflow möglich sind

🔍 Prüfe:

Gehe zu Repository → Settings → Actions → General
Scrolle zu "Workflow permissions"

Wähle:
✅ Read and write permissions

![image](https://github.com/user-attachments/assets/b25fdbbc-f8ea-4430-a0ac-46cc5fa00c69)



## Beispiel 1: 

```
name: Automatischer Tag

on: [push]

jobs:
  version-erzeugen:
    runs-on: ubuntu-latest
    outputs:
      version: ${{ steps.create_version.outputs.version }}
    steps:
      - name: Erzeuge Versionsnummer
        id: create_version
        run: |
          VERSION="v$(date +'%Y.%m.%d-%H%M')"
          echo "version=$VERSION" >> $GITHUB_OUTPUT

  tag-setzen:
    needs: version-erzeugen
    runs-on: ubuntu-latest
    steps:
      - name: Checke Repo aus
        uses: actions/checkout@v4

      - name: Setze Git-Tag und pushe
        env:
          TAG_NAME: ${{ needs.version-erzeugen.outputs.version }}
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        run: |
          git config user.name "github-actions"
          git config user.email "github-actions@github.com"
          git tag "$TAG_NAME"
          git push origin "$TAG_NAME"
```
