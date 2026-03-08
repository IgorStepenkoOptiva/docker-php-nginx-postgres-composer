FROM php:8.3-fpm

MAINTAINER Descamps Antoine <antoine.descamps@ineat-conseil.fr>

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libicu-dev \
        libpq-dev \
        libzip-dev \
        libxpm-dev \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug \
    && docker-php-ext-configure gd \
        --with-freetype \
        --with-jpeg \
    && docker-php-ext-install -j$(nproc) \
        gd \
        intl \
        zip \
        pgsql \
        pdo_pgsql \
        exif

RUN apt-get clean && rm -rf /var/lib/apt/lists/*