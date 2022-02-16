# Enable SSH Server

* install ssh server
```
sudo -l
sudo apt-get update
sudo apt-get install openssh-server --no-install-recommends
systemctl status sshd
ss -tupln
systemctl list-unit-files | grep enabled | grep ssh
```

* set default port to ```<tbd>```, disable PermitRootLogin using
```
sudo vi /etc/ssh/sshd_config
sudo systemctl restart sshd
````

* set up public key authentication by copying existing key
```
ssh-copy-id -p<tbd> <user>@<host name>
```
