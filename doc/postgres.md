# Setup Postgres

* get the latest version of installed packages and refresh the repo cache
```
sudo apt update
```

* install postgres directly from the official repository
```
sudo apt-get install postgresql --no-install-recommends
```

* validate the existence of the postgres admin user
```
cat /etc/passwd|grep postgres
cat /etc/group|grep postgres
```

* set key for user postgres
```
sudo -u postgres psql postgres
postgres=# \password postgres
```

* create a new database user
```
su - postgres
psql
create user new_<user name> with encrypted password <key>;
grant all privileges on database <database name> to <user name>;
```

* create a new database with createdb command, which is going to be owned by user <user name>
```
sudo -u postgres createdb <database name> -O <user name>
```

* edit the pg_hba.conf file\
NOTE: Insert the postgresql database version that is running on the respective host
```
sudo cp /etc/postgresql/<psql version>/main/pg_hba.conf /etc/postgresql/<psgl version>/main/pg_hba.conf-backup
sudo vi /etc/postgresql/<psql version>/main/pg_hba.conf
```

* in order to be able to run a Spring Boot application with a local PostgreSQL installation, change the authentication method for the Unix domain socket and local connections to trust like this
```
# "local" is for Unix domain socket connections only
local   all             all                                     trust
# IPv4 local connections:
host    all             all             127.0.0.1/32            trust
```

* restart PostgreSQL to enable the changes
```
sudo systemctl restart postgresql
systemctl status postgresql
```

* use the psql tool to connect to the database
```
psql -U <user name> -d <database name> -W
```

* configure ports and update firewall using the [firewall setup](firewall.md)
```
sudo ufw allow 5432
sudo ufw enable
sudo ufw status numbered
```

# Allow Remote Connections

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
