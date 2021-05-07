FROM php:7.4-apache-buster

RUN apt-get update -y \
    && apt-get install -y \
       libfreetype6-dev \
       libmcrypt-dev \
       libjpeg-dev \
       libpng-dev \
       libzip-dev \
       zip \
    && docker-php-ext-configure gd \
    && docker-php-ext-install \
       pdo_mysql \
       mysqli \
       opcache \
       gd \
       zip \
    && pecl install xdebug \
    && docker-php-ext-enable \
       xdebug \
       gd \
    && a2enmod rewrite

COPY docker/php/php.ini /usr/local/etc/php/php.ini
COPY . /var/www/html
COPY docker/apache/vhost.conf /etc/apache2/sites-available/000-default.conf
