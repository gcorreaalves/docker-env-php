# Set the base image to Ubuntu
FROM ubuntu:latest

# File Author / Maintainer
MAINTAINER Gustavo Alves <contato@gustavocalves.com.br>

# Set workd dir
WORKDIR ~

# Update Base System
RUN apt-get update \ 
    && apt-get install -y language-pack-en \
    && locale-gen en_US.UTF-8 \
    && dpkg-reconfigure locales

ENV LC_ALL en_US.UTF-8
ENV LANGUAGE en_US
ENV LANG en_US.UTF-8

# Install tools
RUN apt-get install -y build-essential \
    python-software-properties \
    software-properties-common \
    wget curl git man unzip nano

# Install nginx
RUN apt-get install -y nginx
ADD nginx/default /etc/nginx/sites-available/default

# Install php7 and extensions
RUN add-apt-repository ppa:ondrej/php && apt-get update
RUN apt-get remove php7.0 && apt-get install -y php7.1
RUN apt-get install -y php-curl \
    php-mysql \
    php-xml \
    php-xdebug \
    php-zip \
    php-mbstring \
    php-fpm

# Install mysql client
RUN apt-get install -y mysql-client

# Install redis tools
RUN apt-get install -y redis-tools

# Install composer
RUN curl -sS https://getcomposer.org/installer -o composer-setup.php
RUN php -r "if (hash_file('SHA384', 'composer-setup.php') === '669656bab3166a7aff8a7506b8cb2d1c292f042046c5a994c43155c0be6190fa0355160742ab2e1c88d40d5be660b410') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
RUN php composer-setup.php --install-dir=/usr/local/bin --filename=composer

# Create wwwroot dir
RUN mkdir /var/www/app.dev

# Command to start the container services
CMD service nginx start ; service php7.1-fpm start ; /bin/bash
