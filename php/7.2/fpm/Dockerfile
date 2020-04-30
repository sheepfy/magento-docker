FROM php:7.2-fpm
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

RUN pecl install xdebug
RUN docker-php-ext-enable xdebug

RUN pecl install mcrypt-1.0.3
RUN docker-php-ext-enable mcrypt


#RUN curl -L -o /tmp/xdebug.tar.gz https://github.com/xdebug/xdebug/archive/2.9.5.tar.gz \
#    && tar xfz /tmp/xdebug.tar.gz \
#    && rm -r /tmp/xdebug.tar.gz \
#    && mv xdebug-2.9.5 /usr/src/php/ext/xdebug \
#    && docker-php-ext-install xdebug

