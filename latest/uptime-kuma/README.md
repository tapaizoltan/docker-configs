(1) Tároló létrehozása:
docker volume create uptime-kuma

(2) Első indítás:
docker run -d -p 3001:3001 --name uptime-kuma --restart=always -v uptime-kuma:/app/data louislam/uptime-kuma:1

(3) Standard indítás:
docker run uptime-kuma