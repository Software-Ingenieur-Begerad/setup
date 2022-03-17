# Setup Pip3

* update apt repository cache
```
sudo apt update
```

* check available Python version
```
python3 -V
```

* install Pip3 for Python 3
```
sudo apt install python3-venv python3-pip --no-install-recommends
```

* validate Pip3 version
```
pip3 --version
```

* extend PATH environment variable so that Pip3 is able to install packages locally to the user environment
```
env | grep PATH
export PATH="$PATH:/home/$USER/.local/bin"
env | grep PATH
```

# Links

[Install Pip3 & Pip2 on Debian 11/10/9](https://computingforgeeks.com/how-to-install-pip-2-pip-3-on-debian/)
