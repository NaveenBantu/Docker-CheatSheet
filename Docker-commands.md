# Docker Commands with examples

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
