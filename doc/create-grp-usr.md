# Create Group And User

* make shure group or user to be created does not exist yet
```
id <group or user name>
```

* create system group
```
sudo groupadd -r <group name>
```

* create system user with specific login shell and group
```
sudo useradd -r -s /bin/false -g <group name> <user name>
```

* print real and group and user id
```
id <group or user name>
```

* extract group and user details from OS configuration for verification
```
cat /etc/group|grep <group name>
cat /etc/passwd|grep <group name>
```
