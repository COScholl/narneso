# narneso
dockerized mongoDB server based on tutorial here:
https://dev.to/sonyarianto/how-to-spin-mongodb-server-with-docker-and-docker-compose-2lef

## Understanding Docker

### Docker Containers
 A Docker container is an instance of the Docker image that can be run. The Docker images the Docker container. Within the container, changes can be made to applications, services, environment, etc., but they will not persist if the container is deleted, or restarted using the Docker image's definition.
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
With this simple example, the Docker Compose file will build each Dockerfile,
spinning up each micro-service with its own instructions and containers.
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
- `docker system prune --volumes` Remove stopped volumes
- `docker rmi -f $(docker images -qa)` Force remove images by listed ids
- `mongo 127.0.0.1:20000/admin  -u root -p rootpassword` Connect to mongodb shell
