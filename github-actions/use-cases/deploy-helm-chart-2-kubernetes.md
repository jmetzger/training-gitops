# Use Case - helm chart mit githubactions nach Kubernetes 

## Prerequisites 

```
.kubeconfig als base64
cat .kube/config | base64 > .kubeconfig.b64
```

## Step 1: Klonen eines Beispiels 

   * Erstellen eines Repo aber über import mit folgender URL 
     * https://gitlab.com/jmetzger/training-helm-chart-kubernetes-gitlab-ci-cd.git

![image](https://github.com/user-attachments/assets/68e8aa22-ea52-4a6d-9379-7bd5b6d0a151)

## Step 2: Secret erstellen 

Settings -> Security -> Secrets & variables -> Actions -> New Repository Secret 

```
#
KUBECONFIG

# anlegen mit Inhalt von .kubeconfig.b64


```

## Step 3: Workflow erstellen 

  * Actions -> New Workflow -> Setup up a workflow yourself 

![image](https://github.com/user-attachments/assets/884ebadd-70bf-42c9-b18f-f44b3d948e91)


```
name: Deploy Helm Chart

on:
  push:
    branches:
      - main

jobs:
  helm-deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout Repository
      uses: actions/checkout@v4

    - name: Set up Kubeconfig
      run: |
        mkdir -p $HOME/.kube
        echo "${{ secrets.KUBECONFIG }}" | base64 -d > $HOME/.kube/config

    - name: Install Helm
      uses: azure/setup-helm@v3

    - name: Deploy with Helm
# bitte euren namespace eintragen anstelle von default , z.B. euren namen
# muss eindeutig sein 
      run: |

        helm upgrade --install my-release ./charts/my-app --namespace default --create-namespace
        kubectl -n default get all




```
