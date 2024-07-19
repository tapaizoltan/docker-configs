(1) Tároló létrehozása:
docker volume create homeassistant-data

(2) Első indítás:
docker run --name homeassistant -d -v homeassistant-data:/config -p 8123:8123 --privileged --restart=unless-stopped -e TZ="Europe/Budapest" --network=hstack-mysql ghcr.io/home-assistant/home-assistant:stable

(3) Standard indítás:
docker run homeassistant