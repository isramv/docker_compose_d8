# docker compose D8

## Requirements 

- Docker for mac
- composer

clone the repo:

```bash
git clone git@github.com:isramv/docker_compose_d8.git
```

Copy or rename env_example to .env

```bash
cp env_example .env
```

And edit .env with your own settings.

# Install a fresh D8 site with composer

```bash
docker-compose exec --user=82 php composer install
```

# run docker-compose

```bash
$ docker-compose up -d
```

to stop it
```bash
$ docker-compose stop
```

# Database

## example using sequel Pro

![configuration](https://www.evernote.com/l/Ar-v6WAoltRM0q9PH2PVg1fGoc5YspwdLEwB/image.png)

# add your site to hosts file.

In our env_example file the variable **TRAEFIK_HOST** is set to `site.local`

```bash
$ sudo vim /etc/hosts
```
Add that site to your hosts file you can put it in the same line as shown in the following screenshot.

```bash
127.0.0.1       localhost site.local
```
