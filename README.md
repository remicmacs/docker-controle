# Hobodoth

## Build the Node.js image

In the `project` subfolder:

```bash
docker build -t hobodoth:latest .
```

## Run the MongoDB image

Run with environment variables to setup the database, user and password.

```bash
docker volume create mongodbdata
docker run --rm --name mongo -d -p 27017:27017 -e MONGODB_DATABASE:IsenTP -v mongodbdata:/data/db mongo:latest
```

## Run the node image

With the correct URI for MongoDB:

```bash
docker network create node-network
docker run --rm --name hobodoth-node --network node-network -p 8080:1234 -e MONGODB_URI="mongodb://mongo:27017/IsenTP" -d hobodoth:latest
```
