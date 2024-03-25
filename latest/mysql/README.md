(1) Tároló létrehozása:
docker volume create databases

(2) Első indítás:
docker run --name mysql -d -v databases:/var/lib/mysql -e MYSQL_ROOT_PASSWORD=root -p 3306:3306 --network stack-mysql mysql:latest

(5) Standard indítás:
docker run mysql