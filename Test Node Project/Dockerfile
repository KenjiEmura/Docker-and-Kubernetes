
# DOCKER BASIC COMMANDS

# To actually create the Image, go to the path where the Dockerfile is located and run:
# docker build .
# That will run all the commands that are written on this file.

# To start a container based on the created image on port 3000 (The porject internally listens to port 80),
# get the image ID and run:
# docker run -p 3000:80 imageIdHere


FROM node

WORKDIR /app

COPY package.json /app

RUN npm install

COPY . /app

EXPOSE 80

CMD ["node", "server.js"]
