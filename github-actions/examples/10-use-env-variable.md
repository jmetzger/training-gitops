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

## Version 2: Using env: (GLOBALLY) 

```
name: Example Workflow

on: [push]

env:
  HANS: 'hello'

jobs:
  example-job:
    runs-on: ubuntu-latest
    steps:
      - run: echo $HANS
```

## Version 3: Using env: (in job) 

```
name: Example Workflow

on: [push]

jobs:
  example-job:
    runs-on: ubuntu-latest
    env:
      HANS: 'world'
    steps:
      - run: echo $HANS
```

## Version 4: using env: (in step) 

```
name: Example Workflow

on: [push]
jobs:
  example-job:
    runs-on: ubuntu-latest
    steps:
      - name: Example Step
        run: echo $HANS
        env:
          HANS: 'step-value'
```
