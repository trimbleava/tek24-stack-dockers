### Technology stack used by tek24 - nginx, postgres/postgis, redis, pgadmin4 Docker Images

```
to use this must clone the repo and run it manually: 
docker compose up
steps:
created a docker network, tekstack-shared-network, network enables containers to connect to and communicate with each other
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
created an external pgadmin volume pgadmin_data running in shared network
go to TENANT_DATA directory, create another dir called tenant_data and use as volume in docker compose 
login to pgadmin: beheenmt@gmail.com/pgadmin
register server: tek24-db/postgres/postgres/<host> -- same as service name (i.e. postgis in my case)
setup tk-tblsp -> /var/lib/postgresql/data --> C:/Users/BT/PROJECTS/TENANT_DATA/tenant_data
```

#### Postgres Docker
https://github.com/docker-library/docs/tree/master/postgres

```
Below is the instruction to run postgres docker, we are using postgis docker that contains both, see below.
mkdir ./TENANT_DATA/<volume_data>
docker volume create only exists in run command:
docker run --name tek24-postgres -v ./TENANT_DATA/db_data:/var/lib/postgresql/data -e POSTGRES_PASSWORD=mysecretpassword -d postgres:latest
# The default postgres user and database are created in the entrypoint with initdb.
docker ps
docker inspect -f '{{ .Mounts }}' b7efc6c8d5d0 <docker_id>

docker run -d \
  --name devtest \
  --mount source=host_path/myvol2,target=/app \
  nginx:latest
```
### Postgis Docker
https://hub.docker.com/r/postgis/postgis - installs the postgres with it

```commandline
created external volume tenant_data for holding tenants data
created external volume dbbackups 
installed .env file to read the variables from
attach to pgadmin4 docker to see both tenant data and the backups
conection params located in .env
running on the shared network tekstack-shared-network
```
### Nginx Docker
https://hub.docker.com/_/nginx 
TBA

### Redis Docker
https://hub.docker.com/_/redis
TBA