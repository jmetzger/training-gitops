# Check langfile 

## Step 1: Prerequisites (in master) 

```
# only or locally 
# create files in master
dist/index.html
dist/en/index.html

```

```
# workflow yaml 
.github/workflows/lang.yaml 
```

```
name: langchecker

on:
  push:
    branches:    
      - 'feature/**'
    paths:
      - 'dist/index.html'

jobs:
  translation-check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
        with:
          fetch-depth: 0 # otherwise, there would be errors pushing refs to the destination repository.
      - run: |
          ls -la 
          git branch 
          git branch -r
          # grep always returns 1 by design if does not find a result 
          echo "--HEADER--" > ANALYZER 
          git diff --name-only HEAD origin/master -- dist/en/index.html >> ANALYZER 
          COUNT=$(cat ANALYZER | grep -cE "(--HEADER--|dist/en/index.html)")
          # 1 - Only HEADER line will be present  
          if [ $COUNT -eq 1 ] ; then  echo "dist/en/index.html not changed"; exit 1; else echo "Change in lang detected - Happy"; fi
 ```

```
git add -A; git commit -am "lang files"; git push
```

# Step 2: create feature 

´´´
git checkout -b feature/6 
´´´

```
# change
dist/index.html
```

```
git add -A; git commit -am "new version2
git push -u origin feature/6
```

```
Workflow müsste jetzt unter actions triggern und fehler
werden, weil dist/en/index.html (englische Version) nicht geämndert wurde
```
