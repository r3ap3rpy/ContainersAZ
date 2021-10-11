### Image and Container management

**docker images** shows the available images.

**docker rmi centos:centos6** deletes the image, the **-f** can forcefully remove them but if a layer is referenced in other images it will isse a warning.

The DockerFile defines the look of our images and the actions to customer any base image according to our needs.

``` bash
FROM debian:stable
MAINTAINER latest123 <latest123@linuxacademy.com>

RUN apt-get update && apt-get upgrade -y && apt-get install apache2 telnet elinks -y
ENV MYVALUE my-value
EXPOSE 80
EXPOSE 22
CMD ["/usr/sbin/apache2ctl","-D","FOREGROUND"]
```

**docker built -t latest123/myapache .** builds the above container. The to put as many commands in a **RUN** section as possible to reduce the layers.

**docker port <containername> $CONTAINERPORT** shows us the port binding for containers.

**docker run -d -p 8080:80 --name=<container> <base>** binds the specific ports to localhost.