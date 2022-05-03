# Setup PM2

* update Apt repository cache
```
sudo apt update
```

* globally install the latest stable version of PM2 via npm
```
npm i -g pm2 
```

* create group and user ```pm2```
following this [setup](grp-usr.md)

* generate the startup script\
  **NOTE:** This instruction comes back with a reply like ```To setup the Startup Script, copy/paste the following command: sudo env PATH=$PATH:/usr/bin pm2 startup systemd -u <pm2 system service> --hp <pm2 installation home path>```
```
pm2 startup systemd -u pm2
```

* confirm that the PM2 startup service is up and running under systemd, run the following command
```
systemctl status pm2-<pm2 system user>.service
```

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
