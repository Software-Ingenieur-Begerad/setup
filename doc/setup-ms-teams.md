# Setup MS Teams

* install curl using
```
sudo apt install curl --no-install-recommends
```

* import the GPG key using
```
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
```

* import the official MS Teams repository using
```
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/ms-teams stable main" > /etc/apt/sources.list.d/teams.list'
```

* update your APT cache using
```
sudo apt update
```

* install MS Teams using
```
sudo apt install teams --no-install-recommends
```

* verify the installation by checking the APT-CACHE Policy using
```
sudo apt-cache policy teams
```

* launch teams
```
teams
```
