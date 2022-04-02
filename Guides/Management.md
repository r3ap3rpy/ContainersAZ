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

#### Modifying containers and saving changes.

Perform  the specific steps.

``` bash
docker run -it --name=container1 centos
touch /root/whatever
yum install nmap -y
exit
```

After that you can save these changes into another container by.

``` bash 
docker commit -m "Modified the container, nmap installed etc..." -a "daniel Szabo" <containerID> r3ap3rpy/<newimagename>:<tag>
``` 

##### Tag and push

List docker images with **docker image ls**.

Use the **docker image tag <existing name> <userid>/<tag>:<version>** for example **docker image tag my_centos r3ap3rpy/my_centos:latest**.

You can push an image by.

``` bash
docker login
docker image push <imagename>/<etc>:<version>
```

The images are located under the  **/var/lib/docker/overlay2**.

##### Docker volume

Create a new volume with **docker volume create mysite**.

You can list volumes **docker volume inspect mysite**, you can also remove or prune volumes. Prune removes unused ones.

Passing a volume to a container **docker container run -d --name mywebapp -p 80:80 -v mysite:/usr/share/nginx/html** for example.

Let's copy a file **cp /etc/passwd /var/lib/docker/volumes/mysite/_data/index.html**.