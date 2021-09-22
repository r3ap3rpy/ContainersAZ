### Docker on CentOS

Install **yum-utils** and add the official **docker-ce** repo.

``` bash
sudo yum install -y yum-utils
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
```

Install docker itself.

``` bash
sudo yum install docker-ce docker-ce-cli containerd.io -y 
```

We need  to enable and run the service.

``` bash
sudo systemctl enable docker
sudo systemctl start docker
```

Add our user to the **docker** group.

``` bash
sudo usermod -a -G docker <username>
```

Log off and log in then issue the **docker ps** command to verify the functionality.