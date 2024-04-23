(1) Első indítás:
docker run --name mailpit -d -p 8025:8025 --restart=unless-stopped --network stack-mysql axllent/mailpit:latest

(5) Standard indítás:
docker run mailpit