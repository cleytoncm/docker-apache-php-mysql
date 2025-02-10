FROM php:8.0-apache

RUN a2enmod rewrite
RUN a2enmod headers

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

RUN docker-php-ext-install pdo_mysql mysqli mbstring exif pcntl bcmath gd zip

RUN docker-php-ext-configure gd --enable-gd --with-freetype --with-jpeg

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Add user for laravel application
RUN groupadd -g 1000 www
RUN useradd -u 1000 -ms /bin/bash -g www www

RUN printf 'date.timezone = "America/Sao_Paulo"\n' > /usr/local/etc/php/conf.d/tzone.ini
RUN printf 'post_max_size = 50M\n' > /usr/local/etc/php/conf.d/fileupload.ini
RUN printf 'upload_max_filesize = 20M\n' >> /usr/local/etc/php/conf.d/fileupload.ini
RUN printf 'max_execution_time = 600\n' >> /usr/local/etc/php/conf.d/max_execution_time.ini
RUN printf 'memory_limit = 256M\n' >> /usr/local/etc/php/conf.d/memory_limit.ini
RUN printf 'expose_php = Off\n' >> /usr/local/etc/php/conf.d/expose_php.ini

RUN docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-enable pdo pdo_mysql mysqli mbstring exif pcntl bcmath gd zip