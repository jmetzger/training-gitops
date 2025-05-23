# Use schedule with variables 

```
name: Ein Job mit dynamischer Variable je nach Zeitplan

on:
  schedule:
    - cron: '0 8 * * 1'   # Montag 08:00 UTC
    - cron: '0 20 * * 5'  # Freitag 20:00 UTC

jobs:
  dynamic-message:
    runs-on: ubuntu-latest
    steps:
      - name: Setze MESSAGE je nach Zeitplan
        id: set-message
        run: |
          case "${{ github.event.schedule }}" in
            '0 8 * * 1')
              echo "message=Guten Morgen am Montag!" >> $GITHUB_OUTPUT
              ;;
            '0 20 * * 5')
              echo "message=Guten Abend am Freitag!" >> $GITHUB_OUTPUT
              ;;
            *)
              echo "message=Unbekannter Zeitplan" >> $GITHUB_OUTPUT
              ;;
          esac

      - name: Ausgabe der Nachricht
        run: echo "${{ steps.set-message.outputs.message }}"

```
