# Deploy with ssh 

## Deploying to server (without additional 

on:
  push:
    branches:
      - main
  workflow_dispatch:
  
jobs:
  run_pull:
    name: run pull
    # That is the image we are running on 
    runs-on: ubuntu-latest
    
    steps:
    - name: install ssh keys
      # check this thread to understand why its needed:
      # https://stackoverflow.com/a/70447517
      run: |
        install -m 600 -D /dev/null ~/.ssh/id_rsa
        echo "${{ secrets.SSH_PRIVATE_KEY }}" > ~/.ssh/id_rsa
        ssh-keyscan -H ${{ secrets.SSH_HOST }} > ~/.ssh/known_hosts
    - name: connect and pull
      run: ssh ${{ secrets.SSH_USER }}@${{ secrets.SSH_HOST }} "cd ${{ secrets.WORK_DIR }} && git checkout ${{ secrets.MAIN_BRANCH }} && git pull && exit"
    - name: cleanup
      run: rm -rf ~/.ssh

```

## Requirements (OLD VERSION from here) 

```
# apache is installed with php 
# ssh runs 
# DocumentRoot /var/www/html 

```

## Steps 

```
Step 1:
=======
Auf Zielsystem (Webserver) public / private key erstellt 
und pub-key in authorized_keys eingetragen.

cd /root/.ssh 
# Achtung bitte rsa und 4096 nehmen, Beschreibung von github
# zum Erstellen eines pub/private keys funktioniert für github runner nicht 
ssh-keygen -t rsa -b 4096 -C "foo@foo.com"
cat github-actions.pub >> authorized_keys
# Kopieren dieses Inhalt in die Secrets des repositories, von dem aus
# ihr deployen wollt 
cat github-actions

Step 2: Eintrag in die Secretes 
=======
# Repository -> Settings -> Secrets -> Actions -> New Secret for Repo 
SSH_PRIVATE_KEY 
# Hier dann der Wert von github-actions 

# Host (IP Eintragen) 
SSH_HOST 

Step 3: Workflow einrichten in Repo unter 
.github/workflows/deinworkflow.yml 

# This is a basic workflow to help you get started with Actions

name: Jochen's nicer workflow 

# Controls when the workflow will run
on:
  # Triggers the workflow on push or pull request events but only for the master branch
  push:
    branches: [ master ]
  pull_request:
    branches: [ master ]

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:
  # This workflow contains a single job called "build   
    
  deploy:
    
    # needs a succesful build 
    needs: build 
    runs-on: ubuntu-latest 
    
    env:
    # Beispiel, jedoch nicht notwendig 
      SSH_PRIVATE_KEY: ${{ secrets.SSH_PRIVATE_KEY }}
     

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:
      # Checks-out your repository under $GITHUB_WORKSPACE, so your job can access it
      - uses: actions/checkout@v2

      # Runs a single command using the runners shell
      - name: Starting the deploy 
        run: | 
          echo "starting the deployment process" 
          ls -la
      - name: Install SSH Key 
        uses: shimataro/ssh-key-action@v2
        with: 
          key: ${{ secrets.SSH_PRIVATE_KEY }}
          known_hosts: 'placeholder'
      - name: Adding Known Hosts  
        run: ssh-keyscan -H ${{ secrets.SSH_HOST }} >> ~/.ssh/known_hosts  
      - name: Show known hosts 
        run: ls -la ~/.ssh/known_hosts 
      - name: synchronize 
        run: rsync -avz ./dist root@${{ secrets.SSH_HOST }}:/var/www/html/ 

## Schritt 3: Testen und debuggen 

```
## Ref: 

  * https://zellwk.com/blog/github-actions-deploy/
  
