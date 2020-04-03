# narneso
dockerized mongoDB server based on tutorial here:

https://dev.to/sonyarianto/how-to-spin-mongodb-server-with-docker-and-docker-compose-2lef

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
