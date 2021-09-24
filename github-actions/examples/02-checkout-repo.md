# This is a basic workflow to help you get started with Actions

name: Jochen's erster Workflow 

# Controls when the workflow will run
on: push

# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:
  # This workflow contains a single job called "build"
  jochen-checksout-and-runs-something:
    # The type of runner that the job will run on
    runs-on: ubuntu-latest

    # Steps represent a sequence of tasks that will be executed as part of the job
    steps:

      - name: Checke repo aus
        uses: actions/checkout@v2
        
      - run: |
          ls -la
          pwd
          env
      # Runs a single command using the runners shell
      - run: echo Hello, world!
