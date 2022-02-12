# Enable Firewall

* install UFW (Uncomplicated Firewall)
```
sudo apt install ufw --no-install-recommends
```

* enable ufw and configure rules
```
sudo ufw enable
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow <tbd>/tcp
sudo ufw status numbered
```
