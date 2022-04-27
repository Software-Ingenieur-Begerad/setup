# Setup Pgamin

* get the latest version of installed packages and refresh the repo cache
```
sudo apt update
```

* make sure the CLI tool curl is installed
```
sudo apt install curl --no-install-recommends
```

* validate that postgres server is running
```
systemctl status postgresql
```

* add the official pgAdmin repository to the system
```
echo "deb https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" | sudo tee /etc/apt/sources.list.d/pgadmin4.list
```

* import GPG key from the pgAdmin respsitory
```
curl https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo apt-key add
```

* update apt repository cache and install pgAdmin
```
sudo apt update
sudo apt install pgadmin4-web --no-install-recommends
```

* configure pgAdmin
```
sudo /usr/pgadmin4/bin/setup-web.sh
```

* update firewall if necessary
```
sudo ufw status
sudo ufw allow 80
sudo ufw reload
sudo ufw enable
sudo ufw status
```

* access the PgAdmin web interace by opening a web browser and typing the URL ```https://your-server-ip/pgadmin4``` to reach the web interface

# Links

* [How to install pgAdmin on Debian 11](https://codepre.com/en/como-instalar-pgadmin-en-debian-11.html)
* [How To Install pgAdmin 4 on Debian 11|10|9](https://computingforgeeks.com/how-to-install-pgadmin4-on-debian/)
