# Deploy ansible 

## Create files 

```
# infrastructure/ansible/setup-prod.yml
```

```
---
- hosts: all
  tasks:
    - name: install packages
      become: true
      become_user: root
      apt:
        state: present
        name:
          - htop
```

```
# infrastructure/ansible/hosts
# anpassen mit deinem host un der ip (Trainer fragen ;o))
```

```
gr1.t3isp.de ansible_host=167.172.179.197
```



## Create workflow 

```
name: CI

# Controls when the workflow will run
on:
  # Triggers the workflow on push or pull request events but only for the "master" branch
  push:
    branches: [ "master" ]

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:
  
# A workflow run is made up of one or more jobs that can run sequentially or in parallel
jobs:
  run-playbooks:
    runs-on: ubuntu-latest
    steps: 
      - uses: actions/checkout@v4
      - name: Setup SSH 
        shell: bash
        run: |
         eval `ssh-agent -s`
         mkdir -p /home/runner/.ssh/
         touch /home/runner/.ssh/id_rsa
         echo -e "${{secrets.SSH_PRIVATE_KEY}}" > /home/runner/.ssh/id_rsa
         chmod 700 /home/runner/.ssh/id_rsa
         ssh-keyscan -t rsa,dsa,ecdsa,ed25519 ${{secrets.SSH_HOST}} >> /home/runner/.ssh/known_hosts
      - name: Run ansible script
        shell: bash 
        run: |
          cd infrastructure/ansible
          cat setup-prod.yml
          ansible-playbook -vvv --private-key /home/runner/.ssh/id_rsa -u ${{secrets.SSH_USER}} -i hosts setup-prod.yml
```
