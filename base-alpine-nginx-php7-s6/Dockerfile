FROM alpine:3.6

ENV SERVICE_PORT 80

# ENV for s6 overlay
ENV S6_OVERLAY_RELEASE v1.20.0.0

# root filesystem
COPY files/rootfs /

# s6 overlay
RUN apk add --no-cache curl \
 && curl -L -s https://github.com/just-containers/s6-overlay/releases/download/v1.20.0.0/s6-overlay-amd64.tar.gz \
  | tar xvzf - -C / \
 && apk del --no-cache curl

RUN apk update && \
    apk add nginx bash ca-certificates curl ssmtp php7 php7-phar php7-curl \
    php7-fpm php7-json php7-zlib php7-xml php7-dom php7-ctype php7-opcache php7-zip php7-iconv \
    php7-pdo php7-pdo_mysql php7-pdo_sqlite php7-pdo_pgsql php7-mbstring php7-session \
    php7-gd php7-mcrypt php7-openssl php7-sockets php7-posix php7-ldap php7-simplexml && \
    rm -rf /var/cache/apk/* && \
    rm -f /etc/php7/php-fpm.d/www.conf && \
    touch /etc/php7/php-fpm.d/env.conf

RUN curl -sS https://getcomposer.org/installer | php -- --filename=/usr/local/bin/composer

RUN rm -rf /var/www/* && mkdir /var/www/app

COPY files/php/conf.d/local.ini /etc/php7/conf.d/
COPY files/php/php-fpm.conf /etc/php7/
COPY files/php/info.php /var/www/index.php
COPY files/nginx/nginx.conf /etc/nginx/nginx.conf
COPY files/nginx/default.conf /etc/nginx/conf.d/default.conf

EXPOSE $SERVICE_PORT

COPY files/s6 /etc/services.d

# S6 init script
ENTRYPOINT [ "/init" ]