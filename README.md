# docker-apache-php-composer
Basic boilepate to start working with apache and PHP in docker

# Build image 
replace "myapp" with any name you like
don't foget the " ." at the end ;-)
```
$docker build -t myapp .
```
# Run the container to see that is working ok
```
$docker run -p 8080:80 -d myapp
```
then run 
```
$docker ps
```
to check the ip that is assigned to your container (eg 0.0.0.0:8080->80/tcp)
then go to your browser and type: 
```
0.0.0.0:8080
```
and you will see a welcome message and the phpinfo() you have installed

# Stop the container:
```
$docker stop docker stop $(docker ps -a -q)
```
This will stop all the containers. 
If you have more that you want to keep them alive then run:
```
docker ps
```
check the id of the container and run 
```
$docker stop "id of the container"
```
# Now start developing you app:

Run container with a mounted folder to work live.
Replace "/home/user/www/" with any local folder you like to mount to the container.
The folder you mount must have a "/public" subfolder where you place your public files (eg. index.php)
```
$docker run -v /home/user/www:/var/www/site -p 8080:80 -d myapp
```
Now everything you write in "/home/user/www" is reflected to the server.
For example create a file "index.php" in  "/home/user/www/public/" and write in it:
```php
<? echo "Hello Docker World"; ?>
```
go to the browser and hit refresh.

# Credits
Based on what i've learned from this:
- [nimmis/apache-php5](https://hub.docker.com/r/nimmis/apache-php5/~/dockerfile/)
- [webdevops/php-boilerplate](https://hub.docker.com/r/webdevops/php-boilerplate/~/dockerfile/)
- [Dan Pupius@Medium:Apache and PHP on Docker](https://medium.com/dev-tricks/apache-and-php-on-docker-44faef716150#.5bz3h5mgy)
- [Yunes Rafie@sitepoint:Docker and Dockerfiles Made Easy!](http://www.sitepoint.com/docker-and-dockerfiles-made-easy/)
