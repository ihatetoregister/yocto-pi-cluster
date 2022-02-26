# yocto-pi-cluster
Yocto build for Raspberry Pi with ClusterHAT. 

Read more about ClusterHAT [here](https://clusterhat.com/).

# Guide
Use [this](https://jumpnowtek.com/rpi/Raspberry-Pi-Systems-with-Yocto.html) as a base. Tested with poky dunfell branch. 

Fetch this project and use as build directory, use `--recursive` flag to fetch dependencies. 

    git clone --recursive https://github.com/ihatetoregister/yocto-pi-cluster

## Customizaion
Perform any customization by modifying the [build/conf/local.conf](/build/conf/local.conf). 

## Build

    $ cd
    $ source poky-dunfell/oe-init-build-env ~/yocto-pi-cluster/build
    $ bitbake console-image

# Github actions
Tried created automated build using Github Actions but this does not seem feasable due to limits for diskspace and runtime. The yocto build requires about 50 GB and takes a few hours to complete. 

# Todo

## Boot and configuration
The script /usr/sbin/reconfig-clusterctrl should be run at boot. Need to find a way to append this to cmdline.txt. 

    quiet init=/usr/sbin/reconfig-clusterctrl cnat

Also the /boot partition need to be mountable for this script to work. Modified /etc/fstab manually to get this to work. 

    /dev/mmcblk0p1      /boot           auto        defaults,sync,noauto    0   0
