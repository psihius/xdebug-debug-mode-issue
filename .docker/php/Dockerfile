FROM php:8.2-fpm as php

ARG XDEBUG

RUN apt-get update && apt-get install -y strace

RUN \
    pecl install xdebug-${XDEBUG} \
    && docker-php-ext-enable xdebug

# Install composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Copy php.ini file
COPY ./.docker/php/php.ini /usr/local/etc/php/conf.d/custom.ini

# Set working directory
WORKDIR /var/www/html
