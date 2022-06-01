FROM php:8.0-apache-buster

ENV COMPOSER_ALLOW_SUPERUSER=1

ADD php.ini /usr/local/etc/php/
ADD 000-default.conf /etc/apache2/sites-enabled/

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN apt-get update -y && \
    apt-get upgrade -y && \
    apt-get -y install \
        libicu-dev \
        libzip-dev \
        libonig-dev \
        zip \
        unzip \
        libssl-dev && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    docker-php-ext-install intl mbstring opcache pdo_mysql zip

# COPY ./php.ini /usr/local/etc/php/php.ini

WORKDIR /var/www/html
