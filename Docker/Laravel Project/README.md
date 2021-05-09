# Insights

Los bind mounts se usan para tener acceso a las carpetas dentro de los contenedores y facilitar la fase de desarrollo
sin embargo, los archivos Dockerfile son los que se deben usar para copiar los "snapshots" del código de la aplicación
cuando se están construyendo (build) para producción, una vez la fase de desarrollo ha terminado.

Si no se incluye el ```COPY src-project-code-folder(local-files) destination-folder(container)``` en el Dockerfile, los contenedores
van a quedar vacíos cuando se hagan los build para porducción.

En resumen, es buena idea trabajar con bind mounts en el docker-compose.yaml para tener acceso al cóodigo dentro de los contenedores
y poder editarlo, pero de igual manera, hay que crear los Dockerfiles en donde se especifique qué carpetas se deben copiar dentro
de los contenedores al momento de hacer los build necesarios.