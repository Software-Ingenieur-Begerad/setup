# Enable SSH Server

## General

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

## Public Key Authentication

Follow [this](./ssh-pub-key-auth.md) guide to configure public key authentication.
