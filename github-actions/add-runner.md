# Add self-hosted runner to github 

# Prerequisites

  * Install docker 

# Walkthrough

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

```






# Reference 

  * https://docs.github.com/en/actions/hosting-your-own-runners/adding-self-hosted-runners

