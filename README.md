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

# run the container in interactive mode and attach to it and run a command "bash"

'''
docker exec -it cantcontainmyself bash
'''

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
