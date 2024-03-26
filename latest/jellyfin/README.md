(1) Tároló létrehozása:
docker volume create jellyfin-config
docker volume create jellyfin-cache

(2) Első indítás:
docker run -d --name jellyfin -p 8096:8096 --volume jellyfin-config:/config --volume jellyfin-cache:/cache --mount type=bind,source=/home/tapaizoltan/jellymedia,target=/media --restart=unless-stopped jellyfin/jellyfin

(5) Standard indítás:
docker run jellyfin