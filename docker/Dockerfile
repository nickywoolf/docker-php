FROM php:7.2-apache-stretch

RUN apt-get update -y \
    && apt-get install -y \
       libfreetype6-dev \
       libmcrypt-dev \
       libjpeg-dev \
       libpng-dev \
    && docker-php-ext-configure gd \
       --with-freetype-dir=/usr/include/freetype2 \
       --with-png-dir=/usr/include \
       --with-jpeg-dir=/usr/include \
    && docker-php-ext-install \
       pdo_mysql \
       mysqli \
       opcache \
       gd \
    && pecl install xdebug \
    && docker-php-ext-enable \
       xdebug \
       gd \
    && a2enmod rewrite

COPY docker/php/php.ini /usr/local/etc/php/php.ini
COPY . /var/www/html
COPY docker/apache/vhost.conf /etc/apache2/sites-available/000-default.conf
