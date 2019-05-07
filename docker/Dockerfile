FROM php:7.2-apache-stretch

RUN docker-php-ext-install mysqli pdo_mysql opcache \
    && pecl install xdebug \
    && docker-php-ext-enable xdebug \
    && a2enmod rewrite

COPY docker/php/php.ini /usr/local/etc/php/php.ini
COPY . /var/www/html
COPY docker/apache/vhost.conf /etc/apache2/sites-available/000-default.conf
