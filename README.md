# narneso
Dockerized mongoDB server based on tutorial here:
https://dev.to/sonyarianto/how-to-spin-mongodb-server-with-docker-and-docker-compose-2lef

Additional configuration to load seed data on `docker-compose up`

## Understanding Docker

### Docker Volumes
A Docker volume is a path from the host file system into the Docker container.
- By mapping a connection from the host to the container, we can persist data:

  - Host Volume defined:

    - `docker run -v <host file path>:<container file path>`

  - By defining only the container file path to persist data from:

    - Anonymous Volume:

      - automatically created (`/var/lib/docker/volumes/<random-hash>/_data`)
      - `docker run -v `<container file path>`

  - By naming the volume:

    - Named Volume:

      - `docker volume create <volume name>`
      - `docker run -v name:<container file path>`
### Docker Containers
A Docker container is an instance of the Docker image that can be run. The Docker image defines the Docker container. Within the container, changes can be made to applications, services, environment, etc., but they will not persist if the container is deleted, or restarted using the Docker image's definition.
### Docker Images
A Docker image is an immutable template with instructions for creating a Docker container.
### Dockerfiles
A Dockerfile is a text file that defines an image. Essentially, this text file contains all of the commands necessary to create an environment and install applications, services, and environment to suit the purpose defined.  
### Docker Compose
A Docker Compose file is a YAML text file that defines all of the services that make up an application. Each service defined in the Docker Compose file will spin up its own Docker container. A project structure that utilizes multiple Dockerfiles and one docker-compose.yml files might look like this:
 ```
mainApplication/
 - subApplication1/
   - Dockerfile
 - subApplication2/
   - Dockerfile
 - subApplication3/
   - Dockerfile
 - docker-compose.yml
 ```
A Docker Compose file that utilizes Dockerfiles might simply state:
```
version: '3.x'

services:
  subApplication1:
    build: './subApplication1'
  subApplication2:
    build: './subApplication2'
  subApplication3:
    build: './subApplication3'
```
With this simple example, the Docker Compose file will build each Dockerfile, spinning up each micro-service with its own instructions and containers.

As mentioned above, Docker volumes can be named. In a Docker Compose file, the volume can be named as such:
```
version: '3.x'

services:
  mongodb:
    image: mongo
    ports:
      - 27017:27017
    volumes:
      - <volume name>:<container file path>
  volumes:
    <volume name>
```
The `volumes` property at the same indent as the named services would get all named volumes listed,

## helpful commands

- `docker-compose up -d` Build and run image in detached state
- `docker-compose stop` Stop containers without deleting
- `docker-compose start` Start containers
- `docker-compose restart` Start containers
- `docker-compose down` Stop and delete containers (volumes persist)
- `docker ps` List docker containers
- `docker ps -qa` List docker container ids
- `docker volume ls` List docker volumes
- `docker images` List docker images
- `docker stop $(docker ps -qa)` Stop images by listed ids
- `docker system prune` Removed stopped containers
- `docker system prune --volumes` prune volumes
- `docker system prune -a` Remove all unused images
- `docker rmi -f $(docker images -qa)` Force remove images by listed ids
- `mongo 127.0.0.1:20000/admin  -u root -p rootpassword` Connect to mongodb shell
