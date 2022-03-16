# Setup Redis

* update apt repository cache
```
sudo apt update
```

* install redis
```
sudo apt install redis-server --no-install-recommends
```

* check if service is running
```
systemctl status redis-server
```

* verify used port
```
ss -tlpn
```

* create backup of default configuration
```
sudo cp /etc/redis/redis.conf /etc/redis/redis.conf.bak
```

* open config file
```
sudo vi /etc/redis/redis.conf
```

* increase the memory of the server by adding these two lines in the end of the configuration file
```
maxmemory 500mb 
maxmemory-policy allkeys-lru
```

* apply config changes
```
sudo systemctl restart redis-server
```

* test service sending ```ping``` using the client
```
redis-cli
```

# Other

* start service
```
sudo systemctl start redis-server
```

* enable service to start with the system
```
sudo systemctl enable redis-server
```
