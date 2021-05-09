# Steps to deploy a Docker container into AWS EC2

## Remote machine side:

### 1. Create an EC2 instance on AWS
- Go to AWS and follow the instructions to create an EC2 instance using amazon linux extras
- Download the key file (.pem), make sure is ignored in the .gitignore file
- Once the instance is up and running, go to 'Connect' and SSH client
- Follow the steps and you should be connected to the remote machine

### 2. Ensure all essential packages are up to date
- ```sudo yum update -y```

### 3. Install Docker
- ```sudo amazon-linux-extras install docker```
On other service providers different than AWS, you can check the documentation here:
https://docs.docker.com/engine/install/

### 4. Start Docker
- ```sudo service docker start```


## Local computer side:

First you need to build and push the built image to Docker Hub, so later you can pull it from the remote machine (AWS).

### 1. Create a Docker Hub repository that will contain the built image
Go to Docker Hub and create the repository, you will get the name that you have to use when you build your image,
in this particular case, the repository's name is ```kenjiemura/node-aws-deploy-test```                                                                                                                                    git:main*


### 2. Make sure that you add a .dockerignore file
You have to exclude all the sensitive information like the key file to connect to AWS (***.pem)

### 3. Build the image
Build the image ```docker build -t kenjiemura/node-aws-deploy-test .```
If you didn't build the image using the correct name, you can change it with the ```docker tag``` command
For example: ```docker tag incorrect-image-name kenjiemura/node-aws-deploy-test```,
The original incorrect named image will still be there, but you can delete it later.

### 4. Push the image to Docker Hub
You have to be logged in. When you are logged in, just run the next command:
```docker push kenjiemura/node-aws-deploy-test```

### 5. Check the image was successfully pushed to Docker Hub
Go to Docker Hub and check that the image was successfully pushed.


## Remote machine side:

### 5. Start the container used the built and pushed image
Run the next command on the EC2:
```sudo docker run -d --rm -p 80:80 kenjiemura/node-aws-deploy-test```

### 6. Make sure that the inbound rules of the EC2 container accepts http requests
Go to the EC2 Instance, click on the instance that we are working on, then "Security", then click on the "Security Groups"
that this EC2 Instance have, and add the inbound rule if needed.
