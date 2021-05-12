# Imperative approach
# How to start playing around with this project with kubernetes

- Install minikube and kubectl

- Start the minikube container ```minikube start``` which will create a container that runs the Kubernetes cluster

- Build the image of the container and push it to Docker Hub (the name that I used is kenjiemura/kub-first-app)

- Create a deployment based on the pushed image (the name of the deployment in this case is going to be 'first-app')
```kubectl create deployment first-app --image=kenjiemura/kub-first-app```

You can check the progress of the deployment running ```kubectl get deployments``` and ```kubectl get pods```
Also you can launch the minikube dashboard to have a visualization of everything, just run ```minikube dashboard```

- Expose the created deployment to a static IP adress
You can achieve that by using the next command:
```kubectl expose deployment first-app --type=LoadBalancer --port=8080```
the port is the one that is being listened from inside the app (app.js, line 16), and there are many --types, but we
are going to choose the LoadBalancer since is the most common option.

You can check the created service by running the command:
```kubectl get services```
Since we are running Kubernetes from minikube, the 'EXTERNAL-IP' column will remain '<pending>' forever.
To reach the deployed application, simply run the next command:
```minikube service first-app```
which will start a tunnel for the service that you created.

- Try crashing the app intentionaly with the /error route, you will see that the kubernetes will restart the container automatically.
This is a default behaviour, but you will also see that each time you crash the app, the time to restart the container will increase
also automatically to prevent falling into infinite loops of instant crashing and instant re running.
You can check the status of the pods in the minikube dashboard or by running ```kubectl get pods```

- You can also scale the project by running:
```kubectl scale deployment/first-app --replicas=3```
This command means that the Pod is going to be running 3 times.
If you run ```kubectl get pods``` you will see that you have your previous pod and 2 new ones




# To update a deployment with a new image:

Build the image and push it using a different tag, in this case this is the command that we ran:
```docker build -t kenjiemura/kub-first-app:2 .```
```docker push kenjiemura/kub-first-app:2```

Then run the next command:
```kubectl set image deployment/first-app kub-first-app=kenjiemura/kub-first-app:2```

And check the status with the next command:
```kubectl rollout status deployment/first-app```




# Check the history of updates and rollback to another deployment

Check the history with the next command:
```kubectl rollout history deployment/first-app```

Check a specific deployment with the --revision flag:
```kubectl rollout history deployment/first-app --revision=3```

Rollback to the latest working revision (working deployment):
```kubectl rollout undo deployment/first-app```

Rollback to a specific revision:
```kubectl rollout undo deployment/first-app --to-revision=1```

# Delete the deployment:
```kubectl delete deployment first-app```