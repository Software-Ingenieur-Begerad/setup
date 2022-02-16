# Setup Git

* update your APT cache using
```
sudo apt update
```

* install Git from Debian's APT repository
```
sudo apt install git --no-install-recommends
```

* validate installation
```
git --version
```

* provide contact details to be embedded in the commit message
```
git config --global user.name "<tbd>"
git config --global user.email "<tbd>"
```

* verify contact details
```
git config --list
```
