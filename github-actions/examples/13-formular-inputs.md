# Formular verwendets (inputs)

## Version 1: mit ifs 

```
# .github/workflows/deployment.yml
name: Deploy Application

on:
  workflow_dispatch:
    inputs:
      environment:
        description: 'Deployment environment'
        required: true
        default: 'staging'
        type: choice
        options:
          - development
          - staging
          - production
      version:
        description: 'Version/tag to deploy (e.g., v1.2.3)'
        required: true
        default: 'v1.0.0'
      deploy_notes:
        description: 'Optional deployment notes'
        required: false
      dry_run:
        description: 'Run in dry-run mode'
        required: false
        default: 'false'
        type: boolean

jobs:
  deploy:
    name: Deploy to ${{ github.event.inputs.environment }}
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - name: Display Input Values
        run: |
          echo "Environment: ${{ github.event.inputs.environment }}"
          echo "Version: ${{ github.event.inputs.version }}"
          echo "Deploy Notes: ${{ github.event.inputs.deploy_notes }}"
          echo "Dry Run: ${{ github.event.inputs.dry_run }}"

      - name: Run Deployment Script
        run: |
          if [ "${{ github.event.inputs.dry_run }}" = "true" ]; then
            echo "Performing dry-run deployment to ${{ github.event.inputs.environment }}..."
            # simulate deployment here
          else
            echo "Deploying version ${{ github.event.inputs.version }} to ${{ github.event.inputs.environment }}..."
            # real deployment commands go here
          fi
```
