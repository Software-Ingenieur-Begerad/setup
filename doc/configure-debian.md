# Configure Debian

* add user <tbd> to sudoers using
```
sudo usermod -a -G sudo <tbd>
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
