From php:7-fpm-alpine
MAINTAINER zvonimirsun <hi@iszy.xyz>

RUN apk add --no-cache libzip-dev freetype libpng libjpeg-turbo freetype-dev libpng-dev libjpeg-turbo-dev \
    && docker-php-ext-install -j$(nproc) pdo_mysql zip mysqli gd \
    && apk del --no-cache freetype-dev libpng-dev libjpeg-turbo-dev libzip-dev
