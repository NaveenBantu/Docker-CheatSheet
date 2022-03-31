# Docker Commands with examples


## Showing all the Docker images
    docker images -a
    
## Removing all Docker images
    docker rmi $(docker images -a -q)
When the -q flag is passed to rmi, all the images are removed
[How to remove Docker containers and volumes](https://www.digitalocean.com/community/tutorials/how-to-remove-docker-images-containers-and-volumes)


## Assigning Ports to a container
The port can be assigned to a container by -p command
The port mapping has to be done from host to container
    
### While starting a container
    docker run -it -p <host-port>:<container-port> <docker-image>

## Network:

### Create docker network:
    docker network create mongo-network

### Remove docker network:
    docker network rm mongo-network

## Install and start a service
With the below command we can pull a docker image and run the image as a container. We have a mongo db service example below:

    docker run-d \
    -p 20717:20717 \
    -e MONGO_INITDB_ROOT_USERNAME=admin \
    -e MONGO_INITDB_ROOT_PASSWORD=password \
    --net mongo-network \
    --name mongodb \
    mongo

- before running the container, the docker image "mongo" is pulled from official docker repository.
- name "mongodb" is assigned to the running container.
- ports are mapped <host:container> (20717:20717).
- environment variables are assigned.
