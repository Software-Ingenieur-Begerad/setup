# Create User with Postgres

* configure Postgres like [this](./postgres.md)

* create a database like [this](./postgres-create-db.md)

* create a database user called <user name> with password <key>
```
sudo -u postgres psql -W
CREATE USER <user name> with encrypted password <key>;
grant all privileges on database <database name> to <user name>;
```

* edit the pg_hba.conf file\
NOTE: Insert the postgresql database version that is running on the respective host
```
sudo cp /etc/postgresql/<psql version>/main/pg_hba.conf /etc/postgresql/<psgl version>/main/pg_hba.conf-backup
sudo vi /etc/postgresql/<psql version>/main/pg_hba.conf
```

* in order to be able to run applications like e.g. Spring Boot with a local PostgreSQL installation, change the authentication method for the Unix domain socket and local connections to trust like this
```
# "local" is for Unix domain socket connections only
local   all             all                                     trust
# IPv4 local connections:
host    all             all             127.0.0.1/32            trust
```

* restart PostgreSQL to enable the changes
```
systemctl status postgresql
sudo systemctl restart postgresql
systemctl status postgresql
```
