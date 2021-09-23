# Install docker (on Ubuntu 20.04)

## Walkthrough 

```
sudo su -
apt update && apt install -y apt-transport-https ca-certificates curl software-properties-common && curl -fsSL https://download.docker.com/linux/ubuntu/gpg | apt-key add -;
add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable" && apt-get update && apt-cache policy docker-ce && apt-get install -y docker-ce && systemctl status docker
```
