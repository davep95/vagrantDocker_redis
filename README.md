# vagrantDocker_redis
First pass at a short example on using Vagrant with Docker to create a Redis container with multiple images

# Vagrant Box used
add the ubuntu/trusty64 box

$ vagrant box add ubuntu/trusty64

# issues
1. during step when telling docker run make; a dependancy for gcc is unavailable. 
2. i tried to apt-get install build-essential but still failed run gcc
  
make[3]: gcc: Command not found
  
/bin/sh: 1: cc: not found

