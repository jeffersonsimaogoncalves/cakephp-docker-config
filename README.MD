# CakePHP3 with Docker
This repo contains basic configuration to run CakePHP 3 projects using Docker.
To get it working you have to create your own project using composer like in this example:

```
composer create-project --prefer-dist cakephp/app myawesomeapp
```

For more details about installation read the [DOC](https://book.cakephp.org/3.0/en/installation.html).

## Installation
After setting UP CakePHP3 project, you have to clone docker config from this repo using this command:

```
git clone https://github.com/RoBYCoNTe/cakephp-docker-config.git
```

Edit your vhosts file adding this new line (this will enable navigation using localhost):
```
127.0.0.1 dev.local
```

## Usage
To use docker configuration just run this command inside docker folder (placed
in the root directory of the CakePHP project):

```
docker-compose -f docker/docker-compose.yml up
```

Open webpage [http://dev.local:8880](http://dev.local:8880) to see the result. 

## Database
Data associated to your instance will be stored inside docker/mariadb/data folder.
This will ensure the capability to move data between users and machines without any kind of problem.
To get this working I've implemented these [guidelines](https://docs.docker.com/samples/library/mariadb/).
To automatically change database configuration to get it working with docker:
```
composer require robyconte/cakephp-dockerize
bin/cake plugin load Dockerize
bin/cake Dockerize.setup exec
```

## Env
You can edit environment variables editing .env file in the root folder.
Env variables are shared between db and php-fpm instances.
Use `env` in php to access environment variables without writing username 
and password in the source code of the application.