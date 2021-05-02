
# DOCKER BASIC COMMANDS

# To actually create the Image, go to the path where the Dockerfile is located and run:
# docker build .
# That will run all the commands that are written on this file.

# To start a container based on the created image on port 3000 (The porject internally listens to port 80),
# get the image ID and run:
# docker run -p 3000:80 imageIdHere



# -------------------------------------------------------------------------------------------------------------



FROM node

# If we don't setup the WORKDIR, all the subsequent commands ADD, COPY, CMD, ENTRYPOINT or RUN
# will run on the root folder where the image is running we don't want that, so we create a subfolder /any-name.

WORKDIR /app

# COPY . ./ has 2 paths, the left dot means copy everything from the folder where this Dockerfile is located
# the second dot will mean that those copied files will go to the root of the working directory
# still, it is good to be extra explicit where do we want our files to be copied by adding the absolute path.
COPY . /app

# This is the command that we want to execute inside our working directory, in this particular case,
# we will install all the dependencies of this node project.
RUN npm install



# -------------------------------------------------------------------------------------------------------------
# Until here, these were the instructions to create the IMAGE, and from now, we will put the commands
# that will be run when a CONTAINER IS STARTED based on the image.
# -------------------------------------------------------------------------------------------------------------



# In our server.js (line 46) we are listening to port 80, but since this is running in a container, the port will
# only listen inside the container, so we have to expose that port to our machine, however, the EXPOSE command
# doesn't really do anything, it is only for documentation purposes. In order to effectively expose our port to
# the local system, we have to add the "-p" flag (which stands for publish, not for port 🤷🏻‍♂️) when we start our container
# and then indicate which port should we use. In short, we should run the next command: 
# docker run -p 3000:80 imageIdHere
EXPOSE 80

# CMD will execute commands when the container is created, it should be the las command on the Dockerfile
# we have to separte all the elements of the command into strings and pass it as an array
# i.e. "node server.js" will become ["node", "server.js"]
CMD ["node", "server.js"]
