# Setup Node

* update apt repository cache
```
sudo apt update
```

## Using APT

* install node.js and npm
```
sudo apt-get install nodejs npm --no-install-recommends
```

## Using NVM

* install curl command-line utility
```
sudo apt install curl --no-install-recommends
```

* execute NVM installation bash script with your user
```
curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash
```

* apply the new settings
```
source ~/.bashrc
```

* install latest stabe node version
```
nvm install node --lts
```

### Helpful NVM instructions

* install specific node version
```
nvm install 12.20.1
```

* list installed node versions for the current user
```
nvm ls
```

* find available node versions for installation
```
nvm ls-remote
```

* select a different node version for the current session only
```
nvm use 12.20.1
```

* find the default version for the current user
```
nvm run default --version
```

* run node script with the desired node version
```
nvm exec 12.20.1 <node script>.js
```
