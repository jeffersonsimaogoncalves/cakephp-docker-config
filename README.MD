# CakePHP3 with Docker
This repo contains basic docker configuration's files required to run 
CakePHP 3 application using virtualized enviornment. 

## Create new CakePHP project.
If you want to test the config, you can create new CakePHP project
using composer like in this example:

```
composer create-project --prefer-dist cakephp/app myawesomeapp
```

For more details about installation read the [DOC](https://book.cakephp.org/3.0/en/installation.html).

## Installation
After setting up the project, you have to clone docker config using this command:

```
git clone https://github.com/RoBYCoNTe/cakephp-docker-config.git docker
```

This will create a new folder, inside your CakePHP project, called "docker" (
inside this folder you will have all configuration files required to run virtualized
environment with Nginx, PHP-FPM and MariaDB instance).

After that, edit your vhosts file adding this new line (this will enable navigation using dev.local with NGINX on port 8880):
```
127.0.0.1 dev.local
```

## Usage
To start using docker inside your app you have to run these commands:

```
cd docker
docker-compose up
```

Open webpage [http://dev.local:8880](http://dev.local:8880) to see the result. 

## Database
Data associated to your instance will be stored inside docker/mariadb/data folder.
This will ensure the capability to move data between different machines without any kind of problem (or just to allow copy of that data between computers).
To get this working I've implemented these [guidelines](https://docs.docker.com/samples/library/mariadb/).
To automatically change database configuration, after first CakePHP installation, I've built a
plugin that can help doing it very fast:
```
composer require robyconte/cakephp-dockerize
docker exec -it docker_php_1 /bin/bash
cd /app
bin/cake plugin load Dockerize
bin/cake Dockerize.setup exec
```

The *docker_php_1* refer the container running php-fpm instance.

## Env
You can edit environment variables editing .env file in the docker's root folder.
Env variables are shared between db and php-fpm instances.
Use `env` in php to access environment variables without writing
sensitive data in the source code of the application.