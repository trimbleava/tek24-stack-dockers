### Technology stack used by tek24 - nginx, postgres/postgis, redis, pgadmin4 Docker Images

```
using docker default network, tekstack_default, network enables containers to connect to and communicate with each other
using all dockers from https://hub.docker.com/ registry
close any pgadmin on web, before running compose, gives csf error, if not closed

set up .env 
set up compose.yml
docker compose up
docker compose down -v
```

#### Pgadmin4 Docker
http://localhost:5050 
```
beheenmt@gmail.com/pgadmin - tek24-db/postgres/postgres/host:same as service name (i.e. postgis in my case)
setup tk-tblsp -> /var/lib/postgresql/data --> C:/Users/BT/PROJECTS/TENANT_DATA/db_data
```

#### Postgres Docker
https://github.com/docker-library/docs/tree/master/postgres

```
docker volume create tek24_db_vol
mkdir ./TENANT_DATA
docker run --name tek24-postgres -v ./TENANT_DATA:/var/lib/postgresql/data -e POSTGRES_PASSWORD=mysecretpassword -d postgres:latest
# The default postgres user and database are created in the entrypoint with initdb.
docker ps
docker inspect -f '{{ .Mounts }}' b7efc6c8d5d0 <docker_id>

docker run -d \
  --name devtest \
  --mount source=myvol2,target=/app \
  nginx:latest
```
