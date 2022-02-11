# Wichtigste Docker - Befehle 

## Volume 1

```
mkdir testdir
cd testdir 
# Dockerfile anlegen 
docker build -t meincontainer .
docker images 
# interactive starten 
# nach exit wird er beendet 
docker run -it meincontainer
# im container exit 
docker ps -a 
```

## Volume 2

```
# image von docker hub download . hier ubuntu:latest
docker pull ubuntu

# Alle lokalen images anzeigen (auf dem Server vorhandene) 
# z.B. die auf dem Serer mit docker build . erstellt wurden
# ohne downgeloaded von docker hub 
docker images

# Neues docker container starten auf basis das ubuntu:latest images
# Im Hintergrund (Daemonized) und an ein Terminal 
docker run -dt ubuntu:latest

# Alle laufenden docker-container anzeigen 
docker ps 

# Alle docker - container (auch beendete anzeigen)
docker ps -a 

# Alle laufenden Container anzeigen 
docker exec -it e1a1d3 bash

# Laufenden Docker container beendet und löschen 
docker rm -f e21

# docker images anzeigen 
docker images

# docker image lokal löschen 
docker rmi ubuntu:latest


```
