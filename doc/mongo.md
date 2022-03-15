# Setup MongoDB

* install wget to import the GPG key of MongoDB
```
sudo apt install wget --no-install-recommends
```

* import the GPG key of MongoDB from its official website
```
wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add -
```

* enable the MongoDB repository
```
echo "deb http://repo.mongodb.org/apt/debian buster/mongodb-org/5.0 main" | sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list
```

* update apt repository cache
```
sudo apt update
```

* install MongoDB
```
sudo apt install mongodb-org --no-install-recommends
```

* start MongoDB using systemd
```
sudo systemctl start mongod
```

* enable MongoDB using systemd
```
sudo systemctl enable mongod
```

* verify MongoDB using systemd
```
sudo systemctl status mongod
```

* check the installed version of MongoDB
```
mongod --version
```
