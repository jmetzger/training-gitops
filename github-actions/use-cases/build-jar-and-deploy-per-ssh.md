# Build jar and deploy to ssh 

## Step 1: Neues Repo in gittrainereu / gittrainereu2 durch import  

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
        uses: actions/checkout@v3

      - name: Set up JDK 17
        uses: actions/setup-java@v3
        with:
          java-version: '17'
          distribution: 'temurin'

      - name: Build JAR with Maven
        run: mvn clean package

```



```
      - name: Copy JAR to Aya-GlassFish via SCP
        uses: appleboy/scp-action@v1
        with:
          host: ${{ secrets.SCP_HOST }}
          username: ${{ secrets.SCP_USER }}
          key: ${{ secrets.SSH_PRIVATE_KEY }}
          port: 22
          source: "target/*.jar"
          target: "/opt/aya-glassfish/glassfish/domains/domain1/autodeploy/"

      - name: Restart Aya-GlassFish domain
        uses: appleboy/ssh-action@v1
        with:
          host: ${{ secrets.SCP_HOST }}
          username: ${{ secrets.SCP_USER }}
          key: ${{ secrets.SSH_PRIVATE_KEY }}
          script: |
            /opt/aya-glassfish/bin/asadmin restart-domain domain1
```
