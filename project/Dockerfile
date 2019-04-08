# Image de base
FROM alpine:latest

# Installation de curl avec apt-get

RUN apk add --no-cache nodejs || \
    (sed -i -e 's/dl-cdn/dl-4/g' /etc/apk/repositories && apk add --no-cache nodejs) && apk add nodejs nodejs-npm


# Ajout du fichier de dépendances package.json
ADD package.json /project/

# Changement du repertoire courant
WORKDIR /project

# Installation des dépendances
RUN npm install

# Ajout des sources
ADD . /project/

# On expose le port 3000
EXPOSE 1234

# On lance le serveur quand on démarre le conteneur
CMD ["node", "app.js"]
