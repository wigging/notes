# Docker

Some useful commands for working with Docker images and containers. An overview of various Docker commands are discussed below. The commands were tested on a Mac but they should be similar on other systems. Name of the image is represented by `<image>`. Name of the container is represented by `<container>` while name of a volume is represented by `<volume>`.

## Images

```bash
# List all image on your local computer
docker images
```

```bash
# Remove an image using the `IMAGE ID`
# 123456 is the `IMAGE ID` of the Docker image
docker rmi 123456
```

```bash
# Build a Docker image from a Dockerfile
# Run command from within folder containing the Dockerfile
# Name the new image with the -t option, in this example name is `myimage`
docker build -t myimage .
```

## Containers

```bash
# Run an interactive container from an image and start at a bash prompt
# The -i option is for interactive mode, -t is for TTY
docker run -it <image> bash
```

```bash
# Run a named interactive container from an image and start at a bash prompt
# The --name option gives a name to the container
# The -i option is for interactive mode, -t is for TTY
docker run --name <container> -it <image> bash
```

```bash
# Show all running containers
docker ps

# Show all running and stopped containers
docker ps -a
```

```bash
# Remove a stopped container
docker rm <container>

# Stop and remove a running container
docker rm -f <container>

# Start a stopped container in interactive mode
docker start -i <container>
```

## Volumes

```bash
# List all volumes seen by Docker
docker <volume> ls

# Remove a volume
docker volume rm <volume>
```

```bash
# Removing containers that were not created with the -v option can cause
# dangling volumes which are no longer referenced by a container. To find
# dangling volumes use the command:
docker volume ls -f dangling=true
```

## Files

```bash
# Copy files from a Docker container to the host machine
docker cp <container>:/file/path/within/container /host/path/
```

## Run JupyterLab from a container

```bash
# Create and run a new container and publish its ports to the host machine
docker run --name <container> -it -p 8888:8888 <image> bash

# From within the container run JupyterLab
jupyter lab --ip 0.0.0.0 --no-browser --allow-root
```

After starting JupyterLab in the container, use the URL given in the terminal to access JupyterLab from a web browser on the local machine. Notice the token is appended to the URL.

```bash
# Example of URL produced from the previous command
localhost:8888/?token=577b3e0fb95dc26b2491b0a57b5b8ffdf33c7f94792e7948
```
