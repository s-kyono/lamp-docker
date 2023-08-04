FROM php:8.2-rc-fpm-bullseye

ADD docker/php/php.ini /usr/local/etc/php/
ADD docker/php/000-default.conf /etc/apache2/sites-enabled/

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

COPY api-server /var/www/html

# aptパッケージの更新とアップグレード
RUN apt-get -y update && \
    apt-get  -y upgrade

# debian開発パッケージインストール
RUN apt-get install -y \
    locales \
    libpq-dev \
    libicu-dev \
    libonig-dev \
    libzip-dev \
    libssl-dev \
    g++ \
    zlib1g-dev \
    zip \
    unzip

# PHP開発で使用するパッケージインストール
RUN docker-php-ext-install \
    intl \
    opcache \
    pdo \
    pdo_mysql \
    mysqli

# pecl PHP Extension Community Library PHP言語を拡張するためのモジュールレポジトリ
RUN pecl install apcu-5.1.22

# apcu有効化
RUN docker-php-ext-enable apcu

# Composer インストール
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# apt-get クリーン
RUN apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# xdebug設定
RUN pecl install xdebug-3.2.0 && docker-php-ext-enable xdebug

WORKDIR /var/www/html
