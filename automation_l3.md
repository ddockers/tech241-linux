# Automation L3 - Modify app VM script to use database VM

## Overview
The final app VM script will need to run after the database VM script is has finished running on the database VM.

The app VM script already created in *Automation L1* needs to be modified so that **the environment variable `DB_HOST` is created just before the app is installed**.

## DOD (definition of done)
1. The DB VM script runs successfully on a fresh Linux VM (running Ubuntu 18.04 LTS)
2. After the DB VM script finishes running, the app VM script runs successfully on a fresh Linux VM (running Ubuntu 18.04 LTS)
3. The Sparta app (including the posts page) comes up in the web browser when you go to the app VM's public IP

## DB App
The DB app needs to be running forst, so that the main app can use information for the DB app.

```
#!/bin/bash

# Update and upgrade the system
sudo apt update -y
sudo apt upgrade -y

#to download key for the right version (from mongo db website)
wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -

# source list
echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

# update again
sudo apt update -y

# install mongo db
sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20

# Configure bindIp to 0.0.0.0
sudo sed -i 's/bindIp: 127.0.0.1/bindIp: 0.0.0.0/g' /etc/mongod.conf

# Start Mongo DB
sudo systemctl start mongod

# Enable Mongo DB
sudo systemctl enable mongod
```

## Main App
It's in the below code where the new environment variable `DB_HOST` is added.

```
#!/bin/bash


# update
sudo apt update -y

# upgrade
sudo apt upgrade -y

# install nginx
sudo apt install nginx -y

# restart nginx
sudo systemctl restart nginx

# enable nginx
sudo systemctl enable nginx

# get from url needed version of node
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -
# install nodejs
sudo apt install nodejs -y

#installing pm2 that helps run apps in the background
sudo npm install pm2 -g

# getting app folder to the VM
git clone http://github.com/jungjunggg/tech241_sparta_app.git app2

#getting inside app folder
cd /home/adminuser/app2/app

#Creating DB_HOST env variable
export DB_HOST=mongodb://20.162.216.138:27017/posts

# installing the app
npm install

# starting the app in the background by using pm2 (node process managers)
pm2 start app.js
```