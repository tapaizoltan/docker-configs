FROM ubuntu:latest
RUN apt update
RUN apt -y install locales
RUN DEBIAN_FRONTEND=noninteractive TZ=Europe/Budapest apt -y install tzdata
RUN apt install -y software-properties-common gnupg2 curl ca-certificates curl gnupg gpg
RUN add-apt-repository -y ppa:ondrej/php
RUN mkdir -p /etc/apt/keyrings
RUN curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg
RUN echo 'deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_18.x nodistro main' | tee /etc/apt/sources.list.d/nodesource.list
RUN apt update -y && apt upgrade -y
RUN apt install -y nodejs
RUN npm install -g npm
RUN apt install -y zip unzip git mc nano mysql-client htop neofetch
RRUN apt install -y php8.3 php8.3-cli php8.3-curl php8.3-mysql php8.3-xml php8.3-mbstring php8.3-imagick php8.3-gd php8.3-bcmath php8.3-intl php8.3-zip php8.3-fpm
RUN php -r "readfile('https://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer
RUN unlink /etc/localtime
RUN ln -s /usr/share/zoneinfo/Europe/Budapest /etc/localtime
EXPOSE 8000
EXPOSE 8080
CMD tail -f /dev/null
