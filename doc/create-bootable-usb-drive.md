# Prepare USB Drive For Installation

* download debian

* identify USB drive using
```
df -h
```

* unmount drive using
```
sudo umount /dev/<tbd>
```

* format drive using
```
sudo mkfs.vfat /dev/<tbd>
```

* [create bootable USB drive](https://www.pragmaticlinux.com/2021/03/create-a-bootable-usb-drive-from-a-linux-iso-image/)
