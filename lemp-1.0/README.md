# Docker LEMP for local web development

## Content

This branch contains a basic LEMP stack running on Docker and orchestrated by Docker Compose, including:

* A container for Nginx;
* A container for PHP-FPM;
* A container for MySQL;
* A container for phpMyAdmin;
* A volume to persist MySQL data.

The containers are based on Alpine images when available, for an optimised size.

## Prerequisites

Make sure [Docker Desktop for Mac or PC](https://www.docker.com/products/docker-desktop) is installed and running, or head [over here](https://docs.docker.com/install/) if you are a Linux user. You will also need a terminal running [Git](https://git-scm.com/).

This setup also uses localhost's port 80, so make sure it is available.

## Directions of use

Add the following domains to your machine's `hosts` file:

```
127.0.0.1 php.test phpmyadmin.test
```

Guide for setup `hosts` file in windows

```
* open power shell as administrator
* open host file:
notepad $env:windir\system32\drivers\etc\hosts
```

Clone the repository and `checkout` the `dclemp01` branch:

```
$ git clone git@github.com:muhamadherwan/docker-compose dclemp01 && cd dclemp01
$ git checkout dclemp01
```

Copy `.env.example` to `.env`:

```
$ cp .env.example .env
```

Set project name in the `.env`

```
COMPOSE_PROJECT_NAME=<new project name>
```

Run the following command:

```
$ docker compose up -d
```

This may take a little bit of time, as some Docker images might need downloading.

Once the script is done:

* visit [php.test](http://php.test).

* visit [php version](http://php.test/about.php).

* visit [phpmyadmin.test](http://phpmyadmin.test/).

## Cleaning up

To stop the containers:

```
$ docker compose stop
```

To destroy the containers:

```
$ docker compose down
```

To destroy the containers and the associated volumes:

```
$ docker compose down -v
```

To remove everything, including images and orphan containers:

```
$ docker compose down -v --rmi all --remove-orphans
```