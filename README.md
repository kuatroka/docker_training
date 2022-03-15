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
docker run -t -d -p 80:80 --name nccoffee thenetworkchuck/nccoffee:frenchpress
'''

# to see usage stats for running containers

'''
docker stats
'''

# delete image

'''
docker rm -f cantcontainmyself
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
