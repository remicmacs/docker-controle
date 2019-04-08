# :whale: Hobodoth

[![CircleCI](https://circleci.com/gh/rodolpheh/docker-controle/tree/master.svg?style=shield)](https://circleci.com/gh/rodolpheh/docker-controle/tree/master)

- [:construction_worker: Build the Node.js image](#constructionworker-build-the-nodejs-image)
- [:checkered_flag: Run the MongoDB image](#checkeredflag-run-the-mongodb-image)
- [:checkered_flag: Run the Node.js image](#checkeredflag-run-the-nodejs-image)
- [:package: Using docker-compose](#package-using-docker-compose)

## :construction_worker: Build the Node.js image

In the `project` subfolder:

```bash
docker build -t hobodoth:latest .
```

## :checkered_flag: Run the MongoDB image

Run with environment variables to setup the database, user and password.

```bash
docker volume create mongodbdata
docker run --rm --name mongo -d -p 27017:27017 -e MONGODB_DATABASE:IsenTP -v mongodbdata:/data/db mongo:latest
```

## :checkered_flag: Run the Node.js image

With the correct URI for MongoDB:

```bash
docker network create node-network
docker run --rm --name hobodoth-node --network node-network -p 8080:1234 -e MONGODB_URI="mongodb://mongo:27017/IsenTP" -d hobodoth:latest
```

## :package: Using docker-compose

Use the docker-compose.yml file to pull and run both images. From the `project` folder:

```bash
docker-compose up
```