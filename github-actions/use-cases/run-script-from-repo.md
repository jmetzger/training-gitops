# Run script from rep 

## Step 1: Create script in repo 

```
# scripts/deploy.sh
```

```
#!/bin/bash 

echo "test this" 
env
echo $GITHUB_OUTPUT 
echo "VORNAME=Hans" >> $GITHUB_OUTPUT
```

## Step 2: .github/workflows/blank.yml

```
name: CI

# Controls when the workflow will run
on:
  # Triggers the workflow on push or pull request events but only for the "master" branch
  push:
    branches: [ "master" ]

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:
  
# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:
  run-playbooks:
    runs-on: ubuntu-latest
    steps: 
      - uses: actions/checkout@v4
      - name: run deploy 
        shell: bash
        run: |
         cd scripts
         chmod u+x ./deploy.sh
         ./deploy.sh 
```


## Step 3: Script ändern (jetzt mit Rückgabefehler) 

```
# scripts/deploy.sh
```

```
#!/bin/bash 

echo "test this" 
env
echo $GITHUB_OUTPUT 
echo "VORNAME=Hans" >> $GITHUB_OUTPUT
exit 1
```
