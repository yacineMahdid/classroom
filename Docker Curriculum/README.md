# Docker for beginners
[Link to the tutorial](https://docker-curriculum.com/)

## Notes
- docker = os-level virtualization on Linux. Lightweight compared to VM. Can run an app anywhere with docker.
- I need to first install docker by going over here: https://docs.docker.com/engine/install/ubuntu/#install-using-the-repository

Here is some nice to have terminology:
- Images - The blueprints of our application which form the basis of containers. In the demo above, we used the docker pull command to download the busybox image.
- Containers - Created from Docker images and run the actual application. We create a container using docker run which we did using the busybox image that we downloaded. A list of running containers can be seen using the docker ps command.
- Docker Daemon - The background service running on the host that manages building, running and distributing Docker containers. The daemon is the process that runs in the operating system which clients talk to.
- Docker Client - The command line tool that allows the user to interact with the daemon. More generally, there can be other forms of clients too - such as Kitematic which provide a GUI to the users.
- Docker Hub - A registry of Docker images. You can think of the registry as a directory of all available Docker images. If required, one can host their own Docker registries and can use them for pulling images.

- We can pull already pre-bundled image from docker hub and then run them locally. We can then run the containers in detached mode with port open so that they can access stuff on our computer.
- Wow this will simplify so much the development if we just have a container running.
- image can be commited like a git repository
- Base image have no parent image, child image are based on some base image with added functionalities.
- You have to be careful though, if you do `sudo docker run -p 8888:5000` the app will be at localhost:8888
- as soon as it is in a docker repository it is super easy to setup and get up and running!
- ELB allow for docker image upload
- with ubuntu base image pip gave me some issues I had to install pip3 instead:
```docker
# install system-wide deps for python and node
RUN apt-get update && apt-get install -y --no-install-recommends \
    python3.5 \
    python3-pip \
    && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
```

Currently at Docker Network