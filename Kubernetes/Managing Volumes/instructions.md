# Using volumes with Kubernetes

Although volumes can survive container destruction, its lifetime depends on the Pod's lifetime since the volumes and the containers are being held in the same pod.

If you remove a container, the volume will survive, if you remove the pod, by default, the volume will not survive.

That's why we want to use persistent volumes.

