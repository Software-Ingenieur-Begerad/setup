# Setup Cups Printing Service

* get the latest version of installed packages and refresh the repo cache
```
sudo apt update
```

* install driver and cups from the official repository
```
sudo apt install printer-driver-all --no-install-recommends
sudo apt install cups --no-install-recommends
```

* install firewall and update with cups web interface port ```631``` like [this](firewall.md)

* enable cups access from network clients by editing ```/etc/cups/cupsd.conf```
```
sudo vi /etc/cups/cupsd.conf
```

* change the following values in ```sudo vi /etc/cups/cupsd.conf```
```
Listen <host>:631


# Show shared printers on the local network.
BrowseAddress All

# Default authentication type, when authentication is required...
DefaultAuthType Basic

# Restrict access to the server...
Allow All

# Restrict access to the admin pages...
Allow All

# Restrict access to configuration files...
Allow All
```

* add user <user> to group ```ldamin```
```
sudo usermod -a -G lpadmin <user>
```

* restart cups service
```
sudo systemctl restart cups
```

* open http://192.168.178.51:631/ in web browser on any client in the network

* follow cups web interface to add network printer and share it with clients
