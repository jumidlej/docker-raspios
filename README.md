# Create Docker Image from Raspberry OS .img file on UBuntu 20.04

1. Download the Raspberry Pi OS file on https://www.raspberrypi.com/software/operating-systems/.

2. Unzip and mount the OS. You can use the command:

```
$ udisksctl loop-setup --file file.img
```

3. Go to the root directory and compress the root partition:

```
$ cd rootfs
$ sudo tar cvf compressed.tar *
```

4. Docker import the tar file that was created. Docker untars it in the container relative to the / (root).

```
$ docker import compressed.tar account/repository:tag
```