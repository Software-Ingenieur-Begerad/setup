# Connect To VPN

* get the latest version of installed packages and refresh the repo cache
```
sudo apt update
```

* install VPN client directly from the official repository
```
sudo apt install openvpn --no-install-recommends
```

* install openresolv (a resolvconf implementation, i.e. a resolv.conf management framework)
```
sudo apt install openresolv --no-install-recommends
```

* append the following configuration to the OpenVPN client configuration file
```
script-security 2
up /etc/openvpn/update-resolv-conf
down /etc/openvpn/update-resolv-conf
```

* call client to connect to VPN
```
sudo openvpn --config <configuration file *.ovpn> --ca <certification authority file *ca.pem> --cert <certificate file *cert.pem --key <key file *cert.key
```

* verify that ```resolvconf``` works properly\
NOTE: You should see a ```resolv.conf``` file updated by
```resolvconf``` instead of e.g. ```NetworkManager```
```
cat /etc/resolv.conf
```

# Links

[How to configure OpenVPN to resolve local DNS & hostnames](https://steamforge.net/wiki/index.php/How_to_configure_OpenVPN_to_resolve_local_DNS_&_hostnames)
