# Introduction
Provide a basic project to start a koa web server

## Source
https://github.com/VincentLinsanity/basic-koa-framework.git

## Version
Current Version: 0.0.0

## Maintainer
### Vincent Lin
### Vincentlinsanity@gmail.com

# Pre Requirement
- Nodejs
- Gulp
- MongoDB

If you are not start by docker, then you need to install nodejs first, 
all gulp require libary will install during npm install,
eventally you also need to install mongoDB and start it from
https://www.mongodb.org/

# Quick Start by Default
git clone project
```bash
$ git clone https://github.com/VincentLinsanity/basic-koa-framework.git
```

initial node_module
```bash
$ mkdir -p usr/src/webapp/basic-koa-framework && cd usr/src/webapp/basic-koa-framework
$ npm install
```

run server
```bash
$ npm start
```

# Quick Start by Docker
get docker-compose file
```bash
$ mkdir -p /home/docker/compose/basic-koa-framework
$ wget https://raw.githubusercontent.com/vincentlinsanity/basic-koa-framework/master/docker-compose.yml
```

run docker-compose
```bash
$ cd /home/docker/compose/basic-koa-framework
$ docker-compose up -d
```

# Compose Setting
- listen port 80:3000 for http protocol
- link mongo and expose port 27017

```
basickoaframework:
  image: vincentlinsanity/basickoaframework:latest
  links:
    - "mongo:mongo"
  ports:
    - "80:3000"
mongo:
  image: vincentlinsanity/mongodb:3.0.7
  expose:
    - 27017
  volumes:
    - '/home/docker/compose/meta/data/mongo:/data/db'
```
## environment example
- MONGO_ADDR = '10.36.62.101';
- MONGO_PORT = 27017;
- REDIS_ADDR = '10.36.62.101';
- REDIS_PORT = 6379;

# Build Docker Images
```bash
$ make docker-build
$ docker run -d -p 80:3000 vincentlin/basickoaframework:latest
```