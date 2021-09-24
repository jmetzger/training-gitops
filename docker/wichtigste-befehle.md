# Wichtigste Docker - Befehle 

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
