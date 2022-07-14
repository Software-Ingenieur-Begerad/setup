# Create User

* create user <usr> with default home folder\
```
sudo useradd -m <usr>
```
* create password\
```
sudo passwd <usr>
```
* add user <usr> to sudo group\
```
su -
usermod -a -G sudo <usr>
```
