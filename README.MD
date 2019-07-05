# CakePHP3 with Docker

This repo contains basic configuration to run CakePHP 3 projects using Docker.
To get it working you have to create your project using composer like in this example:

`composer create-project --prefer-dist cakephp/app yourappname`

For more details about installation read the [https://book.cakephp.org/3.0/en/installation.html#](DOC).

## Installation
After that you can clone this repo inside created `yourappname` folder.

`git clone ...`

Edit your vhosts file adding new line:
`127.0.0.1 dev.local`

## Usage
To use the docker configuration.

`docker-compose -f docker/docker-compose.yml up`

Open webpage [http://localhost:8880](http://localhost:8880) to see your project UP & Running!