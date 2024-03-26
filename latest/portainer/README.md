(1) Tároló létrehozása:
docker volume create portainer-data

(2) Első indítás:
docker run -d -p 9000:9000 -p 9443:9443 --name portainer --restart=always -v /var/run/docker.sock:/var/run/docker.sock -v portainer-data:/data portainer/portainer-ce:latest

(5) Standard indítás:
docker run portainer