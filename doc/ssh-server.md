# Enable SSH Server

## General

* install ssh server
```
sudo -l
sudo apt-get update
sudo apt-get install openssh-server --no-install-recommends
systemctl status sshd
systemctl list-unit-files | grep enabled | grep ssh
```

* set default port to ```<sshd port number>```, disable PermitRootLogin using
```
sudo vi /etc/ssh/sshd_config
sudo systemctl restart sshd
````
* check port configuration
```
ss -tupln|grep <sshd port number>

## Public Key Authentication

Follow [this](./ssh-pub-key-auth.md) guide to configure public key authentication.
