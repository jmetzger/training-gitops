# Run a python test github action 

## Step 1: Simple Version 

  * Import https://github.com/jmetzger/github-actions-python-test

### 1.1 Neues Repo als import 

![image](https://github.com/user-attachments/assets/4eb573e6-81c2-4e4b-9a78-bbff2d3eadac)

```
The url for your source repository:
https://github.com/jmetzger/github-actions-python-test

Your new repository detail:
Bei Repository name:
z.B. --> jm-github-actions-python-test

Begin import -> Button
```



## Info 2: This workflow is included 

```
name: Python Tests

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'

      - name: Install Dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt

      - name: Run Tests
        run: |
          pytest
```



## Step 3: We want more info: 

  * Does not work because of missing permissions 

```
name: Python Tests with Report

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'

      - name: Install Dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt

      - name: Run Tests and Generate Report
        run: |
          pytest --junitxml=pytest-results.xml

      - name: Upload Test Results
        uses: actions/upload-artifact@v4
        with:
          name: pytest-results
          path: pytest-results.xml

      - name: Publish Test Results
        uses: EnricoMi/publish-unit-test-result-action@v2
        if: always()
        with:
          files: pytest-results.xml
```

## Step 4: With correct permissions 

## Step 3: We want more info: 

  * Does not work because of missing permissions 

```
name: Python Tests with Report

permissions:
  checks: write
  pull-requests: write

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'

      - name: Install Dependencies
        run: |
          python -m pip install --upgrade pip
          pip install -r requirements.txt

      - name: Run Tests and Generate Report
        run: |
          pytest --junitxml=pytest-results.xml

      - name: Upload Test Results
        uses: actions/upload-artifact@v4
        with:
          name: pytest-results
          path: pytest-results.xml

      - name: Publish Test Results
        uses: EnricoMi/publish-unit-test-result-action@v2
        if: always()
        with:
          files: pytest-results.xml
```

