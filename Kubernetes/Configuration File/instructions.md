# How to run Kubernetes with configuration files:

```kubectl apply -f deployment.yaml```
```kubectl apply -f service.yaml```

OR ```kubectl apply -f=deployment.yaml,service.yaml```


# Expose the service with minikube:
The backend corresponds to the name of the service specified in the metadata section of the file.
```minikube service backend```


# Updating the resources:
Simply make the changes you need inside the configuration files and run the apply command of the file(s) you changed.
```kubectl apply -f deployment.yaml```
```kubectl apply -f service.yaml```


# Deleting resources:
```kubectl delete -f=deployment.yaml,service.yaml```

You can also select which resources to delete based on their labels, for example:
```kubectl delete deployments,services -l sample-group-label=group-1```
So this will be read like: "delete all the deployments and services that have a label "sample-group-label" with value of "group-1"