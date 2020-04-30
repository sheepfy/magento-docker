FROM php:7.2-cli
MAINTAINER Matei Purcaru <matei.purcaru@gmail.com>

# Install modules
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        libicu-dev \
        libxml2-dev \
        g++\
        cron \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install gd \
    && docker-php-ext-install pdo pdo_mysql \
    && docker-php-ext-install intl \
    && docker-php-ext-install mbstring \
    && docker-php-ext-install soap

RUN pecl install mcrypt-1.0.3
RUN docker-php-ext-enable mcrypt

RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

# Run as a Non-Root Inside Docker Container
RUN adduser --disabled-password --gecos '' r
RUN adduser r sudo
RUN echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

