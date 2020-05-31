FROM php:7.3-apache

RUN a2enmod rewrite

RUN docker-php-ext-install pdo pdo_mysql mysqli

RUN apt-get update -y && apt-get install -y libpng-dev libjpeg62-turbo-dev libfreetype6-dev

RUN apt-get update

RUN docker-php-ext-install mbstring

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

RUN docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-enable pdo pdo_mysql mysqli