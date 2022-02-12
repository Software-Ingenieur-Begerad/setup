# Setup PM2

* update Apt repository cache
```
sudo apt update
```

* globally install the latest stable version of PM2 via npm
```
sudo npm i -g pm2 
```

* create group and user ```pm2``` following this [setup](create-grp-usr.md)
# Helpful PM2 instructions

* list all node application (process/microservices)
```
pm2 list
```

* monitor logs, custom metrics, process information from all processes
```
pm2 monit
```

* view details of a single Node.js process using the process ID or name
```
pm2 show <process ID or name
```

* update PM2 package
```
pm2 update
```
