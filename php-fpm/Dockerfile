From php:7-fpm-alpine
MAINTAINER zvonimirsun <hi@iszy.xyz>

# 更换国内源
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories \
    && apk update

RUN apk add --no-cache  alpine-sdk libpng libpng-dev \
    && docker-php-ext-install -j$(nproc) pdo_mysql mysqli gd \
    && apk del  alpine-sdk libpng-dev
