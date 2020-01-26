FROM php:7.4.2-apache

RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

COPY config/php.ini $PHP_INI_DIR/conf.d/custom.ini

RUN docker-php-ext-install mysqli && docker-php-ext-enable mysqli

###COMPOSER###
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer --version

RUN apt-get update \
    && apt-get install -y zip unzip libzip-dev

RUN docker-php-ext-install zip

###FIN COMPOSER###

###XDEBUG###
RUN yes | pecl install xdebug

RUN echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/xdebug.ini\
    && echo "xdebug.remote_autostart=off" >> /usr/local/etc/php/conf.d/xdebug.ini

###FIN XDEBUG###