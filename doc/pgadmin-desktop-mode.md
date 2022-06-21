# Setup pgAdmin in Desktop Mode

## Add pgAdmin repository to Debian 11/10/9

* The pgAdmin DEBs for Debian are available from the pgAdmin APT repository.\
Start the repository setup process by installing the public key for the repository\
```
sudo curl https://www.pgadmin.org/static/packages_pgadmin_org.pub | sudo apt-key add
```
* Then create the repository configuration file:\
```
sudo sh -c 'echo "deb https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/$(lsb_release -cs) pgadmin4 main" > /etc/apt/sources.list.d/pgadmin4.list'
```
* You can check the contents of the repository file created using the following command:\
```
$ cat /etc/apt/sources.list.d/pgadmin4.list
deb https://ftp.postgresql.org/pub/pgadmin/pgadmin4/apt/bullseye pgadmin4 main
```

## Install pgAdmin4 on Debian 11/10/9

* With the repository added you can now install pgAdmin 4 on Debian 11/10/9 Linux system:\
```
sudo apt update
```

* What are Server Mode and Desktop Mode?\ When deploying pgAdmin on a web server for multiple users, it is run in server mode (SERVER_MODE = True). This mode requires each user to have an account in pgAdmin, with their own password. Users are required to login to pgAdmin in order to use it. One or more users may be configured as an administrator and will be able to add or remove other users. For more information, please see the Server Deployment and User Management documentation. To allow running in desktop mode (SERVER_MODE = False), a runtime application is provided to host and display the pgAdmin code (sometimes referred to as the application server). In this mode, each user runs their own instance of pgAdmin, thus no authentication or user management is required. For more information, please see the Desktop Deployment documentation.

* If you wanted to install the desktop mode only, run the commands below:\
```
sudo apt install pgadmin4-desktop
```

* For web mode only use:\
```
sudo apt install pgadmin4-web
```

##: Configure Web Server for pgAdmin4

* For guys who installed web mode, you need to configure the webserver by running the command:\
```
sudo /usr/pgadmin4/bin/setup-web.sh
```
