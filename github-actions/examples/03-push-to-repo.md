# Push to repo - Example 


```
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
      - name: In repo schreiben
        run: |
          env > umgebung.txt
          ls -la >> umgebung.txt
          ls -la $GITHUB_WORKSPACE 
          ls -la 
          
      - name: Commit files
        run: |
          git config --local user.email "41898282+github-actions[bot]@users.noreply.github.com"
          git config --local user.name "github-actions[bot]"
          git add .
          git commit -m "Add changes" -a
          
      - name: Push changes
        uses: ad-m/github-push-action@master
        
```
