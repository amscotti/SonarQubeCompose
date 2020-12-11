# SonarQube with Docker Compose
Using Docker Compose this will create a SonarQube server with a PostgreSQL database with all data saved into Docker volumes.

## Prerequisites
Docker and Docker Compose, both of which are installed with [Docker Desktop for Mac](https://www.docker.com/products/docker-desktop)

## Commands
* `docker-compose up` - Creates everything based on the `docker-compose.yml`
* `docker-compose stop` - Stops all the services
* `docker-compose down` - Stops and removes all everything, but leave the volumes with all the saved data

## Scanning a project using the sonar-scanner in Docker
Using `sonarsource/sonar-scanner-cli` you can scan a project by mounting your project folder into the container. 

```bash
docker run \
    --rm \
    -e SONAR_HOST_URL="http://localhost:9000" \
    -v "<Full Path To Repository>:/usr/src" \
    --network="host" \
    sonarsource/sonar-scanner-cli
```