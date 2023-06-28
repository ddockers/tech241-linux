# Automation L2 - Configure Mongo DB VM (including bindIP) with a script

Connect to DB VM

`db_script.sh` script created.

## Script content

```
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

sed -i 's/^bindip=.*/bindip=0.0.0.0/' /etc/mongod.conf

# print mongo nano to make sure it's done
cat nano /etc/mongod.conf

# start mongo db

sudo systemctl start mongod

# enable mongo db
sudo systemctl enable mongod
```
