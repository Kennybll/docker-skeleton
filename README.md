# Docker Telos Node

Basic scripts and config files for running a Telos node from a Docker container. There are separate mainnet and testnet for clarity but the set up is very similar.

**DISCLAIMER: this is provided as a basic skeleton to get you started. You'll need to test thoroughly and tune the configuration to make sure it meets your requirements. USE AT YOUR OWN RISK**

## Files

On each directory you'll find the following basic files:

- config.ini: basic [config skeleton sample](https://github.com/Telos-Foundation/telos/wiki/Telos:-config.ini) from Telos Foundation. You need to edit accordingly
- docker-compose-init.yml: Docker Compose config file to be used the first time the node is launched (genesis.json file is used to create database)
- docker-compose.yml: Docker Compose config file to be used once the node has been initialized
- Dockerfile: build instructions for the image, based on stock Ubuntu 18.04 and [build instructions](https://github.com/Telos-Foundation/telos/wiki/How-To-Install-Telos,-A-Block-Producer%E2%80%99s-Guide) from Telos Foundation
- genesis.json: the genesis file for each of the networks
- teclos.sh: simple script to have access to teclos on the running node

When the node is running you'll notice a volumes directory (see docker-compose.yml for details), this is where all persistent data is stored so it can be easily backed-up.

## Usage

**PRE-REQUISITES:** You'll need a recent version of [Docker](https://docs.docker.com/install/)
and [Docker Compose](https://docs.docker.com/compose/install/) installed on your machine

These are the basic steps to have a node running, provided you are using a correct config.ini:


Build the image (it will take a long time and take up to 20GB of disk space)
```
$ docker-compose build
```


Init the chain and state databases (Press CTRL+C once it's been initialized)
```
$ docker-compose -f docker-compose-init.yml up
```


Start the node
```
$ docker-compose up -d
```


Check the logs of the running node
```
$ docker-compose logs 
```


Get node info
```
$ ./teclos.sh get info
```


See node status
```
$ docker-compose ps
```


Stop the node
```
$ docker-compose stop
```
