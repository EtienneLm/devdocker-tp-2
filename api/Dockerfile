FROM node:22-alpine

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY src ./src

EXPOSE 3000

ENTRYPOINT ["node"]

CMD ["src/server.js"]