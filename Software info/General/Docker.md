-   **ADD** – Defines files to copy from the Host file system onto the Container
	-   ADD ./local/config.file /etc/service/config.file
-   **CMD** – This is the command that will run when the Container starts
    -   CMD [“nginx”, “-g”, “daemon off;”]
-   **ENTRYPOINT** – Sets the default application used every time a Container is created from the Image. If used in conjunction with CMD, you can remove the application and just define the arguments there
    -   CMD Hello World!
    -   ENTRYPOINT echo
-   **ENV** – Set/modify the environment variables within Containers created from the Image.
    -   ENV VERSION 1.0
-   **EXPOSE** – Define which Container ports to expose
    -   EXPOSE 80
-   **FROM** – Select the base image to build the new image on top of
    -   FROM ubuntu:latest
-   **LABEL maintainer** – Optional field to let you identify yourself as the maintainer of this image. This is just a label (it used to be a dedicated Docker directive).
    -   LABEL maintainer=someone@xyz.xyz”
-   **RUN** – Specify commands to make changes to your Image and subsequently the Containers started from this Image. This includes updating packages, installing software, adding users, creating an initial database, setting up certificates, etc. These are the commands you would run at the command line to install and configure your application. This is one of the most important dockerfile directives.
    -   RUN apt-get update && apt-get upgrade -y && apt-get install -y nginx && rm -rf /var/lib/apt/lists/*
-   **USER** – Define the default User all commands will be run as within any Container created from your Image. It can be either a UID or username
    -   USER docker
-   **VOLUME** – Creates a mount point within the Container linking it back to file systems accessible by the Docker Host. New Volumes get populated with the pre-existing contents of the specified location in the image. It is specially relevant to mention is that defining Volumes in a Dockerfile can lead to issues. Volumes should be managed with docker-compose or “docker run” commands. Volumes are optional. If your application does not have any state (and most web applications work like this) then you don’t need to use volumes.
    -   VOLUME /var/log
-   **WORKDIR** – Define the default working directory for the command defined in the “ENTRYPOINT” or “CMD” instructions
    -   WORKDIR /home



### Dockerfile vs Docker compose

A Dockerfile is a simple text file that contains the commands a user could call to assemble an image whereas Docker Compose is a tool for defining and running multi-container Docker applications.

Docker Compose define the services that make up your app in docker-compose.yml so they can be run together in an isolated environment. It gets an app running in one command by just running docker-compose up. Docker compose uses the Dockerfile if you add the build command to your project’s docker-compose.yml. Your Docker workflow should be to build a suitable Dockerfile for each image you wish to create, then use compose to assemble the images using the build command.

#### Your Docker workflow should be to build a suitable `Dockerfile` for each image you wish to create, then use compose to assemble the images using the `build` command.


## Data persistence
In order to persist data for example a DB from a container to an outside source u must map the internal to external source
`docker run -v /opt/datadir:/var/lib/mysql <image name?` 

## Command vs Entrypoint

`CMD` --> stands for **Command** and defines the program when the container starts
`CMD["command", "param"]`

`ENTRYPOINT` --> makes the user enter a default value to start a container

## Networks

When docker is installed it creates three networks automatically
- **Bridge network**: is a private internal network created by Docker on the host. All containers attached to this network by default and they get an internal IP address usually in the range of  172.17 series. the containers can access each other using this internal IP if required to access any of these containers from the outside world map the ports of these containers to ports on the docker host as we have seen before the container to the host network.
- **Host Network**: Another way to access the containers externally is to associate the container to the host network. This takes out any network isolation between the docker host and the docker container. Meaning if you were to run a web server on Port 5000 in a web container it is automatically as accessible on the same port externally without requiring any port mapping as the web container uses the hosts network. This would also mean that unlike before you will now not be able to run multiple web containers on the same host on the same port as the ports are now common to all containers in the host network with the none network.
- **None Network**:  The containers are not attach to any network and doesn't have any access to the external network or other containers they run in an isolated network.

In Docker, creating a new network apart from the initial three (bridge, host, and none) offers several benefits and use cases that are crucial for organizing and managing containerized applications effectively:

1. **Isolation and Security**: Creating a new network allows you to isolate containers from each other. By placing containers in separate networks, you can control communication and enhance security. Containers in one network cannot communicate with containers in another network unless you explicitly allow it.
    
2. **Custom Network Configuration**: Custom networks provide the flexibility to define specific network configurations, such as IP address ranges, subnets, and gateways, tailored to the needs of your applications. This is particularly useful in complex applications that require precise network setups.
    
3. **Service Discovery**: Custom networks enable automatic service discovery using container names. Containers on the same custom network can resolve each other by name, which simplifies inter-container communication without needing to hard-code IP addresses.
    
4. **Multi-host Networking**: Using Docker's overlay network driver (often in conjunction with Docker Swarm), you can create networks that span multiple hosts. This is essential for distributed applications and services that need to communicate across different physical or virtual machines.
    
5. **Enhanced Networking Features**: Custom networks can be configured to use advanced networking features such as DNS-based service discovery, encryption, and network policies. These features help in building more robust and secure containerized applications.
    
6. **Control Traffic Flow**: By creating separate networks for different parts of your application, you can control the flow of traffic. For example, you can segregate frontend and backend services into different networks, controlling access and enhancing security.
## Commands
`docker version`
`docker run <image>` --> runs a container from an image
`docker run -d <image>` --> runs a container in detached mode
`docker run redis:<tag number>`
`docker run -p outside port : container port`
`docker ps` --> lists all current conatiners
`docker ps -a`  --> lists all containers even if they are not running
`docker stop <container name>`
`docker rm <container name>` --> remove a container
`docker images` --> list all images
`docker rmi <image name>` --> remove an image
`docker pull <image name>`
`docker exec <container name>` --> run a command
`docker inspect <container name>`
`docker logs <container name>`
`docker network ls` --> see all networks
