# Create Docker Image of Raspberry Pi OS (.img file) on Ubuntu 20.04

1. Download the Raspberry Pi OS file on https://www.raspberrypi.com/software/operating-systems/.

2. Unzip and mount the OS. You can use the following command to mount it on Ubuntu 20.04:

```
$ udisksctl loop-setup --file file_example.img
```

3. The previous command will create loop devices for the partitions in the image and mount them. Check the mount point of the root partition, go to this directory and compress the root partition using the following commands:

```
$ lsblk -p
$ cd /dir_example/rootfs
$ sudo tar cvf /output_dir/compressed.tar *
```

4. Docker import the tar file that was created. Docker untars it in the container relative to the / (root).

```
$ docker import compressed.tar account/repository:tag
```
5. Umount the mounted partitions. 

```
$ sudo umount /dir_example/rootfs
$ sudo umount /dir_example/boot
```
