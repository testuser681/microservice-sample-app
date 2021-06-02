FROM node:13-alpine

WORKDIR /res-app

COPY package*.json ./

RUN npm install

COPY server.js .

CMD ["node", "server.js"]