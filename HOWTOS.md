# [Docker](https://www.docker.com/) HOW-TO's

## Running a command in interactive mode on a container
```
$ docker run -it --rm [image] [program]
```
**Note:** The command starts a container based on *[image]* and runs *[program]* in interactive mode (*-it*). When the container is stopped, all the state will be removed (*--rm*).

## Listing containers
```
$ docker ps
```
**Note:** `docker ps -a` lists all containers that have been exited as well.

## Inspect a container
```
$ docker inspect [container name or id]
```
**Note:** Retrieve a container name or id by running `docker ps`.

## Killing a container
```
$ docker kill [container name or id]
```
**Note:** Retrieve a container name or id by running `docker ps`.

## Downloading an image
```
$ docker pull [image]
```

## Uploading an image
```
$ docker push [image]
```

## Removing a container
```
$ docker rm [container name or id]
```

## Listing all images
```
$ docker images
```

## Removing an image
```
$ docker rmi [image ID or name]
```
**Note:** When an image is removed, all related containers are removed as well.

## Creating a new image
Create a Dockerfile extending an existing image and add some layers to it by copying files (using the **ADD** command), executing commands (using the **CMD** command), etc.
```
FROM jboss/wildfly
ADD standalone-custom.xml /opt/wildfly/standalone/configuration/
CMD ["/opt/wildfly/bin/standalone.sh", "-c", "standalone-custom.xml", "-b", "0.0.0.0", "-bmanagement", "0.0.0.0"]
```
## More about Dockerfiles
[Dockerfile Best Practices](https://docs.docker.com/articles/dockerfile_best-practices/)

## Building a new image from a Dockerfile
```
$ docker build -t image-name .
```
**Note:** **.** indicates that the Dockerfile is in the current directory.

## Finding a container IP address
```
$ docker ps
$ docker inspect [container name or ID]
```
**Note:** Look for IPAddress on the container JSON data.

## Port forwarding
```
$ docker run -it --rm -p 8080:8080 jboss/wildfly
```
**Note:** You may add as many *-p* parameters as needed.