# Containers inside the same pod
For containers inside the same pod, you can access each other (from the same pod) just using localhost, if inside your code there is an
environment variable that receives the path to access another container that will be running inside the same pod, you can just plugin that
variable below the image definition of the container, and use localhost as the value.


# Kubernetes auto generated services IP environment variables
By default, kubernetes will generate environment variables that contains the IP address of our services with the next format
The service's name all in caps, if there is a '-' replace it with '_' then after the service's name, put _SERVICE_HOST
For example, if our service's name is auth-service, the auto generated name will be AUTH_SERVICE_SERVICE_HOST, we can directly inject that
environment variable into our code (users-app.js lines 26 and 57)


# DNS for Pod-to-Pod communication
Kubernetes out of the box, uses a service called CoreDNS, which allows us to use domain names inside our cluster, this can be achieved simply
by using the name of the service, add a dot (.) and the namespace (namespaces are used to group stuff, it's for large projects). The default
namespace is default, so for example, to access the auth-service from the users container, in the user's container definition, we can define
an env variable that holds the auth-service namespace which is "auth-service.default"