# Setup Chrome

## Update Debian

* First, update your system to ensure all existing packages are up to date.\
```
sudo apt update && sudo apt upgrade
```
## Install Required Packages

* To successfully install the browser, you will need to install the following packages; run this command if you are unsure; it will not harm your system.\
```
sudo apt install software-properties-common apt-transport-https wget ca-certificates gnupg2 --no-install-recommends
```
* These are pretty generic dependencies that may be already installed. Run the command regardless if unsure, as many other installations will require these on your system.

## Install Google Chrome Browser

### Import Google Chrome GPG Key

* The first step in installing Google Chrome is to import the GPG key for the digital signature; without this, your installation will not complete successfully.\
Import the GPG key, and use the following command.
```
sudo wget -O- https://dl.google.com/linux/linux_signing_key.pub | gpg --dearmor | sudo tee /usr/share/keyrings/google-chrome.gpg
```
* Import Google Chrome Repository.\
Once the GPG import is complete, you will need to import the Google Chrome repository.\
```
echo deb [arch=amd64 signed-by=/usr/share/keyrings/google-chrome.gpg] http://dl.google.com/linux/chrome/deb/ stable main | sudo tee /etc/apt/sources.list.d/google-chrome.list
```

### Install Google Chrome – Stable

* The next step is to update the repository list using the apt update command to reflect the new additions to the apt sources list.\
```
sudo apt update
```
* Next, install the Google Chrome stable edition, the recommended option for most users.\
```
sudo apt install google-chrome-stable --no-install-recommends
```

## How to Launch Google Chrome Browser

* Now that you have installed Chrome, you can launch the application. You can type the following command in the terminal to launch Chrome:\
```
google-chrome
```

## How to Update/Upgrade Google Chrome Browser

* Ideally, you should check for updates using the terminal often; sometimes, the GUI update notifications may update Google Chrome; run the APT update command in your terminal.\
```
sudo apt update
```
* If one is available, use the upgrade option:\
```
sudo apt upgrade
```
* Note this will update all packages (recommended), for example, to upgrade the Chrome package.\
```
sudo apt upgrade google-chrome-stable
```
