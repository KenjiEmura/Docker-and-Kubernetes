# Steps to deploy a Docker container into AWS EC2

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




