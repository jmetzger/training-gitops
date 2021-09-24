# Example - Simple workflow test 


```
# This is a basic workflow to help you get started with Actions
# .github/workflows/workflow-test.yml 

name: Jochen's erster Workflow 

# Controls when the workflow will run
on: push

# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:
  # This workflow contains a single job called "build"
  jochen-runs-something:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:

      # Runs a single command using the runners shell
      - run: echo Hello, world!
```
