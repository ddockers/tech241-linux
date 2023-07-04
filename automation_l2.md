# Automation L2 - Configure Mongo DB VM (including bindIP) with a script

## Requirements to run DB VM
1. Linux VM - Ubuntu 18.04 LTS
2. Update and upgrade
3. Install mongo db - version 3.2
    - Download key for correct version
    - Source list - specify mongo db version
    - Apt update again
    - Install mongo db
4. Configure mongo db to accept connections from app VM
   - Change bindIP
   - Start mongo db
   - Enable mongo db
    

Connect to DB VM

`db_script.sh` script created.

`chmod u+x db_script.sh` to grant execute permissions.

## Script content
`bash` is the shell we're using. `#!/bin/bash` is instructions for the bash shell to run the script.

```
#!/bin/bash

# update
sudo apt update -y

# upgrade
sudo apt upgrade -y

# install mongo

wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -

# specify mongo db version
echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list

# update again
sudo apt update -y

# install mongo db
sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20

# configure bindIP to 0.0.0.0

sudo sed -i 's/bindip: 127.0.0.1/bindip: 0.0.0.0/' /etc/mongod.conf

# print mongo nano to make sure it's done
cat nano /etc/mongod.conf

# start mongo db

sudo systemctl restart mongod

# enable mongo db
sudo systemctl enable mongod
```
`./db_script.sh` to execute script.

`sudo systemctl restart mongo` - `start` could be used in place of `restart` since in this instance it means the same thing. MongoDB is not already running after installation (unlike NginX, whuch runs straight after installation).