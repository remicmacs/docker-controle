# Hobodoth

## Build the Node.js image

In the `project` subfolder:

```bash
docker build -t hobodoth:latest .
```

## Run the MongoDB image

```bash
docker volume create mongodbdata
docker run --rm --name mongo -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME:ISEN -e MONGO_INITDB_ROOT_PASSWORD:<ACTUAL_PASSWORD_HERE> -e MONGODB_DATABASE:IsenTP -v mongodbdata:/data/db mongo:latest
```

Run with environment variables to setup the database, user and password.