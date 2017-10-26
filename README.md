# Docker
Docker image files for setting up the environment of BasePlatform

After having all the images, you can start a BasePlatform service

* docker run -v `/path_to_your_source`:/var/www/app -p `port_number`:`port_number` -e SERVICE_PORT=`port_number` base-php7-dev:latest

```bash
docker run -v /var/www/BasePlatform/App:/var/www/app -p port_number:80 -e SERVICE_PORT=80 base-php7-dev:latest
```

If you need customizing the Nginx and PHP Conf, you can use the following commands

* docker run -v `/path_to_your_source`:/var/www/app -v `/path_to_your_nginx_conf`:/etc/nginx/conf.d -p `port_number`:`port_number` -e SERVICE_PORT=`port_number` base-php7-dev:latest

Example - this will create a container and log in to the container

```bash
docker run -it -v /var/www/BasePlatform/App:/var/www/app -v /var/www/BasePlatform/Environment/nginx/conf.d:/etc/nginx/conf.d -p 80:80 -e SERVICE_PORT=80 base-php7-dev:latest /bin/sh
```
