# Work with secrets 

## Secret in der Gui festlegen 

 * SECRET_SUPER_SECRET

## Workflow 

```
name: secret 

on: [push]

jobs:
  job1:
    runs-on: ubuntu-latest
    steps:
      - name:  show secrets and env  
        shell: bash
        env:
          SUPER_SECRET: ${{ secrets.SECRET_SUPER_SECRET }}
          DAY: "monday"
        run: |
          echo "show env"
          echo "$DAY"
          echo "$SUPER_SECRET"
          echo "Show secret" 
          echo "${{ secrets.SECRET_SUPER_SECRET }}"
