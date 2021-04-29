# Docker commands:

Make sure there are no "trash volumes".

Mongo:
docker run --name mongodb --rm -v data:/data/db -e MONGO_INITDB_ROOT_USERNAME=kenji -e MONGO_INITDB_ROOT_PASSWORD=secret -d --network multi-app mongo

Backend:
- CD into the backend folder (so the $PWD works)
- We still need to publish the 80:80 port so the React App (frontend) can communicate with the backend
- The -e flags have to match the environment variables defined in the Dockerfile, the values of those env variables should match the ones defined before when creating the database, those values are used in the app.js, line 87
  docker run --name goals-backend --rm --network multi-app -p 80:80 -v logs:/app/logs -v $PWD:/app -v /app/node_modules -e MONGODB_USERNAME=kenji -e MONGODB_PASSWORD=secret -d goals-node

Frontend:
- The react app runs on the client side, so we can't encapsulate this container inside the --network
- The -it flag must be used, it stands for "interactive mode", according to the --help, it keeps the STDIN open even if not attached, which apparently means, the server will be kept up and listening (not pretty sure about that last thing)
  docker run --name goals-frontend --rm -p 3000:3000 -it -d goals-react


Flags:
-e  -> Environment variables
-v  -> Volumes
-it -> Interactive mode