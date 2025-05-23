# Using a secret 

## welche repo:

  * Wieder repo fürs training z.B.
  * https://github.com/gittrainereu2/gitops-jochen/new/master?filename=.github%2Fworkflows%2Fmain.yml&workflow_template=blank


## Step 1: Secrets anlegen 

  * https://github.com/gittrainereu2/gitops-jochen/settings/secrets/actions



## Step 2: Secret verwenden 

```
# .github/workflows/blank.yml 
name: Use GitHub Secret

on:
  push:
    branches:
      - main

jobs:
  print-secret:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Use secret
        run: |
          echo "Using secret..."
          echo "Secret is set: [${{ secrets.MY_SECRET_TOKEN != '' }}]"

```
