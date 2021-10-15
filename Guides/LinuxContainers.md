### Linux containers

LXC, acronym for Linux Containers, is a lightweight Linux kernel based virtualization solution, which practically runs on top of the Operating System, allowing you to run multiple isolated distributions the same time.

The difference between LXC and KVM virtualization is that LXC doesn’t emulates hardware, but shares the same kernel namespace, similar to chroot applications.

In order to install **LXC** follow these steps.

``` bash
yum install epel-release -y
yum install debootstrap perl libvirt -y
yum install lxc lxc-templates -y
```

Once all is installed, lets verify the service.

``` bash
systemctl enable lxc.service
systemctl start lxc.service
systemctl enable libvirtd
systemctl start libvirtd 
```

You can list the templates with this command **ls -alh /usr/share/lxc/templates/**

In order to create a new container run the following **lxc-create -n test -t centos**

Let's start the container **lxc-start -n test -d**

The **root** will have a temporary password under **/var/lib/lxc/test/tmp_root_pass** which has to be changed as it will expire.

To get the status issue the **lxc-info test**.

Let's install container module for python.

``` bash
yum install python-devel python-pip lxc-devel -y
python -m pip install lxc-python2
```