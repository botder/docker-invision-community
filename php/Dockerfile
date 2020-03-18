FROM php:7.4-fpm

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libzip-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd mysqli exif zip

COPY www.conf /usr/local/etc/php-fpm.d/www.conf
COPY php.ini /usr/local/etc/php/php.ini

# Setup permissions
ARG UID
ARG GID

RUN usermod -u ${UID} www-data \
    && groupmod -g ${GID} www-data
