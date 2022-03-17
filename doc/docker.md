# Setup Docker

## General

* update your APT cache using
```
sudo apt update
```

* uninstall old versions
```
sudo apt-get remove docker docker-engine docker.io containerd runc
```

* install basic package dependencies
```
sudo apt install apt-transport-https ca-certificates curl gnupg lsb-release --no-install-recommends
```

* add Docker's official GPG key
```
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

* set up the stable repository
```
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

* update the package index and install the latest version
```
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

* check whether the service is enabled
```
systemctl is-enabled docker
systemctl is-enabled containerd
```

* check Docker and Containerd service status
```
systemctl status docker containerd
```

* verify Docker version
```
docker -v
```

* add the user <user> to the group ‘docker‘
```
sudo usermod -aG docker <user>
```

* log in as user <user> using the command below and verify the configuration
```
su - <user>
```

* run the following docker command to verify your installation
```
docker run hello-world
```

## Links

[How to Install Docker on Debian 11](https://www.techlear.com/blog/2021/10/01/how-to-install-docker-on-debian-11/)

[How to Install Docker on Debian 11](https://www.rosehosting.com/blog/how-to-install-docker-on-debian-11/)
