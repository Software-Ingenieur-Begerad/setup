# Connect to Postgres Database Using Psql

* configure Postgres like [this](./postgres.md)

* create a database like [this](./postgres-create-db.md)

* create a use like [this](./postgres-create-user.md)

* when needed connect to Postgres as admin user locally
```
sudo -u postgres psql postgres -W
```

* when needed connect to the database <database name>
as user <user name> locally
```
psql -U <user name> -d <database name> -W

```

* when needed connect to the database <database name>
as user <user name> to a remote Postgres instance at host
<host name> and port <port number>\
NOTE: Configure Postgres for remote connections like
[this](./postgres.md)
```
psql -h <host name> -p <port number> -U <user name> -d <database name> -W
```