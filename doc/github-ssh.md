# Connect To GitHub Using SSH

* check if existing SSH keys are present
```
ls -al ~/.ssh
```

* create a new SSH key
```
ssh-keygen -t ed25519 -C "<tbd: email address>"
```

* verify SSH key
```
ls -al ~/.ssh
```

* start the ssh-agent in the background
```
eval "$(ssh-agent -s)"
```

* list keys managed by the agent
```
ssh-add -l
```

* add SSH private key to the ssh-agent
```
ssh-add ~/.ssh/id_ed25519
```

* copy the SSH public key to your clipboard and add it to [GitHub](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)
```
cat ~/.ssh/id_ed25519.pub
```
