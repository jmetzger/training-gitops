# Using a secret 

## welche repo:

  * Wieder repo fürs training z.B.
  * https://github.com/gittrainereu2/gitops-jochen/new/master?filename=.github%2Fworkflows%2Fmain.yml&workflow_template=blank

  * Settings -> Security -> Secrets and varialbles  -> Actions
    * New repository secret
    * MY_SECRET_TOKEN

![image](https://github.com/user-attachments/assets/17bd0dbd-4c70-45a8-ac98-6e09a3184cab)


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
          echo "${{secrets.MY_SECRET_TOKEN}}" 
          echo "Secret is set: [${{ secrets.MY_SECRET_TOKEN != '' }}]"

```
