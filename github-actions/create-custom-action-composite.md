# Create custom action (composite)

## Walkthrough 

### Step 1: create new repo 

```
# new repo - e.g.  <tln>-bash-action
# z.B. f1-bash-action 
```

### Step 2: create action.yml in repo (toplevel)

```
# action.yml - im toplevel
```

```
name: 'Hello World'
description: 'Greet someone'
inputs:
  who-to-greet:  # id of input
    description: 'Who to greet'
    required: true
    default: 'World'
outputs:
  random-number:
    description: "Random number"
    value: ${{ steps.random-number-generator.outputs.random-id }}
runs:
  using: "composite"
  steps:
    - run: echo Hello ${{ inputs.who-to-greet }}.
      shell: bash
    - id: random-number-generator
      run: echo "::set-output name=random-id::$(echo $RANDOM)"
      shell: bash
    - run: ${{ github.action_path }}/goodbye.sh
      shell: bash
```

### Step 3: Create script 

```
# goodbye.sh 
echo "Goodbye"
```

### Step 4: workflow erstellen 

```
## use it in other repo in workflow 
# .github/workflows/workflow-hello.yml 
```

```
on: [push]

jobs:
  greetings:
    runs-on: ubuntu-latest
    name: Greet Again 

    steps:
      - id: foo
        uses: gittrainereu/bash-action@main
        with:
          who-to-greet: 'Mona the Octocat'
      - run: echo random-number ${{ steps.foo.outputs.random-number }}
        shell: bash
```

## Type of actions 

  * JavaScript
  * Docker 
  * Composite 
  * Ref: https://docs.github.com/en/actions/creating-actions/about-custom-actions#types-of-actions

## Create a composite action 

  * https://docs.github.com/en/actions/creating-actions/creating-a-composite-action

## Reference 

  * https://docs.github.com/en/actions/creating-actions
