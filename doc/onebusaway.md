# Setup OneBusAway

## Setup

* get the latest version of installed packages and refresh the repo cache
```
sudo apt update
```

* setup JDK version 8 (requirement of OneBusAway)\
NOTE: Refer to [Java setup](java.md)
```
sudo mkdir -p /usr/lib/jvm/open-jdk-8 --
sudo tar -xvzf ./OpenJDK8U-jdk_x64_linux_hotspot_8u322b06.tar.gz -C /usr/lib/jvm/open-jdk-8/ --strip-components=1
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/open-jdk-8/bin/java 1
sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/open-jdk-8/bin/javac 1
sudo update-alternatives --install /usr/bin/jar jar /usr/lib/jvm/open-jdk-8/bin/jar 1
sudo update-alternatives --install /usr/bin/jshell jshell /usr/lib/jvm/open-jdk-8/bin/jshell 1
```

* validate Java version
```
update-alternatives --list java
java -version
sudo update-alternatives --config java

* add user and group
```
sudo groupadd tomcat
sudo mkdir -p /opt/tomcat
sudo useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat
```

* download and extract Tomcat 8
```
wget https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.78/bin/apache-tomcat-8.5.78.tar.gz
sudo tar -xvf apache-tomcat-8.5.78.tar.gz -C /opt/tomcat --strip-components=1
sudo chown -R tomcat: /opt/tomcat
sudo sh -c 'chmod +x /opt/tomcat/bin/*.sh'
```

* create Systemd service file
```
sudo vi /etc/systemd/system/tomcat.service
systemctl daemon-reload
sudo systemctl start tomcat
sudo systemctl enable tomcat
systemctl status tomcat

* configure Tomcat 8
```
sudo cp /opt/tomcat/conf/tomcat-users.xml /opt/tomcat/conf/tomcat-users.xml.backup
sudo vi /opt/tomcat/conf/tomcat-users.xml
sudo cp /opt/tomcat/webapps/manager/META-INF/context.xml /opt/tomcat/webapps/manager/META-INF/context.xml.backup
sudo vi /opt/tomcat/webapps/manager/META-INF/context.xml
sudo cp /opt/tomcat/webapps/host-manager/META-INF/context.xml /opt/tomcat/webapps/host-manager/META-INF/context.xml.backup
sudo vi /opt/tomcat/webapps/host-manager/META-INF/context.xml
sudo systemctl restart tomcat
systemctl status tomcat
```

* adjust firewall
```
sudo ufw status
sudo ufw allow 8080
sudo ufw status
sudo ufw reload
sudo ufw enable
```

* validate
```
ss -tpln
```

* open Tomcat in Browser using the address ```http://localhost:8080```

* install MySQL
```
wget https://dev.mysql.com/get/mysql-apt-config_0.8.22-1_all.deb
sudo dpkg -i mysql-apt-config_0.8.22-1_all.deb
sudo apt update
sudo apt install mysql-server
sudo systemctl status mysql
mysql_secure_installation
mysql -u root -p
```

