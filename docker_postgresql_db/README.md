# PostgreSQL Database with Docker Compose

Docker Compose file helps to initiate a PostgreSQL Database, with an attached persistant volume. As Postgre is an open source database, it could be used to various projects, due to it's functionrich design and wide selection of available extensions.

## Set-up PostgreSQL Database

 1. Install docker and docker compose
    - Docker Engine: https://docs.docker.com/engine/install/
    - Docker Compose: https://docs.docker.com/compose/install/
 2. Create a folder for the part of the PostgreSQL Docker instance - e.g.: docker_postgresql
 3. Create a folder for the part of the database, so we won't lost data if we shut down the instance - e.g.: postgresql_db_volume
 4. Create docker-compose.yml file contains the following:

```
version: '3.9'

services:
  postgres:
    image: postgres
    ports:
      - 5432:5432
    volumes:
      - /path/of/your/folder/postgresql_db_volume:/var/lib/postgresql/database
    environment:
      - POSTGRES_USER=postgres
      - POSTGRES_PASSWORD=yourpassword
      - POSTGRES_DB=dev # OPTIONAL
      - POSTGRES_SCHEMA=raw_data # OPTIONAL
```
 5. In the terminal move to the root folder which contains the docker-compose.yml file - in our case: docker_postgresql
 6. Use the following Docker commands to
    - Start instance: docker-compose up -d
    - Verify container: docker ps
    - Stop instance: docker-compose down

## Resources

 - https://hub.docker.com/_/postgres
 - https://www.docker.com/blog/how-to-use-the-postgres-docker-official-image/
 - https://medium.com/@agusmahari/docker-how-to-install-postgresql-using-docker-compose-d646c793f216
