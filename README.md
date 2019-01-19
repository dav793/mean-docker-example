# Example of docker containerization of a front-end, back-end and db.

* front-end is angular
* back-end is node + express + mongoose
* db is mongo

## Run entire system

```bash

    /> docker-compose up

```

* client: ```http://localhost:4200```
* server: ```http://localhost:8080```
* db: ```>/ mongo -u root -p example```

## Run a single container

### front-end

```bash
    cd client/template-frontend

```

### back-end

### db

## Notes

* DB is stored in ```./db```
* Configure DB root user in ```./docker-compose.yml```
* Configure backend environment in
    ** ```server/template-mongodb/config/environment.js```  - with mongo/mongoose```
    ** ```server/template-basic/config/environment.js```    - w/out mongo/mongoose```