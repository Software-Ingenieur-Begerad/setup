# Connect To VPN

* get the latest version of installed packages and refresh the repo cache
```
sudo apt update
```

* install VPN client directly from the official repository
```
sudo apt install openvpn --no-install-recommends
```

* connect to VPN
```
sudo openvpn --config <configuration file *.ovpn>
```
