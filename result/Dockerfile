FROM node:13-alpine

WORKDIR /res-app

COPY package*.json ./

RUN npm install

COPY server.js .

COPY views ./views

CMD ["node", "server.js"]
