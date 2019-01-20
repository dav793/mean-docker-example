# Example of docker containerization of a front-end, back-end and db.

* front-end is angular
* back-end is node + express + mongoose
* db is mongo

## Set path to DB on host
* in docker-compose.yml, replace ```<path to db on host>``` with your own path

## Run entire system

```bash

    /> docker-compose up

```

* client: ```http://localhost:4200```
* server: ```http://localhost:8080```
* db: ```>/ mongo -u root -p example -authenticationDatabase admin```

## Run a single container

### front-end

```bash
    cd client/template-frontend
    docker build -t <image tag> .
    docker run --name <container name> -p 4200:4200 <image tag>
```

### back-end (will not connect to mongo container if run as individual container. use docker-compose)

```bash
    cd server/template-mongodb
    docker build -t <image tag> .
    docker run --name <container name> -p 8080:8080 <image tag>
```

### db

```bash
    docker run --name <container name> -p 27017:27017 -v /Users/david/Workspace/testMeanDocker/db:/data/db -e MONGO_INITDB_ROOT_USERNAME=root -e MONGO_INITDB_ROOT_PASSWORD=example mongo:3.4.18-jessie
    mongo -u root -p example -authenticationDatabase admin < server/template-mongodb/scripts/createDatabase.js
    mongo -u root -p example -authenticationDatabase admin < server/template-mongodb/scripts/populateDatabase.js
```

## Notes

* DB is stored in ```./db```
* Configure DB root user in ```./docker-compose.yml```
* Configure backend environment in\
    ```server/template-mongodb/config/environment.js - with mongo/mongoose```\
    ```server/template-basic/config/environment.js - w/out mongo/mongoose```