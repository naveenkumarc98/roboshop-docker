FROM node:20-alpine3.21 AS builder
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN npm install

FROM node:20-alpine3.21
RUN addgroup -S roboshop && adduser -S robo -G roboshop
ENV MONGO=true \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
WORKDIR /opt/server
COPY --from=builder /opt/server /opt/server
USER robo
CMD ["node","server.js"]