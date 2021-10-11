### Running Containers

Usually the **docker run imagename** is used.

The **helloworld** and **whalesay** are demo containers to be used for demonstration.

The **docker ps** is used to inspect run history about containers on a specific system, the **-a** switch shows all.

The **docker0** is the default network interface for the containers.

The **docker run -it centos:latest /bin/bash** with run the container and attach to the tty with the given shell.

The **docker run -d centos:latest /bin/bash** runs the container in detached mode, the **--name=** switch allows you to name your containers.