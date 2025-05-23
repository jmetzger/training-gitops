# Use env variable 

## Version 1: Using $GITHUB_ENV 

```
name: secret test 

on:
  push:
    branches:
      - master

jobs:
  secret-test:
    runs-on: ubuntu-latest

    steps:
    - name: ausgabe 
      run: |
        echo "HANS=${{secrets.MYSECRET}}" >> $GITHUB_ENV
    - name: ausgabe2
      run: env | grep "HANS" 
  ```
