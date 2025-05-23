# Eintrag über github actions von reviewern:


```
.github/workflows/auto-reviewer-eintragen.yml
```

```
name: "Reviewer mit gh CLI hinzufügen"

on:
  pull_request:
    types: [opened, reopened, ready_for_review]

jobs:
  assign-reviewers:
    runs-on: ubuntu-latest

    permissions:
      pull-requests: write  # Notwendig für gh CLI

    steps:
      - name: Checkout Code
        uses: actions/checkout@v4

      - name: GitHub CLI installieren
        uses: cli/cli-action@v2

      - name: Reviewer hinzufügen
        env:
          GH_TOKEN: ${{ secrets.GITHUB_TOKEN }}  # Automatischer Token
        run: |
          gh pr edit ${{ github.event.pull_request.number }} \
            --repo ${{ github.repository }} \
            --add-reviewer user1 \
            --add-reviewer user2
```
