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

## Links

[How to Install Apache Tomcat on Debian 11](https://www.linuxtechi.com/how-to-install-apache-tomcat-on-debian/)
[How to Install Apache Tomcat on Debian 11](https://www.itzgeek.com/how-tos/linux/debian/how-to-install-apache-tomcat-on-debian-11.html)
