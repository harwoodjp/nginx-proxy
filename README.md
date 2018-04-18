## Starts an nginx container
docker run --name docker-nginx -p 80:80 -d -t nginx

## Starts an nginx container with /var/www/ mounted
docker run --name docker-nginx -p 80:80 -d -t -v /var/www/:/var/www nginx

## Attaches to terminal
docker attach docker-nginx

## Stops nginx
docker stop docker-nginx

## Removes container and frees namespace
docker rm docker-nginx

## Open container bash in host terminal
docker exec -ti docker-nginx /bin/bash

## Launch process with docker-compose
docker-compose up -d

## Remove all containers
docker ps -aq | xargs docker rm -f

## Crontab to start docker-compose on reboot
@reboot (sleep 30s ; cd /home/justin/nginx-proxy ; /usr/local/bin/docker-compose up --build -d )&
