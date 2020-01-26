FROM php:7.4.2-apache

RUN mv "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

COPY config/php.ini $PHP_INI_DIR/conf.d/custom.ini