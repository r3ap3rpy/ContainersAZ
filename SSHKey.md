### Welcome

In this short guide you will learn how you can generate ssh keys for passwordless authentication.

Open up a console and generate the keys.

``` bash
ssh-keygen -t rsa -b 2048 -C 'My key generated on <date>'
```

Then you can copy the public key to a remote machine.

``` bash
ssh-copy-id <username>@<ipofserver>
```

After entering the password you can see the results.

On your local machine you can exit your **./.ssh/config** file with the following content.

``` bash
Host *
    User <username>
	IdentityFile ~/.ssh/id_rsa 
```