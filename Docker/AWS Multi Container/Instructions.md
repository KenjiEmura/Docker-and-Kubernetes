# Deploying to AWS ECS

No es buena idea usar docker-compose para deployment, ya que como vimos antes, en el deploy no se deben poner
volumes ni bindings, ya que no tiene sentido enlazar carpetas internas del contenedor, con carpetas externas que igual
siguen siendo "internas" del servidor, es decir, desde nuestro sistema local, no tenemos fácil acceso a esas carpetas
no importa que usemos bindings.

Es por esto, que los archivos Dockerfile juegan un papel super importante en la fase de deployment de nuestro proyecto.
El archivo de docker-compose lo podemos usar como una guía para desplegar los servicios (containers) uno por uno.

