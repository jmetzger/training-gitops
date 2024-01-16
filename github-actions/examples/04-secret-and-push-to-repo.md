# Secret and push to repo 

```
name: secret and push 

on: [push]

jobs:
  job1:
    runs-on: ubuntu-latest
    permissions:                # Job-level permissions configuration starts here
      contents: write           # 'write' access to repository contents
      pull-requests: write      # 'write' access to pull requests
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0 # otherwise, there would be errors pushing refs to the destination repository.
      - name: Create local changes 1
        run: |
          touch somefile.txt 
      - name: Create local secret 
        shell: bash
        env:
          SUPER_SECRET: ${{ secrets.SECRET_SUPER_SECRET }}
        run: |
          echo "$SUPER_SECRET" 
          echo "foo" > myfile 
          echo 
          echo "OUTPUT 1: -------"
          cat myfile
          echo "EOF OUTPUT1"
          echo 
          echo "OUTPUT 2: -------"
          echo "$SUPER_SECRET" >> myfile
          cat myfile 
          echo "EOF OUTPUT 2"
          echo 
          echo "OUTPUT 3: -------"
          echo "foo2" >> myfile 
          cat myfile 
          echo "EOF OUTPUT 3"
      - name: Commit files
        run: |
          git config --local user.email "41898282+github-actions[bot]@users.noreply.github.com"
          git config --local user.name "github-actions[bot]"
          git add -A
          git commit -a -m "Add changes"
      - name: Push changes
        uses: ad-m/github-push-action@master
        with:
          github_token: ${{ secrets.GITHUB_TOKEN }}
          branch: ${{ github.ref }}
```
