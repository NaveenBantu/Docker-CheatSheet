In an docker-compose yaml file can define the following parameters:

## Version:


## Containers:

### Ports:
Expose ports. Either specify both port (HOST:CONTAINER), or just the container port (a random host port will be chosen).

Ports mentioned in docker-compose.yml will be shared among different services started by the docker-compose.
Ports will be exposed to the host machine to a random port or a given port.
    
The ports section will publish ports on the host. Docker will setup a forward for a specific port from the host network into the container. By default this is implemented       with a userspace proxy process (docker-proxy) that listens on the first port, and forwards into the container, which needs to listen on the second point. If the container is     not listening on the destination port, you will still see something listening on the host, but get a connection refused if you try to connect to that host port, from the failed forward into your container.

    Note, the container must be listening on all network interfaces since this proxy is not running within the container's network namespace and cannot reach 127.0.0.1 inside       the container. The IPv4 method for that is to configure your application to listen on 0.0.0.0.

    Also note that published ports do not work in the opposite direction. You cannot connect to a service on the host from the container by publishing a port. Instead you'll         find docker errors trying to listen to the already-in-use host port.
    
### Expose:
Expose ports without publishing them to the host machine - they’ll only be accessible to linked services. Only the internal port can be specified.

With Expose, ports are not exposed to host machines, they are only exposed to other services.
    
    Expose is documentation. It sets metadata on the image, and when running, on the container too. Typically you configure this in the Dockerfile with the EXPOSE instruction, and     it serves as documentation for the users running your image, for them to know on which ports by default your application will be listening. When configured with a compose         file, this metadata is only set on the container. You can see the exposed ports when you run a docker inspect on the image or container.


## Volumes:


## Networks:
