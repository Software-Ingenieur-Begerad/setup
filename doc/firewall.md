# Setup Ufw Firewall

* get the latest version of installed packages and refresh the repo cache
```
sudo apt update
```

* install firewall directly from the official repository
```
sudo apt install ufw --no-install-recommends
```

* configure ports and update firewall
```
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow <port>
sudo ufw enable
sudo ufw status numbered
```

# Links

[Initial Server Setup with Debian 10](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-debian-10#step-4-%E2%80%94-setting-up-a-basic-firewall)
