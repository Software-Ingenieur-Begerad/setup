# Setup Remote Desktop Protocol (RDP) Client

* update Apt repository cache
```
sudo apt update
```

* Using Apt install Remmina RDP client using Debian 11 default repository. NOTE: A restart of the operation system (like ```sudo shutdown -r now```) might be neseccary to add RDP to the available connection protocols.
```
sudo apt install remmina remmina-plugin-rdp remmina-plugin-secret remmina-plugin-spice --no-install-recommends
```

* start Remmina
```
remmina
```

* configure a connection and connect
```
Name: <optional>
Protocol: RDP
Server: <IP address of target computer>
User name: <tbd>
User password: <tbd>
Domain: <tbd>
```
