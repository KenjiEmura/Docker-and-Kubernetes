FROM node

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 80

ENV MONGODB_USERNAME=root
ENV MONGODB_PASSWORD=secret
ENV MONGODB_URL=goals-app.tvcvu.mongodb.net
ENV MONGODB_NAME=goals-dev

CMD ["npm", "start"]