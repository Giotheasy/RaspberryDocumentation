# Docker

---

## Installation

```sh
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

## Basic Commands

#### Pull images from the docker public repository

```sh
docker pull <image>
# Example: pulling alpine image
docker pull alpine
```

#### Create and run a container from an image. Modifier `-it` permit use all the host resources. Modifier `-d` starts the container detached (background).

```sh
docker run -it -d <image>
# Example: running mariadb
docker run -it -d mariadb
```

#### List the running containers

```sh
docker ps
```

#### Show all the running and exited containers

```sh
docker ps -a
```

#### Access to a running container

```sh
docker exec -it <container_id> bash
```

#### Stop a running container

```sh
docker stop <container_id>
```

#### Kill instantly a running container

```sh
docker kill <container_id>
```

#### Creates a new image of an edited container on the local system

```sh
docker commit <container_id>
```

#### Delete a stopped container

```sh
docker rm <container_id>
```

#### Delete an image from local storage

```sh
docker rmi <image_id>
```

#### Build an image from a specified docker file

```sh
docker build <path to docher file>
```

#### Run a container and give it a port on the local machine

```sh
docker run -d -p <local_port>:<container_port> <image_id>
# Example: run a container detached where connects the local port 5000 to the container port 8000
docker run -d -p 5000:8000 missingpets
```

## Dockerfile Example

```dockerfile
FROM alpine:latest
RUN apk -U update \
    && apk upgrade \
    && apk add --no-cache python3-dev \
    && apk add --no-cache --virtual build-deps gcc musl-dev \
    && apk add --no-cache mariadb mariadb-dev mariadb-common mariadb-client \
    && apk add --no-cache py3-pip \
    && apk add --no-cache jpeg-dev zlib-dev libjpeg \
    && python3 -m pip install --upgrade pip \
    && mkdir "missingpets"
COPY . /missingpets
WORKDIR /missingpets

RUN pip install -r requirements.txt
EXPOSE 8000
ENTRYPOINT ["./gunicorn_starter.sh"]
```

## .dockerignore Example

```docker
venv/
env/
.idea/
.git/
```

## PostgreSQL over Docker

```sh
docker run --name db-postgres -p 5432:5432 -e POSTGRES_PASSWORD=<mysecretpassword> -d postgres

# ... or more complete
docker run --name db-postgres -p 5432:5432 -d -e POSTGRES_PASSWORD=<password> \
 -e POSTGRES_USER=<username> \
 -e POSTGRES_DB=<example> \
 -v pgdata:/var/lib/postgresql/data \
  postgres

```

## Docker-compose example with PostgreSQL

```yaml
version: "3.3"

services:
  postgres:
    image: postgres
    ports:
      - "5432:5432"
    restart: unless-stopped
    environment:
      POSTGRES_PASSWORD: <password>
      POSTGRES_USER: <username>
      POSTGRES_DB: <database_name>
      DATABASE_HOST: 127.0.0.1
    volumes:
      - /localpath/local/postgres:/var/lib/postgresql/data
```

```yaml
version: "3.8"
services:
  postgres:
    container_name: database_postgresql
    image: postgres:14.1-alpine
    restart: always
    environment:
      - POSTGRES_USER=galo
      - POSTGRES_PASSWORD=admin
      - POSTGRES_DB=mibasegalo
      - POSTGRES_HOST=localhost
    volumes:
      - ./db:/var/lib/postgresql/data
  php:
    build:
      context: ./
      dockerfile: Dockerfile
    container_name: servidor-php
    restart: always
    ports:
      - 8080:80
    volumes:
      - ./html:/var/www/html
  django_app:
    build:
      context: ./
      dockerfile: DockerfileDjango
    container_name: webapp_django
    restart: always
    volumes:
      - ./djangoapp:/application
    ports:
      - 5000:5000
    command: python manage.py runserver 0.0.0.0:5000
volumes:
  html: {}
  db: {}
```

### PHP service Dockerfile

```Dockerfile
FROM php:apache
RUN apt-get update \
    && apt-get install -y libpq-dev \
    && docker-php-ext-install pdo pdo_pgsql pgsql \
    && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql

```

### Django service Dockerfile (DockerfileDjango)

```Dockerfile
FROM python:latest
WORKDIR /application
COPY ./djangoapp/requirements.txt /application/
RUN pip install -r requirements.txt
COPY ./djangoapp/ /application/

```

#### To init the django project

```sh
docker-compose run <service-name> <command>
```

Example:

```sh
docker-compose run django_app django-admin startproject application .
```

or

```sh
docker-compose run django_app python manage.py startapp blog
```

### SQL Server docker-compose example

```yaml
version: "3.8"
services:
  sql-server:
    container_name: sql-server
    image: mcr.microsoft.com/mssql/server:2019-latest
    restart: always
    ports:
      - 1433:1433
    environment:
      - SA_PASSWORD=very_long_password
      - ACCEPT_EULA=Y
```

### CodeIgniter docker-compose and Dockerfile example

#### docker-compose example

```yaml
version: "3.8"
services:
  codeigniter:
    build:
      context: ./
      dockerfile: DockerfileCodeigniter
    container_name: codeigniter
    restart: always
    ports:
      - 5050:80
    volumes:
      - ./html2:/var/www/html
```

#### DockerfileCodeigniter

```Dockerfile
FROM php:8.0-apache
RUN apt-get update
RUN apt-get install -y
RUN apt-get install -y curl
RUN apt-get install -y build-essential libssl-dev zlib1g-dev libpng-dev libjpeg-dev libfreetype6-dev
RUN apt-get install -y libicu-dev
RUN apt-get update
RUN docker-php-ext-install intl
RUN docker-php-ext-configure intl
RUN apt-get install -y libpq-dev
RUN docker-php-ext-install pdo pdo_pgsql pgsql
RUN docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql
RUN service apache2 restart
```

#### Codeigniter extra permissions

Common issues are related with the system permissions:

```sh
sudo chown -R $USER <development_path>
sudo chmod 777 -R <development_path>
```
