# Setup Emacs

## To-do List

* I can not open the status page on http://acer:8080

## Setup

* get the latest version of installed packages and refresh the repo cache
```
sudo apt update
```

#mkdir -p/usr/lib/jvm/open-jdk-17 --strip-components=1
  193  mkdir -h
  194  mkdir --help
  195  mkdir -p/usr/lib/jvm/open-jdk-8
  196  mkdir -p /usr/lib/jvm/open-jdk-8
  197  sudo mkdir -p /usr/lib/jvm/open-jdk-8 --
  198  #sudo tar -xvzf ./OpenJDK8U-jdk_x64_linux_hotspot_8u322b06.tar.gz -C /usr/lib/jvm/open-jdk-8/ --strip-components=1
  199  cat /etc/debian_version 
  200  sudo tar -xvzf ./OpenJDK8U-jdk_x64_linux_hotspot_8u322b06.tar.gz -C /usr/lib/jvm/open-jdk-8/ --strip-components=1
  201  cd /usr/lib/jvm/open-jdk-8/
  202  ls
  203  update-alternatives --list java
  204  java -version
  205  sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/open-jdk-8/bin/java 1
  206  sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/open-jdk-8/bin/javac 1
  207  sudo update-alternatives --install /usr/bin/jar jar /usr/lib/jvm/open-jdk-8/bin/jar 1
  208  sudo update-alternatives --install /usr/bin/jshell jshell /usr/lib/jvm/open-jdk-8/bin/jshell 1
  209  sudo update-alternatives --config java
  210  java -version
  211  #https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.78/bin/apache-tomcat-8.5.78.zip
  212  cd
  213  ls
  214  wget https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.78/bin/apache-tomcat-8.5.78.zip
  215  java -version
  216  sudo groupadd tomcat
  217  sudo mkdir -p /opt/tomcat
  218  #sudo groupadd tomcat
  219  #sudo useradd -g tomcat -d /opt/tomcat -s /usr/sbin/nologin tomcat
  220  #
  221  #sudo useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat
  222  sudo useradd -s /bin/false -g tomcat -d /opt/tomcat tomcat
  223  sudo tar -xvf apache-tomcat-8.5.78.zip -C /opt/tomcat --strip-components=1
  224  wget https://dlcdn.apache.org/tomcat/tomcat-8/v8.5.78/bin/apache-tomcat-8.5.78.tar.gz
  225  sudo tar -xvf apache-tomcat-8.5.78.tar.gz -C /opt/tomcat --strip-components=1
  226  cd /opt/tomcat/
  227  ls
  228  sudo update-java-alternatives -l
  229  java -version
  230  sudo vi /etc/systemd/system/tomcat.service
  231  cd /usr/lib/jvm/open-jdk-8/
  232  pwd
  233  sudo vi /etc/systemd/system/tomcat.service
  234  sudo systemctl daemon-reload
  235  ss -tpln
  236  sudo chown -R tomcat: /opt/tomcat
  237  ls -ltha /opt/tomcat
  238  sudo sh -c 'chmod +x /opt/tomcat/bin/*.sh'
  239  ls -ltha /opt/tomcat/bin/
  240  sudo ls -ltha /opt/tomcat/bin/
  241  sudo vi /etc/systemd/system/tomcat.service
  242  sudo systemctl daemon-reload
  243  sudo update-java-alternatives -l
  244  java -v
  245  java -version
  246  echo $JAVA_HOME
  247  sudo systemctl start tomcat
  248  systemctl status tomcat.service
  249  less /etc/systemd/system/default.target.wants/e2scrub_reap.service 
  250  less /etc/systemd/system/sshd.service 
  251  less /etc/systemd/system/syslog.service 
  252  less /etc/systemd/system/tomcat.service 
  253  less /etc/systemd/system/syslog.service 
  254  less /etc/systemd/system/sshd.service 
  255  sudo update-java-alternatives -l
  256  whereis update-java-alternatives
  257  whereis update-alternatives
  258  sudo update-alternatives --list java
  259  sudo systemctl start tomcat
  260  journalctl -xe
  261  sudo cp /etc/systemd/system/tomcat.service /etc/systemd/system/tomcat.service.backup
  262  echo '' > /etc/systemd/system/tomcat.service
  263  sudo echo '' > /etc/systemd/system/tomcat.service
  264  sudo rm /etc/systemd/system/tomcat.service
  265  sudo vi /etc/systemd/system/tomcat.service
  266  pwd
  267  sudo vi /etc/systemd/system/tomcat.service
  268  sudo vi /etc/systemd/system/tomcat.service.backup 
  269  sudo cp /etc/systemd/system/tomcat.service /etc/systemd/system/tomcat.service.backup.next
  270  sudo cp /etc/systemd/system/tomcat.service.backup /etc/systemd/system/tomcat.service
  271  sudo systemctl daemon-reload
  272  sudo systemctl start tomcat
  273  sudo systemctl enable tomcat
  274  systemctl status tomcat
  275  sudo vi /opt/tomcat/conf/tomcat-users.xml
  276  sudo cp /opt/tomcat/conf/tomcat-users.xml /opt/tomcat/conf/tomcat-users.xml.backup
  277  sudo less /opt/tomcat/conf/tomcat-users.xml.backup
  278  sudo vi /opt/tomcat/conf/tomcat-users.xml
  279  sudo cp /opt/tomcat/webapps/manager/META-INF/context.xml /opt/tomcat/webapps/manager/META-INF/context.xml.backup
  280  sudo vi /opt/tomcat/webapps/manager/META-INF/context.xml
  281  sudo cp /opt/tomcat/webapps/host-manager/META-INF/context.xml /opt/tomcat/webapps/host-manager/META-INF/context.xml.backup
  282  sudo vi /opt/tomcat/webapps/host-manager/META-INF/context.xml
  283  sudo systemctl restart tomcat
  284  systemctl status tomcat
  285  sudo ufw status
  286  sudo ufw allow 8080
  287  sudo ufw status
  288  sudo ufw reload
  289  sudo ufw enable
  290  sudo vi /opt/tomcat/conf/tomcat-users.xml
  291  sudo netstat -antup | grep 8080
  292  ss -tpln
  293  ss -autpln
  294  sudo vi /opt/tomcat/conf/tomcat-users.xml
  295  sudo vi /opt/tomcat/webapps/manager/META-INF/context.xml
  296  sudo vi /opt/tomcat/webapps/host-manager/META-INF/context.xml
  297  sudo systemctl restart tomcat
  298  sudo vi /opt/tomcat/conf/tomcat-users.xml
  299  sudo systemctl restart tomcat
  300  sudo vi /opt/tomcat/conf/tomcat-users.xml

## Links

[How to Install Apache Tomcat on Debian 11](https://www.linuxtechi.com/how-to-install-apache-tomcat-on-debian/)
[How to Install Apache Tomcat on Debian 11](https://www.itzgeek.com/how-tos/linux/debian/how-to-install-apache-tomcat-on-debian-11.html)
