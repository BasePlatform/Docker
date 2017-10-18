# Docker
Docker image files for setting up the environment of BasePlatform

After having all the images, you can start a BasePlatform service

```bash
docker run -v `/path_to_your_source`:/var/www/app -p `port_number`:`port_number` -e SERVICE_PORT=`port_number` base-php7-dev:latest
```

If you need customizing the Nginx and PHP Conf, you can use the following commands

```bash
docker run -v `/path_to_your_source`:/var/www/app -v `/path_to_your_nginx_conf`:/etc/nginx/conf.d -v `/path_to_your_php_fpm`:/etc/php7 -p `port_number`:`port_number` -e SERVICE_PORT=`port_number` base-php7-dev:latest
```
