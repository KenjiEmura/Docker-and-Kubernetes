FROM node:14-alpine

WORKDIR /app

# A diferencia del "CMD", el "ENTRYPOINT" lo que hace es añadir el comando ingresado en el command line
# a lo que uno ponga después del "ENTRYPOINT", por ejemplo si el comando es "docker run -it node init",
# lo que va a pasar es que lo que realmente se va a ejecutar es "docker run -it node npm init",
# si usáramos "CMD [ "npm "]", el comando ingresado en el command line SOBRESCRIBE el comando 
# ingresado con CMD, por lo cual siguiendo con el ejemplo anterior, si quisiéramos correr "docker run -it node init",
# al usar CMD en el Dockerfile, lo que realmente correríamos sería "docker run -it node init", pues el "init"
# sobrescribiría todo.
ENTRYPOINT [ "npm" ]