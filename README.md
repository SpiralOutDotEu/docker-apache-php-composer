# docker-apache-php-composer
Basic boilepate to start working with apache and PHP in docker

#Build image 
# replace "myapp" with any name you like
# don't foget the " ." at the end ;-)
docker build -t myapp .

#run the container to see that is working ok
docker run -p 8080:80 -d myapp

#then run 
docker ps
#to check the ip that is assigned to your container
#(eg 0.0.0.0:8080->80/tcp)
#then go to your browser and type "0.0.0.0:8080"
#and you will see a welcome message and the phpinfo() you have installed

#stop the container:
docker stop docker stop $(docker ps -a -q)
# This will stop all the containers. 
# If you have more that you want to keep them alive then
# run: 
docker ps
# check the id of the container and run 
docker stop <id of the container>

#now start developing you app
#
# Run container with a mounted folder to work live.
# Replace "/home/user/www/" with any local folder you like to mount to the container.
# The folder you mount must have a "/public" subfolder where you place your public files (eg. index.php)
docker run -v /home/user/www:/var/www/site -p 8080:80 -d myapp
#Now everything you write in "/home/user/www" is reflected to the server.
# For example create a file "index.php" in  "/home/user/www/public/" and write in it:
<? echo "Hello Docker World" ?>
#go to the browser and hit refresh.

