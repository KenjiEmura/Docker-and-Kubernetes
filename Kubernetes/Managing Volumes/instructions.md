# Using volumes with Kubernetes

Although volumes can survive container destruction, its lifetime depends on the Pod's lifetime since the volumes and the containers are being held in the same pod.

If you remove a container, the volume will survive, if you remove the pod, by default, the volume will not survive.

That's why we want to use persistent volumes.



# Persistent volumes:

1. Define the persistent volume's resource
There are many persistent volume types, the one that we are going to use here is still going to be the hostPath mode since we are running locally
a small minikube project, but we have to keep in mind that there are way more kinds of persitent volumes which configuration will differ from each other
No matter which persistent volume we choose, we have to create the volume's resource in an independant yaml file (see host-persistent-volume.yaml)

2. Define the 'claim' through which the pods are going to access the persistent volume
See the host-persistent-volume-claim.yaml to see the details of how the file was created.

3. Make sure that in the deployment configuration file, on the pod's definition, you include the 'persistentVolumeClaim' under the volumes property,
see the master-deployment.yaml file for more details

4. Apply the persistent volume configuration
```kubectl apply -f host-persistent-volume.yaml```

5. Apply the claim configuration
```kubectl apply -f host-persistent-volume-claim.yaml```

5. Apply the updated deployment configuration
```kubectl apply -f master-deployment.yaml```



# Environment Variables:

We could use something like this in the master-deployment.yaml file:
```
env:
  - name: STORY_FOLDER
    value: "story"
```
But instead, it's better to use a ConfigMap resource provided out of the box by Kubernetes. First create the environment.yaml file (name it as you wish)
then under the 'data' property, add all the key - value pairs that you need. Once you are done with that, apply the configuration to the cluster:
```kubectl apply -f environment.yaml```

Once the data is 'applied' to our cluster, we can then go to the master-deployment.yaml configuration file and set the 'env:' property like this:
