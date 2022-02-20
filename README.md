# yocto-pi-cluster
Yocto build for Raspberry Pi with ClusterHAT

# Todo

## Boot and configuration
The script /usr/sbin/reconfig-clusterctrl should be run at boot. Need to find a way to append this to cmdline.txt. 
    quiet quiet init=/usr/sbin/reconfig-clusterctrl cnat

Also the /boot partition need to be bootable for this script to work. Modified /etc/fstab manually to get this to work.
    /dev/mmcblk0p1      /boot           auto        defaults,sync,noauto    0   0
