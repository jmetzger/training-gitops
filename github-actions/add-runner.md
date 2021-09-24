# Add self-hosted runner to github 

## Prerequisites

  * Install docker 

## Walkthrough

```
1. Login to github 
2. Click on repo -> settings
3. Click on actions 
4. Click on runners
5. Click add self-hosted runner 

# important, as we install it as root, 
# you need to 
export RUNNER_ALLOW_RUNASROOT="1"
# before doing the configuration ./config.sh 
see:
https://serverfault.com/questions/1052695/must-not-run-with-sudo-while-trying-to-create-a-runner-using-github-actions

# When configuration is done, install service and start it.
./svc.sh install
./svc.sh start
./svc.sh status 

```

## Using it for an action:

```
# Example 
# You need to activated it as:
# runs-on: [self-hosted, linux, x64, gpu]
# minimal would be 
runs-on: self-hosted 
```

## Full example 

  * in .github/workflows/whatevername.yml 

```
name: GitHub Actions Demo
on: [push]
jobs:
  Explore-GitHub-Actions:
    runs-on: self-hosted
    steps:
      - run: echo "🎉 The job was automatically triggered by a ${{ github.event_name }} event."
      - run: echo "🐧 This job is now running on a ${{ runner.os }} server hosted by GitHub!"
      - run: echo "🔎 The name of your branch is ${{ github.ref }} and your repository is ${{ github.repository }}."
      - name: Check out repository code
        uses: actions/checkout@v2
      - run: echo "💡 The ${{ github.repository }} repository has been cloned to the runner."
      - run: echo "🖥️ The workflow is now ready to test your code on the runner."
      - name: List files in the repository
        run: |
          ls ${{ github.workspace }}
      - run: echo "🍏 This job's status is ${{ job.status }}."
```

## View logs of runner - service 

```
systemctl status actions.runner.gittrainereu-runnertest.gh-runner1 -l
journalctl -u actions.runner.gittrainereu-runnertest.gh-runner1 
```

## Reference 

  * https://docs.github.com/en/actions/hosting-your-own-runners/adding-self-hosted-runners

