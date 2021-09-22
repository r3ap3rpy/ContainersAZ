### Docker on Ubuntu

First update the system.

``` bash
sudo apt-get update -y
sudo apt-get upgrade -y
```

Then install the dependenices.

``` bash
sudo apt-get install apt-transport-https ca-certificates curl gnupg lsb-release -y
```

Now you can add the GPG key.

``` bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

Set up the repository.

``` bash
 echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

Finally install the docker engine itself.

``` bash
sudo apt-get update -y
sudo apt-get install docker-ce docker-ce-cli containerd.io -y
```

Now all that is left to enable and start the docker service.

``` bash
sudo systemctl enable docker 
sudo systemctl start docker
```

Add the user to the appropriate group then re-login.

``` bash
sudo usermod -a -G docker <username>
```

Issue the **docker ps** to verify functionality.
