# Setup Java

* download OpenJDK from the [Eclipse Foundation](https://adoptium.net/)

* extract JDK to target folder\
NOTE: Create target folder in advance
```
sudo mkdir -p /usr/lib/jvm/open-jdk-17 --
sudo tar -xvzf ./OpenJDK17U-jdk_x64_linux_hotspot_17.0.2_8.tar.gz -C /usr/lib/jvm/open-jdk-17 --strip-components=1
sudo mkdir -p /usr/lib/jvm/open-jdk-11 --
sudo tar -xvzf ./OpenJDK11U-jdk_x64_linux_hotspot_11.0.14.1_1.tar.gz -C /usr/lib/jvm/open-jdk-11/ --strip-components=1
```

* check if any JDK is already installed
```
java -version
update-alternatives --list java
```

* install JDK 17
```
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/open-jdk-17/bin/java 1
sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/open-jdk-17/bin/javac 1
sudo update-alternatives --install /usr/bin/jar jar /usr/lib/jvm/open-jdk-17/bin/jar 1
sudo update-alternatives --install /usr/bin/jshell jshell /usr/lib/jvm/open-jdk-17/bin/jshell 1
```

* install JDK 11
```
sudo update-alternatives --install /usr/bin/java java /usr/lib/jvm/open-jdk-11/bin/java 2
sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/open-jdk-11/bin/javac 2
sudo update-alternatives --install /usr/bin/jar jar /usr/lib/jvm/open-jdk-11/bin/jar 2
sudo update-alternatives --install /usr/bin/jshell jshell /usr/lib/jvm/open-jdk-11/bin/jshell 2
```

* chose JDK version
```
sudo update-alternatives --config java
```

* verify installation and configuratin
```
java -version
javac -version
jar --version
jshell -version
sudo update-alternatives --display java
```
