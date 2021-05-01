## Create a laravel project:
docker-compose run --rm composer create-project --prefer-dist laravel/laravel .

## Build and start the containers:
```docker-compose up -d --build server```

Con el anterior comando también se inician los contenedores de mysql y nginx debido a que
dentro del docker-compose.yaml, el servicio "server" depende de estos dos servicios, (depends_on:)
por lo cual Docker los inicia automáticamente

--build hace que el docker-compose re evalúe si algún Dockerfile de algún servicio ha cambiado, y si es así,
se vuelven a construir las imágenes automáticamente.

## Run artisan commands:

```docker-compose run --rm artisan migrate```

El servicio de artisan es un "Util container" que usa PHP (el mismo Dockerfile del servicio "php"), y se usa para
correr el archivo "artisan" (lo puede ver en el ./src/artisan) usando php, para ello, se configura el entrypoint
de tal manera que se use el archivo artisan que está dentro del container, es decir, al usar:
```docker-compose run --rm artisan migrate```
lo que realmente se estaría corriendo sería:
```php artisan migrate```
dentro del contenedor, y como hay un bind volume dirigido al root folder del container (/var/www/html), este comando
se ejecutará en ese contexto.
