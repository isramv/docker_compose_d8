# docker compose D8

# Credits

- https://github.com/weknowinc

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

In our `env_example` file the variable **`TRAEFIK_HOST`** is set to `site.local`

```bash
$ sudo vim /etc/hosts
```

Append:

```
127.0.0.1 site.local mailhog.site.local webgrind.site.local
```

# Install a fresh D8 site with composer

```bash
$ docker-compose exec --user=82 php composer install
```
to stop it
```bash
$ docker-compose stop
```

# Aliases

A bash script to set up aliases

```bash
source scripts/env
drush status
```

# Database

## installing Drupal, use mariadb instead of localhost:

```bash
drush -y site-install --db-url=mysql://drupal:drupal@mariadb/drupal
drush uli
```

or via UI:

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

# Debugging

## Xdebug

[`scripts/env`](scripts/env) defines a function to enable/disable xdebug:

```bash
# enable
xdebug en
# disable
xdebug dis
```

## Profile with Webgrind

To use [webgrind](https://github.com/jokkedk/webgrind) to profile php, uncomment the line in your [`.env`][env_example].

```bash
COMPOSE_FILE=docker-compose.yml:docker-compose.debug.yml
```

and run up again to rebuild containers

```bash
docker-compose up -d
```

# destroy docker instance

```bash
$ docker-compose down -v
```
# ssh your docker image

nginx
```bash
$ docker-compose exec --user=82 nginx sh
```

php
```bash
$ docker-compose exec --user=82 php sh
```
