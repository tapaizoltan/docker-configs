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
RUN apt install -y libapache2-mod-php php php-common php-cli php-tokenizer php-curl php-mysql php-xml php-json php-mbstring php-imagick php-gd php-bcmath php-intl php-zip php-fpm
RUN php -r "readfile('https://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer
RUN unlink /etc/localtime
RUN ln -s /usr/share/zoneinfo/Europe/Budapest /etc/localtime
EXPOSE 8000
EXPOSE 8080
CMD tail -f /dev/null