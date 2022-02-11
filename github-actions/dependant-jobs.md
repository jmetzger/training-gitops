# Dependant jobs 

## Execute job, if referred (by: needs) was succesful 

```
name: Jochen's nicer workflow 

on:
  # Triggers the workflow on push or pull request events but only for the master branch
  push:
    branches: [ master ]

jobs:
  build:
 
    runs-on: ubuntu-latest

    steps:
      - name: Run a one-line script
        run: | 
          pwd 
          ls -la
          /bin/false
    
  deploy:
    
    # needs a succesful build 
    # THAT IS IMPORTANT 
    needs: build 
    runs-on: ubuntu-latest 

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:
      - name: Starting the deploy 
        run: | 
          echo "starting the deployment process" 
          ls -la

```

## Ref: 

  * https://www.edwardthomson.com/blog/github_actions_17_dependent_jobs.html
