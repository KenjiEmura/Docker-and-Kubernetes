We first started this project by setting up everything for the users-api service. For that we followed the next steps:

1. Tweeked a little bit the code by 'disabling' real requests made by axios.
2. Built the image and pushed it to Docker Hub.
3. Created the users-deployment.yaml file and applied the configurations.
4. Created the users-service. Services **give us a stable IP address that doesn't change all the time**, and also gives us access from outside the outside world

