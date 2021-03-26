FROM node

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

# You can change the value of the "DEFAULT_PORT" with the --build-arg flag to build different images from the same source code.
ARG DEFAULT_PORT=80

ENV PORT $DEFAULT_PORT

EXPOSE $PORT

CMD ["npm", "start"]