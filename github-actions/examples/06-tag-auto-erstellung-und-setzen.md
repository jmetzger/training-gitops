# Tag automatisch erstellen und nächsten Schritt setzen 

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
