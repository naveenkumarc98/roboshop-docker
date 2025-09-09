FROM node:20-alpine3.21 
RUN groupadd -r roboshop && useradd -r -g roboshop roboshop
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN npm install
RUN chown -R roboshop:roboshop /opt/server
ENV MONGO=true \
    MONGO_URL="mongodb://mongodb:27017/catalogue"
USER roboshop
CMD ["node","server.js"]