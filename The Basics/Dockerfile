FROM node

# If we don't setup the WORKDIR, all the subsequent commands ADD, COPY, CMD, ENTRYPOINT or RUN
# will run on the root folder where the image is running we don't want that, so we create a subfolder /any-name

WORKDIR /app

# COPY . ./ has 2 paths, the left dot means copy everything from the folder where this Dockerfile is located
# the second dot will mean that those copied files will go to the root of the working directory
# still, it is good to be extra explicit where do we want our files to be copied by adding the absolute path
COPY . /app

RUN npm install