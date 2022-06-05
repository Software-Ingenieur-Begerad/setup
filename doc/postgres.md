# Setup Postgres

* install Postgres like [this](./postgres-install.md)

* create copy of config file ```pg_hba.conf file```\
NOTE: Insert the postgresql version <psql version> that is running on the respective host
```
cd /etc/postgresql/<psql version>/main/
sudo cp pg_hba.conf pg_hba.conf-backup
```

* switch authentication method from ```peer``` to ```md5``` for all local users connecting by Unix domain sockets by opening the following config file and adding the example configuration
```
sudo vi pg_hba.conf
```

```
# "local" is for Unix domain socket connections only
#local   all             all                                     peer
local   all             all                                     md5
```

* restart PostgreSQL to enable the changes
```
systemctl status postgresql
sudo systemctl restart postgresql
systemctl status postgresql
```

* when needed, create a database like [this](./postgres-create-db.md)

* when needed, create a user like [this](./postgres-create-user.md)

TODO: move the following description to dedicated setup files

# Allow Remote Connections

* configure ports and update firewall using the [firewall setup](firewall.md)
```
sudo ufw allow 5432
sudo ufw enable
sudo ufw status numbered
```

* create config backup
```
sudo cp /etc/postgresql/<version>/main/postgresql.conf /etc/postgresql/<version>/main/postgresql.conf-backup
```

* open config file to define what IP addresses postgres to listen on
```
sudo vi /etc/postgresql/<version>/main/postgresql.conf
```

* edit config file like this
```
#listen_addresses = 'localhost'
listen_addresses = '*'
```

* open config file to define access to all databases for all users with an encrypted key
```
sudo vi /etc/postgresql/<version>/main/pg_hba.conf
```

* edit config file like this
```
# TYPE  DATABASE	USER	ADDRESS   	METHOD
host    all     	all     0.0.0.0/0       md5
host    all             all     :/0             md5
```

* restart PostgreSQL to enable the changes
```
sudo systemctl restart postgresql
systemctl status postgresql
```

# Disable Start Up At System Boot

* If you install the PostgreSQL database from packages, it is automatically added to the start up scripts of the operating system. If you are only learning to work with the database, it is unnecessary to start the database each time you boot the system. Remove system startup link for the PostgreSQL database
```
sudo update-rc.d -f postgresql remove
```

# Links

* [PostgreSQL Java](https://zetcode.com/java/postgresql/)
