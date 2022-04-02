### A teaser demo for a complex setup.

Let's create our folders.

``` bash
sudo su -
mkdir -p /opt/wordpress/database
mkdir -p /opt/wordpress/html
``` 

Fire up our containers.

``` bash
docker run -e MYSQL_ROOT_PASSWORD=PASSWORD1 -e MYSQL_USER=wpuser -e MYSQL_PASSWORD=PASSWORD2 -e MYSQL_DATABASE=wordpress_db -v /opt/wordpress/database:/var/lib/mysql --name wordpressdb -d mariadb
docker run -e WORDPRESS_DB_USER=wpuser -e WORDPRESS_DB_PASSWORD=PASSWORD2 -e WORDPRESS_DB_NAME=wordpress_db -p 80:80 -v /opt/wordpress/html:/var/www/html --link wordpressdb:mysql --name wpcontainer -d wordpress
```