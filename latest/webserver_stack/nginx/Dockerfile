FROM ubuntu:latest
RUN apt update
RUN apt -y install locales
RUN DEBIAN_FRONTEND=noninteractive TZ=Europe/Budapest apt -y install tzdata
RUN apt install software-properties-common gnupg2 curl ca-certificates curl gnupg gpg nginx -y
RUN add-apt-repository -y ppa:ondrej/php
RUN curl -fsSL https://deb.nodesource.com/setup_20.x | bash -
RUN apt update && apt upgrade -y
RUN apt install -y nodejs
RUN npm install -g npm
RUN apt install -y zip git mc zsh
RUN apt install -y php8.3 php8.3-cli php8.3-curl php8.3-mysql php8.3-xml php8.3-mbstring php8.3-imagick php8.3-gd php8.3-bcmath php8.3-intl php8.3-zip php8.3-fpm
RUN php -r "readfile('https://getcomposer.org/installer');" | php -- --install-dir=/usr/bin/ --filename=composer
RUN unlink /etc/localtime
RUN ln -s /usr/share/zoneinfo/Europe/Budapest /etc/localtime
RUN echo 'alias rnx="nginx -s reload"' >> ~/.bashrc
RUN echo "[www]\nuser = root\ngroup = root\n" > /etc/php/8.3/fpm/pool.d/zzz-docker.conf
RUN sed -i 's/--daemonize/--daemonize -R/g' /etc/init.d/php8.3-fpm
CMD service nginx start && service php8.3-fpm start && tail -f /dev/null