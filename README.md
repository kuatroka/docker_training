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
docker run -t -d -p 80:80 --name nccoffee thenetworkchuck/nccoffee:frenchpress
docker run <image_name> sleep 10 # run the image and sleep for 10 seconds
docker run <image_name>:<tag> # tag is where the version of the image or app is specified
docker attach <container_name> # attach to the container, but it doesn't mean the CLI is attached too

'''

# to see usage stats for running containers

'''
docker stats # info about running containers
docker ps # lists running containers
docker ps -a # lists all containers, including stopped ones
docker stop <container_id or name> # stops a container
docker rm <container_id or name> # removes a container permanently

'''

# delete or list image or container

'''
docker image rm -f cantcontainmyself
docker container rm CONTAINER
docker rmi <image_name> # removes an image permanently
'''

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
