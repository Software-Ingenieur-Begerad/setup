# Configure Lid Switch On Debian

* edit /etc/systemd/logind.conf and make sure to configure like this\
to make the OS ignore the lid being closed
```
HandleLidSwitch=ignore
```

* reload logind.conf to make your changes go into effect\
```
sudo systemctl restart systemd-logind
```
