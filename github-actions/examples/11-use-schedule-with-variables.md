# Use schedule with variables 

## Remark 

  * In the free version, this is not exact
  * Scheduled jobs on private only if they are starred or in other plan 

## Exercise 

  * Anpassen auf die aktuelle Zeit (Fall 1 in 2 Minute, Falls in 4 minuten)

```
name: Ein Job mit dynamischer Variable je nach Zeitplan

on:
  schedule:
    - cron: '*/5 * * * *'   # alle 5 Minuten 
    - cron: '* * * * *'  # jede Minute 

jobs:
  dynamic-message:
    runs-on: ubuntu-latest
    steps:
      - name: Setze MESSAGE je nach Zeitplan
        id: set-message
        run: |
          case "${{ github.event.schedule }}" in
            '*/5 * * * *')
              echo "message=Guten Morgen am Montag!" >> $GITHUB_OUTPUT
              ;;
            '* * * * *')
              echo "message=Guten Abend am Freitag!" >> $GITHUB_OUTPUT
              ;;
            *)
              echo "message=Unbekannter Zeitplan" >> $GITHUB_OUTPUT
              ;;
          esac

      - name: Ausgabe der Nachricht
        run: echo "${{ steps.set-message.outputs.message }}"

```
