# Stages mit und ohne needs 

## Beispiel ohne needs 

  * alle stages (jobs) laufen parallel 

```
name: Ohne needs

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: |
          echo "🔨 Baue etwas"
          sleep 30 

  test:
    runs-on: ubuntu-latest
    steps:
      - run: |
          echo "✅ Teste etwas"
          sleep 30

  deploy:
    runs-on: ubuntu-latest
    steps:
      - run: |
          echo "🚀 Deploy"
          sleep 30 
```


## Beispiel mit needs 

  * Erst wenn das need erfüllt ist, kann der nächste Job gestartet werden

```
name: Mit needs

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: |
          echo "🔨 Baue etwas"
          sleep 30 

  test:
    needs: build 
    runs-on: ubuntu-latest
    steps:
      - run: |
          echo "✅ Teste etwas"
          sleep 30

  deploy:
    needs: [test]
    runs-on: ubuntu-latest
    steps:
      - run: |
          echo "🚀 Deploy"
          sleep 30 



```

## Beispiel weitermachen (auch bei Fehler) 

```
name: Mit needs

on: [push]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - run: |
          xecho "🔨 Baue etwas"
          sleep 30 

  test:
    if: always()
    needs: build 
    runs-on: ubuntu-latest
    steps:
      - run: |
          echo "✅ Teste etwas"
          sleep 30

  deploy:
    needs: [test]
    runs-on: ubuntu-latest
    steps:
      - run: |
          echo "🚀 Deploy"
          sleep 30 
```

