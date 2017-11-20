# Base-PHP7-Dev

This image is used for local development of BasePlatform services.

This image inherits from strong-alpine-nginx-php-s6 image. It maps your working source folder to the folder /var/www/app of container.

To use it, make sure you:

* Built the base image: strong-alpine-nginx-php7-s6
* Built the dev image (this image): strong-php7-dev