# Configure Keyboard Layout  On Debian

* check the current layout
```
less /etc/default/keyboard
```

* configure keyboard layout
```
sudo dpkg-reconfigure keyboard-configuration
```

* apply changes
```
sudo service keyboard-setup restart
```
