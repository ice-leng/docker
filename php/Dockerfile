FROM php:7.0-fpm

COPY ./sources.list.jessie /etc/apt/sources.list

## Update Ubuntu
RUN apt-get update

## mcrypt
RUN apt-get install -y libmcrypt-dev
RUN docker-php-ext-install mcrypt

## GD
RUN apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng12-dev
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-install -j$(nproc) gd

## Intl
RUN apt-get install -y libicu-dev
RUN docker-php-ext-install -j$(nproc) intl

## General
RUN docker-php-ext-install zip
RUN docker-php-ext-install pcntl
RUN docker-php-ext-install opcache
RUN docker-php-ext-install pdo_mysql
RUN docker-php-ext-install mysqli
RUN docker-php-ext-install mbstring

# Required by composer
RUN apt-get -y install \
            git \
            zlib1g-dev \
        --no-install-recommends apt-utils

# Install composer
RUN curl -sS https://getcomposer.org/installer \
| php -- --install-dir=/usr/bin/ --filename=composer