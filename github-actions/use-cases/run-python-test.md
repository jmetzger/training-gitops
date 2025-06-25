# Run a python test github action 

## Step 1: Simple Version 

  * Import or fork  https://github.com/jmetzger/github-actions-python-test


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

  * Attention: You have to set write permssions to repo 

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
