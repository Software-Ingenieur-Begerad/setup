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

* set key for admin user postgres
```
sudo -u postgres psql
postgres=# \password postgres
```
