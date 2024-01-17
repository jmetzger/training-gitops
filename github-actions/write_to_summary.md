# Write to summary - example 

  * Writing to $GITHUB_STEP_SUMMARY writes to a summry, that is visible on the summary of the actions - run 

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
          echo "### Hello world! :rocket:" >> $GITHUB_STEP_SUMMARY
          pwd 
          ls -la
          #/bin/false
          echo "### Hello world in build after false ! :rocket:" >> $GITHUB_STEP_SUMMARY
    
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
          echo "### Hello world in deploy after false ! :rocket:" >> $GITHUB_STEP_SUMMARY
```
