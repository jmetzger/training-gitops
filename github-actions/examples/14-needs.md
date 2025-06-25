# Stages mit und ohne needs 

## Beispiel ohne needs 

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