* define Tomcat memory using OBA Config and Deploy guide and [this](https://mkyong.com/tomcat/tomcat-javalangoutofmemoryerror-permgen-space/) guide
```
sudo find / -name "catalina.sh"
sudo vi /opt/tomcat/bin/catalina.sh
sudo -u tomcat vi /opt/tomcat/bin/setenv.sh
sudo sh -c 'chmod +x /opt/tomcat/bin/*.sh'
export JAVA_OPTS="-Dfile.encoding=UTF-8 -Xms128m -Xmx1024m -XX:PermSize=64m -XX:MaxPermSize=256m"
sudo systemctl restart tomcat
sudo systemctl status tomcat
```

* download the binaries
```
mkdir ~/oba
mkdir oba
cd oba
wget https://repo.camsys-apps.com/releases/org/onebusaway/onebusaway-transit-data-federation-builder/2.0.0/onebusaway-transit-data-federation-builder-2.0.0-withAllDependencies.jar
wget https://repo.camsys-apps.com/releases/org/onebusaway/onebusaway-transit-data-federation-webapp/2.0.0/onebusaway-transit-data-federation-webapp-2.0.0.war
wget https://repo.camsys-apps.com/releases/org/onebusaway/onebusaway-api-webapp/2.0.0/onebusaway-api-webapp-2.0.0.war
wget https://repo.camsys-apps.com/releases/org/onebusaway/onebusaway-enterprise-acta-webapp/2.0.0/onebusaway-enterprise-acta-webapp-2.0.0.war
```

* Download the Transit GTFS Data From the Transit Agency
```
mkdir -p oba/gtfs
cd oba/gtfs/
wget http://data.ndovloket.nl/flixbus/flixbus-eu.zip
```

* Build the Transit Data Bundle
```
cd oba/gtfs
java -version
java -jar -Xss4m -Xmx1g ~/oba/onebusaway-transit-data-federation-builder-<enter version>.jar ~/oba/gtfs/<enter file name>.zip ~/oba/gtfs
```

* Download the MySQL Connector Java Library
```
cd ~/oba
wget https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-java-8.0.28.tar.gz
tar -zxvf mysql-connector-java-8.0.28.tar.gz
mv mysql-connector-java-8.0.28/mysql-connector-java-8.0.28.jar .
rm -rf mysql-connector-java-8.0.28.tar.gz
rm -rf mysql-connector-java_8.0.28-1debian11_all.deb
rm -rf mysql-connector-java-8.0.28
```

* Create the MySQL Database
```
sudo -u root mysql -p -e "CREATE DATABASE oba; GRANT ALL PRIVILEGES ON oba.* TO 'oba'@'localhost' IDENTIFIED BY '<enter key for obu db user';"
```

* Stop the Tomcat 8 Service
```
sudo systemctl status tomcat
sudo systemctl stop tomcat
sudo systemctl status tomcat
```

* Deploy and Configure the OneBusAway Transit Data Federation Webapp
```
cd /var/lib
sudo mkdir -p /var/lib/tomcat8/webapps/onebusaway-transit-data-federation-webapp
cd /var/lib/tomcat8/webapps/onebusaway-transit-data-federation-webapp
sudo mv ~/oba/onebusaway-transit-data-federation-webapp-2.0.0.war /var/lib/tomcat8/webapps/onebusaway-transit-data-federation-webapp/
sudo jar xvf /var/lib/tomcat8/webapps/onebusaway-transit-data-federation-webapp/onebusaway-transit-data-federation-webapp-2.0.0.war
sudo rm -rf /var/lib/tomcat8/webapps/onebusaway-transit-data-federation-webapp/onebusaway-transit-data-federation-webapp-2.0.0.war
```

* Copy the MySQL Driver
```
cd /var/lib/tomcat8/webapps/onebusaway-transit-data-federation-webapp/WEB-INF/lib
sudo cp ~/oba/mysql-connector-java-8.0.28.jar .
```

* Configure the OneBusAway Transit Data Federation Webapp
  * change ```pasword``` value to ```<blub>```
  * change ```agencyId``` value to ```Flix```
  * change ```refreshInterval``` value to ```60```
  * change ```tripUpdatesUrl``` value to ```https://wimb-api-ops-gis.ew1p3.k8s.mfb.io/v1/gtfs-rt/flavour/rmv/region/de/agency/bus_train/trip-update```
  * change ```vehiclePositionsUrl``` value ```to https://wimb-api-ops-gis.ew1p3.k8s.mfb.io/v1/gtfs-rt/flavour/rmv/region/de/agency/bus_train/vehicle-position```
  * change ```alertsUrl``` value to ```https://wimb-api-ops-gis.ew1p3.k8s.mfb.io/v1/gtfs-rt/flavour/rmv/region/de/agency/bus_train/alerts```

```
sudo cp /var/lib/tomcat8/webapps/onebusaway-transit-data-federation-webapp/WEB-INF/classes/data-sources.xml /var/lib/tomcat8/webapps/onebusaway-transit-data-federation-webapp/WEB-INF/classes/data-sources.xml.backup
sudo vi /var/lib/tomcat8/webapps/onebusaway-transit-data-federation-webapp/WEB-INF/classes/data-sources.xml
```

* Deploy and Configure the OneBusAway API Webapp

* copy files

```
sudo mkdir /var/lib/tomcat8/webapps/onebusaway-api-webapp
ls -ltha /var/lib/tomcat8/webapps
cd /var/lib/tomcat8/webapps/onebusaway-api-webapp
sudo mv ~/oba/onebusaway-api-webapp-2.0.0.war /var/lib/tomcat8/webapps/onebusaway-api-webapp/
ls /var/lib/tomcat8/webapps/onebusaway-api-webapp/
sudo jar xvf /var/lib/tomcat8/webapps/onebusaway-api-webapp/onebusaway-api-webapp-2.0.0.war
ls
sudo rm -rf /var/lib/tomcat8/webapps/onebusaway-api-webapp/onebusaway-api-webapp-2.0.0.war
ls
```

* copy the MySQL Driver

```
cd /var/lib/tomcat8/webapps/onebusaway-api-webapp/WEB-INF/lib
sudo cp ~/oba/mysql-connector-java-8.0.28.jar .
```

* configure the OneBusAway API Webapp
  * insert last bean
  * change value of ```username``` to ```oba``` twice
  * change value of ```password``` to ```<blub>``` twice

```
cd /var/lib/tomcat8/webapps/onebusaway-api-webapp/WEB-INF/classes/
ls
sudo cp data-sources.xml data-sources.xml-backup
sudo vi data-sources.xml
```

* Deploy and Configure the OneBusAway Enterprise ACTA Webapp

* copy files

```
rm -rf /var/lib/tomcat8/webapps/ROOT/*
sudo mkdir ROOT
cd /var/lib/tomcat8/webapps/ROOT
sudo mv ~/oba/onebusaway-enterprise-acta-webapp-2.0.0.war /var/lib/tomcat8/webapps/ROOT/
ls
sudo jar xvf /var/lib/tomcat8/webapps/ROOT/onebusaway-enterprise-acta-webapp-2.0.0.war
sudo rm -rf /var/lib/tomcat8/webapps/ROOT/onebusaway-enterprise-acta-webapp-2.0.0.war
ls

* copy MySQL Driver

```
cd /var/lib/tomcat8/webapps/ROOT/WEB-INF/lib
sudo cp ~/oba/mysql-connector-java-8.0.28.jar .
ls
```

* configure the OneBusAway API Webapp
  * change value of ```username``` to ```oba```
  * change value of ```password``` to ```<blub>```

```
cd /var/lib/tomcat8/webapps/ROOT/WEB-INF/classes
ls
sudo cp data-sources.xml data-sources.xml-backup
```

* Start the Tomcat8 Service

* In a SSH terminal you may want to run the following command so that you can watch the console output of the Tomcat8 service as OneBusAway starts up for the first time:

```
tail -f /var/log/tomcat8/catalina.out
```

* start the Tomcat8 Service

```
sudo service tomcat8 start
```

* or

```
systemctl status tomcat.service
sudo systemctl restart tomcat.service
systemctl status tomcat.service
```

## Links

* [OneBusAway/onebusaway:Configuration and Deployment Guide for v2.x](https://github.com/OneBusAway/onebusaway/wiki/Configuration-and-Deployment-Guide-for-v2.x)
* [How to Install Apache Tomcat on Debian 11](https://www.linuxtechi.com/how-to-install-apache-tomcat-on-debian/)
* [How to Install Apache Tomcat on Debian 11](https://www.itzgeek.com/how-tos/linux/debian/how-to-install-apache-tomcat-on-debian-11.html)
* [How to install MySQL on Debian 11](https://codepre.com/en/como-instalar-mysql-en-debian-11.html)