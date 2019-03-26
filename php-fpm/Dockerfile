From php:7-fpm-alpine
MAINTAINER zvonimirsun <hi@iszy.xyz>

RUN apk add --no-cache  alpine-sdk libpng libpng-dev \
    && docker-php-ext-install -j$(nproc) pdo_mysql mysqli gd \
    && apk del  alpine-sdk libpng-dev
