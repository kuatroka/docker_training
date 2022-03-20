# docker_training

# pull the latest/default image of centos from docker hub

'''
docker pull centos
'''

# run the container (

# "--name" is the name I give to the container

# "centos" is the name of image I want to use

# could also use -p to specify the port like 80:80 - first is host, second is container

'''
docker run -d -t --name cantcontainmyself centos
'''

# -d: run in the background

# -t: allocate a pseudo-TTY

# -it: allocate a pseudo-TTY for interactive use

# run the container in interactive mode and attach to it and run a command "bash"

'''
docker exec -it cantcontainmyself bash
'''

# -it means interactive mode

# pull an image from docker hub with a tag - add : after the image name

# to run it while specifiying the port and the tag

# and you can open a web browser as localhost with the indicated port and see the app

'''
docker pull <image_name> # pulls the image withour running it
docker run -t -d -p 80:80 --name nccoffee thenetworkchuck/nccoffee:frenchpress # first port is host, second is container
docker run <image_name> sleep 10 # run the image and sleep for 10 seconds
docker run <image_name>:<tag> # tag is where the version of the image or app is specified
docker attach <container_name> # attach to the container, but it doesn't mean the CLI is attached too

'''

# to see usage stats for running containers

'''
docker stats # info about running containers
docker inspect <container_name> # in-depth info about the container

docker ps # lists running containers
docker ps -a # lists all containers, including stopped ones
docker stop <container_id or name> # stops a container
docker rm <container_id or name> # removes a container permanently
docker rm -f $(docker ps -a -q) # removes all containers, running or not

'''

# delete or list image or container

'''

docker rm <container_name> # removes a container permanently
docker rmi <image_name> # removes an image permanently
docker rmi -f <image_name> # forcefully removes an image permanently
docker rmi -f $(docker images -a -q) # removes all images
docker history <image_name> # shows the history of steps to create the image was created with
'''

# map local volume to container's volume

'''
docker run -v C:/Users/yo_fanpc/Documents/dev/docker_training/test_data_folder:/var/lib/mysql  
-p 3306:3306 -e MYSQL_ROOT_PASSWORD=qwerty -d mysql
'''

# "-v C:/Users/yo_fanpc/Documents/dev/docker_training/test_data_folder:/var/lib/mysql" maps volumes.

# 1st is local host and after the colon is the container's path

# linux commands in docker

'''
echo hello # write hello to the terminal
whoami # show the user name
echo $0 # show the name of the shell script being used
history # show the history of commands
ls !1 # run the command in the history at index 1
ls 1 # display the contents of the directory line by line
apt install nano # apt is a the main package manager in linux
apt update # update the default package list with a lot more packages
cat filename.txt # read the contents of a file
nano filename.txt # create or edit the contents of a file
mkdir directory # create a directory
touch filename.txt # create a file
more filename.txt # read the contents of a file in more mode
less filename.txt # read the contents of a file in less mode
tail filename.txt # read the contents of a file in tail mode. Can add -n 3 to see the last 3 lines
head filename.txt # read the contents of a file in head mode. Can add -n 3 to see the first 3 lines
'''

# CMD and ENTRYPOINT

'''
CMD ["command", "arguments"] # run the command with the arguments (CMD ["sleep", "10"])
CMD ["command"] # run the command with no arguments (CMD ["bash"])
ENTRYPOINT ["command", "arguments"] # run the command with the arguments (ENTRYPOINT ["sleep", "10"])
'''

### we can use both if we want to have a defalut argument and change it when running the container

'''
ENTRYPOINT ["sleep"]
CMD ["10"]
'''

# Docker Networking

'''
docker network ls # list all the networks
'''

# Volumes

'''
docker volume create <volume_name> # create a volume inside docker internal installation files
docker run -v <volume_name>:/var/lib/mysql mysql # maps previously created volume to the container
'''

# even if the volume creation command was not ran, the volume will be created automatically when docker run # command with volume mapping is invoked. This is volume mounting

# We can also mound or bind any other folder to the container - volume binding

# the more recent syntaxis is to use --mount

'''
docker run \
--mount type=bind, source=/data/mysql,target=var/lib/mysql
'''

##### docker-compose

'''
docker-compose up # start all the containers
docker-compose -f <docker-compose-file.yml> up # start specified yml file, not the default one
docker-compose down # stop all the containers

# tiny dockerised app

# 1 create a directory "hello-docker" and in it a file called "app.py" with one line

'''console.log("Hello Docker");'''

# 2 create a file called Dockerfile with the following contents:

'''
FROM node:alpine
COPY . /app
WORKDIR /app
CMD node app.js
'''

# 3 run a command in CLI "docker build -t hello-docker ."
