## MongoDB Dockerfile


This repository contains **Dockerfile** of [PostgreSQL](https://www.postgresql.org/) for [Docker](https://www.docker.com/).

### Installation

1. Install [Docker](https://www.docker.com/).

### Build
```shell
docker build -t="yourdockerusername/postgresql" github.com/acrossthecloud/postgresql
```



### Usage

#### Run `mongod`

    docker run -d -p 27017:27017 --name mongodb dockerfile/mongodb

#### Run `mongod` w/ persistent/shared directory

    docker run -d -p 27017:27017 -v <db-dir>:/data/db --name mongodb dockerfile/mongodb

#### Run `mongod` w/ HTTP support

    docker run -d -p 27017:27017 -p 28017:28017 --name mongodb dockerfile/mongodb mongod --rest --httpinterface

#### Run `mongod` w/ Smaller default file size

    docker run -d -p 27017:27017 --name mongodb dockerfile/mongodb mongod --smallfiles

#### Run `mongo`

    docker run -it --rm --link mongodb:mongodb dockerfile/mongodb bash -c 'mongo --host mongodb'

##### Usage with VirtualBox (boot2docker-vm)

_You will need to set up nat port forwarding with:_  

    VBoxManage modifyvm "boot2docker-vm" --natpf1 "guestmongodb,tcp,127.0.0.1,27017,,27017"

This will allow you to connect to your mongo container with the standard `mongo` commands.
