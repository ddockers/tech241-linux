# Automation L1 - Start the Sparta app with a script (no database)

New VM created

`new_script.sh` nano script created.

### Script Commands
```
#! /bin/bash

# update
sudo apt update -y

# upgrade
sudo apt upgrade -y

# install nginx
sudo apt install nginx -y

# restart nginx
sudo systemctl restart nginx

# enabie nginx
sudo systemctl enable nginx

# install nodejs

curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -

sudo apt install nodejs -y

sudo npm install pm2 -g
```

**TBC**