(1) Tároló létrehozása:
docker volume create mailpit

(2) Első indítás:
docker run --name mailpit -d -p 8025:8025 --restart=unless-stopped --network stack-mysql -v mailpit:/data -e MP_DATABASE=/data/mailpit.db -e TZ=Europe/Budapest axllent/mailpit:latest

(3) Standard indítás:
docker run mailpit