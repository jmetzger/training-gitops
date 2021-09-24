# Using Digitalocean Kubernetes 

## Walkthrough 

```
# Step 1: Setup Kubernetes through digitalocean interface 

# Step 2: Setup Container Registry (digitalocean) 
(if not setup create a container registry)
ours is currently: training 

# Step 3a: Create personal access key 
https://cloud.digitalocean.com/account/api/

# Step 3b: ... and save it as secret DIGITALOCEAN_ACCESS_TOKEN in your repo 
Repo -> Settings -> Secrects -> New Repository Secret (Button top left) 

# Step 4: Kubernetes Cluster (digitalocean) mit Registry verheiraten (digitalocean) 
In the control panel, you can select the Kubernetes clusters to use with your registry. 
This generates a secret, adds it to all the namespaces in the cluster and updates 
the default service account to include the secret, allowing you to pull images from the registry.

Container Registry -> Settings (Tab) -> Digital Ocean Kubernetes Integration -> Edit 

Integrate all clusters -> Save (Button) (or only one specific cluster) 

```


## Reference 

  * https://docs.digitalocean.com/products/kubernetes/how-to/deploy-using-github-actions/
