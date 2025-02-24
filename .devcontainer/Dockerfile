FROM php:8.2-fpm-alpine

RUN apk add --no-cache \
    zip \
    gmp-dev \
    npm && \
    docker-php-ext-install \
    mysqli \
    pdo \
    pdo_mysql \
    gmp

RUN apk add --no-cache mysql-client mariadb-connector-c-dev msmtp perl wget procps shadow libzip libpng libjpeg-turbo libwebp freetype icu icu-data-full

RUN apk add --no-cache --virtual build-essentials \
    icu-dev icu-libs zlib-dev g++ make automake autoconf libzip-dev \
    libpng-dev libwebp-dev libjpeg-turbo-dev freetype-dev && \
    docker-php-ext-configure gd --enable-gd --with-freetype --with-jpeg --with-webp && \
    docker-php-ext-install gd && \
    docker-php-ext-install mysqli && \
    docker-php-ext-install pdo_mysql && \
    docker-php-ext-install intl && \
    docker-php-ext-install opcache && \
    docker-php-ext-install exif && \
    docker-php-ext-install zip && \
    docker-php-ext-install pcntl && \
    apk del build-essentials && rm -rf /usr/src/php*

# install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

