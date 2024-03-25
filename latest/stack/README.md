(1) Hálózat létrehozása:
docker network create stack-mysql

(2) Tároló létrehozása:
docker volume create stack

(3) Felépítés:
docker build . -t stack

(4) Első indítás:
docker run --name stack -d -v stack:/var/www/html -p 80:8000 --network stack-mysql stack <-// akkor ha csak a stack-et akajuk futtatni
- vagy -
docker run --name stack -d -v stack:/var/www/html -p 80:8000 -p 8080:8080 --network stack-mysql stack <-// akkor ha nem csak a stack-et akarjuk futtatni hanem egy vscode servert is, de akkor előtte ki kell kommentelni a Docker fájlban az EXPOSE 3000-es sort és úgy kell build-elni.

(5) Standard indítás:
docker run stack

(6) Opcionális - code-server telepítése és futtatása kontémeren belül

(Belépés a konténerbe bash-el)
docker exec -it stack bash

Raspberry Pi 4-esen és 5-ösön:
curl -fOL https://github.com/coder/code-server/releases/download/v4.22.1/code-server_4.22.1_arm64.deb
dpkg -i code-server_4.22.1_arm64.deb
systemctl enable --now code-server@$USER <-// Figyelem! a dockeren belül nincs systemctl
nano /root/.config/code-server/config.yaml -> bind-addr: 0.0.0.0:8080    auth: none
code-server

# Now visit http://127.0.0.1:8080. Your password is in ~/.config/code-server/config.yaml