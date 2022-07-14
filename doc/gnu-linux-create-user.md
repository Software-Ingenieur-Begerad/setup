# Create User

* create user <usr> with default home folder\
```
sudo useradd -m <usr>
```
* create password\
```
sudo passwd username
```
* add user <usr> to sudo group\
```
sudo usermod -a -G sudo <usr>
