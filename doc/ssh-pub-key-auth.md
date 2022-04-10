# Public Key Authentication

## General

* login on the server using password\
NOTE: Leave this terminal/shell always open until this configuration is successfully validated. This is a backup connection to your server using password in case the public key authentication fails.
```
ssh -p<tbd> <user>@<host name>
```

* open the **sshd_config** file using a text editor like this
```
sudo vi /etc/ssh/sshd_config
```

* in this file, make sure the following options are set as follows
```
PasswordAuthentication yes
PermitRootLogin no
PubkeyAuthentication yes
#GSSAPIAuthentication yes
#GSSAPICleanupCredentials no
UsePAM yes
```

* save this file and restart sshd service
```
sudo systemctl restart sshd
```

* navigate to your local host home folder and check permissions
```
cd ~
ls -ld
chmod 0700 ~
ls -ld
```

* navigate to the **.ssh** folder and check permissions
```
cd ~/.ssh
ls -ld
chmod 0700 ~/.ssh
ls -ld authorized_keys
chmod 0600 ~/.ssh/authorized_keys
```

* copy your existing local host public key on the server
```
ssh-copy-id -p<tbd> <user>@<host name>
```

* login on the server using public key authentication
```
ssh -p<tbd> <user>@<host name>
```

* if you completed public key authentication successfully,
you may savely close the terminal/shell running the open password-based login

* revert the password changes in ```ssh_config``` if you are srcurity conscious\
```
sudo vi /etc/ssh/sshd_config
PasswordAuthentication no
```

## Links

[How to Fix SSH Failed Permission Denied (publickey)](https://phoenixnap.com/kb/ssh-permission-denied-publickey)

[How to Set Up SSH Keys on Debian 11](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys-on-debian-11)
