## Create a laravel project:
docker-compose run --rm composer create-project --prefer-dist laravel/laravel .

Build and start the containers:
docker-compose up -d server

Con el anterior comando también se inician los contenedores de mysql y nginx debido a que
dentro del docker-compose.yaml, el servicio "server" depende de estos dos servicios, (depends_on:)
por lo cual Docker los inicia automáticamente