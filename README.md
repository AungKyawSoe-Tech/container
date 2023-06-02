# container 

Credits
---------
This work is inspired by following works and the major credit should be attributed to them:

(1) Building a container from scratch in Go - Liz Rice (Microscaling Systems)
https://www.youtube.com/watch?v=Utf-A4rODH8

(2) A container in less than 60 lines of Go 
https://gist.github.com/christophberger/58505418133d474486a88f958d8ea14b

(3) Build Your Own Container Using Less than 100 Lines of Go 
https://www.infoq.com/articles/build-a-container-golang/


Install Go and LxC
---------------------

sudo apt install golang-go

sudo apt-get install lxc
lxc-checkconfig

Create Linux Container
---------------------------
sudo lxc-create -t download -n ubuntu

Choose as follows:

Distribution: 
ubuntu
Release: 
bionic 
Architecture: 
amd64

Copying the created privileged container to create a root file system in /home/work/
-----------------------------------------------------------------------------------
cd /home/work/rootfs
sudo cp /var/cache/lxc/download/ubuntu/bionic/amd64/default/rootfs.tar.xz .
tar xvf rootfs.tar.xz

Running the container
----------------------
aung@aung-VirtualBox:/home/work$ sudo go run container.go run /bin/bash
running [/bin/bash] 
child running [/bin/bash] 
root@container:/# hostname
container
root@container:/# mount -t proc proc /proc
root@container:/# ps
    PID TTY          TIME CMD
      1 ?        00:00:00 exe
      5 ?        00:00:00 bash
     17 ?        00:00:00 ps
root@container:/# exit
exit
aung@aung-VirtualBox:/home/work$ hostname
aung-VirtualBox

root@container:/# uname -a
Linux container 5.15.0-73-generic #80~20.04.1-Ubuntu SMP Wed May 17 14:58:14 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux
root@container:/# exit
exit
aung@aung-VirtualBox:/home/work$ uname -a
Linux aung-VirtualBox 5.15.0-73-generic #80~20.04.1-Ubuntu SMP Wed May 17 14:58:14 UTC 2023 x86_64 x86_64 x86_64 GNU/Linux

root@container:/# ls
bin   dev  home  lib64  mnt  proc  rootfs.tar.xz  sbin  sys  usr
boot  etc  lib   media  opt  root  run            srv   tmp  var
root@container:/# which bash
/bin/bash
root@container:/# exit
exit
aung@aung-VirtualBox:/home/work$ which bash
/usr/bin/bash





