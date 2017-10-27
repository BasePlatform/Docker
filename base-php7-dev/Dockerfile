# create a file named Dockerfile
FROM base-alpine-nginx-php7-s6:latest

ENV SERVICE_PORT 80
ENV NGINX_CONF /var/www/BasePlatform/Config/nginx
ENV PHP_CONF /var/www/BasePlatform/Config/php

VOLUME /var/www/app
VOLUME /etc/nginx/conf.d
VOLUME /etc/php7

COPY files/php/conf.d/local.ini /etc/php7/conf.d/
COPY files/nginx/nginx.conf /etc/nginx/nginx.conf
COPY files/nginx/default.conf /etc/nginx/conf.d/default.conf

WORKDIR /var/www/app

EXPOSE $SERVICE_PORT
