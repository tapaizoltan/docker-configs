(1) Tároló létrehozása:
docker volume create keepass-config

(2) Első indítás:
docker run -d --name=keepassxc --security-opt seccomp=unconfined -e PUID=1000 -e PGID=1000 -e TZ=Europe/Budapest -p 3000:3000 -p 3001:3001 -v keepass-config:/config --restart unless-stopped lscr.io/linuxserver/keepassxc:latest

(3) Standard indítás:
docker run keepassxc