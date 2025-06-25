# Build jar and deploy to ssh 

## Step 1: Neues Repo in gittrainereu / gittrainereu2 durch import  

  
  * mit beliebigen Namen: jm-sein-java 
  * https://github.com/yhayashi30/maven-jar-sample.git

## Step 2: Workflow erstellen 

```
name: Build and Deploy Aya GlassFish Jar

on:
  push:
    branches:
      - main

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Set up JDK 17
        uses: actions/setup-java@v4
        with:
          java-version: '17'
          distribution: 'temurin'

      - name: Build JAR with Maven
        run: mvn clean package

      - name: Copy JAR to Aya-GlassFish via SCP
        run: |
          ls -la
          cd target
          ls -la 

```

## Step 3: adding scp 

```
name: Build and Deploy Aya GlassFish Jar

on:
  push:
    branches:
      - main

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Set up JDK 17
        uses: actions/setup-java@v4
        with:
          java-version: '17'
          distribution: 'temurin'

      - name: Build JAR with Maven
        run: mvn clean package

      - name: Copy JAR to Aya-GlassFish via SCP
        uses: appleboy/scp-action@v1
        with:
          host: 161.35.74.206
          username: tln1
          key: ${{ secrets.SSH_PRIVATE_KEY }}
          port: 22
          source: "target/*.jar"
          target: "/home/tln1/"

```
