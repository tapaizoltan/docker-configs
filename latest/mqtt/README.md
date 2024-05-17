(1) Tároló létrehozása:
docker volume create mosquitto

(2) Első indítás:
docker run --name mqtt -d -p 1883:1883 -p 9001:9001 -v mosquitto:/mosquitto/config -v mosquitto:/mosquitto/data -v mosquitto:/mosquitto/log eclipse-mosquitto

(3) Mosquitto config szerkesztése:
Bele kell rakni a /mosquitto/config/mosquitto.conf fájlba:

(3a) Ha hitelesítés nélkül szeretnék kapcsolódni a brókerhez akkor ezt:

persistence true
persistence_location /mosquitto/data/
log_dest file /mosquitto/log/mosquitto.log
allow_anonymous true
listener 1883
listener 9001
protocol websockets

(3b) Ha hitelesítéssel szeretnénk kapcsolódni a brókerhez akkor ezt:

persistence true
persistence_location /mosquitto/data/
log_dest file /mosquitto/log/mosquitto.log
allow_anonymous false
password_file /mosquitto/config/auth
listener 1883
listener 9001
protocol websockets

?-(4) Ha hitelesítéses kapcsolatot állítottunk be akkor létre kell hozni egy auth fájlt hitelesítési adatokkal
mosquitto_passwd -c /mosquitto/config/auth <mosquitto_felhasznalonev>
password: <akarmi>

(5) Újraindítás fontos!

(6) Standard indítás:
docker run mqtt