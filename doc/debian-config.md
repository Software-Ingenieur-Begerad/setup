# Configure Debian

* install sudo
```
su -
apt install sudo --no-install-recommends
exit
```

* add user <tbd> to sudoers using
```
whereis usermod
su -
usermod -a -G sudo <tbd>
exit
exit
```

* logout and login user <tbd> and validate participation of the sudo group
```
sudo -l
```

* update Debian
```
sudo apt update
sudo apt upgrade
```

* speed up boot time: In case you have only Debian installed on your system then you can speed up boot time by changing the grub timeout value ```GRUB_TIMEOUT``` to 0 in grub file.
```
sudo vi /etc/default/grub
```
