FROM node:25.6.0-bookworm
WORKDIR /app

COPY . .
EXPOSE 3000

COPY package*.json ./

ENTRYPOINT start npm
