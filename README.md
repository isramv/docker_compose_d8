# docker compose D8

## Requirements 

- [Docker](https://www.docker.com/community-edition)
- [composer](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-osx)

clone the repo:

```bash
$ git clone git@github.com:isramv/docker_compose_d8.git
```

Copy or rename env_example to .env

```bash
$ cp env_example .env
```

And edit .env with your own settings.

# run docker-compose

```bash
$ docker-compose up -d
```

# add your site to hosts file.

In our env_example file the variable **TRAEFIK_HOST** is set to `site.local`

```bash
$ sudo vim /etc/hosts
```
Add that site to your localhost line:

```bash
127.0.0.1       localhost site.local
```

# Install a fresh D8 site with composer

```bash
$ docker-compose exec --user=82 php composer install
```
to stop it
```bash
$ docker-compose stop
```

# Database

## installing Drupal, use mariadb instead of localhost:

![isntalling d8](https://www.evernote.com/l/Ar8MCZ_MMGdLEJNL7_RK9wC8MMh6j5MEHgwB/image.png)


## Acessing with sequel Pro client

![configuration](https://www.evernote.com/l/Ar-v6WAoltRM0q9PH2PVg1fGoc5YspwdLEwB/image.png)

# drush stuff

```bash
$ docker-compose exec --user=82 php drush -r /var/www/html/web status
$ docker-compose exec --user=82 php drush -r /var/www/html/web uli
```
# drupal console site aliases (only D8).

user login

```bash
$ docker-compose exec --user=82 php drupal @site.local ulu 1
```
# destroy docker instance

```bash
$ docker-compose down -v
```
# ssh your docker image

nginx
```bash
$ docker-compose exec --user=82 ngnix sh
```

php
```bash
$ docker-compose exec --user=82 nginx sh
```
