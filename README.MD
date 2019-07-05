# CakePHP3 🍰 with Docker 🐳
This repo contains basic configuration to run CakePHP 3 projects using Docker.
To get it working you have to create your own project using composer like in this example:

```
composer create-project --prefer-dist cakephp/app myawesomeapp
```

For more details about installation read the [DOC](https://book.cakephp.org/3.0/en/installation.html).

## Installation
After setting UP CakePHP3 project, you have to clone docker config from this repo using this command:

```
git clone https://github.com/RoBYCoNTe/cakephp3-docker.git
```

Edit your vhosts file adding this new line (this will enable navigation using localhost):
```
127.0.0.1 dev.local
```

## Usage
To use docker configuration just run this command inside your application's folder:

```
docker-compose -f docker/docker-compose.yml up
```

Open webpage [http://localhost:8880](http://localhost:8880) to see the result. 

# Warnings
Be patient, this is my first release, if you have something to share that can improve
this configuration file, just create a PR 👌!