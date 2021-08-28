FROM php:7.4-apache

RUN a2enmod rewrite

RUN docker-php-ext-install pdo pdo_mysql mysqli

RUN apt-get update -y && apt-get install -y libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng-dev \
        zlib1g-dev \
        libxml2-dev \
        libzip-dev \
        libonig-dev \
        graphviz \
        apt-utils \
        zip \
        vim \
        unzip \
        curl 

RUN apt-get update

RUN docker-php-ext-install mbstring

RUN docker-php-ext-configure gd

RUN docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-enable pdo pdo_mysql mysqli 

RUN pecl install redis-5.1.1 \
    && pecl install xdebug-2.8.1 \
    && docker-php-ext-enable redis xdebug