# Connecting Sparta App with Database App

Create a new database (DB) VM

Use existing key pairs stored in Azure

New VM is `adminuser@tech241-deanne-man-db`

Use GitBash to ssh into the new VM.

First thing to do on a new VM is to update and upgrade
`sudo apt update -y` then `sudo apt upgrade -y`

## Requirements to run the Sparta app
1. Linux VM with image Ubuntu 18.04 LTS Gen 2
2. Update & Upgrade
3. Web server nginx (this is a dependency)
4. Correct version of node js version 12 (this is also a dependency)
5. App folder
6. Run `npm install`
7. `node app.js` or `npm start`





## Requirements to run DB VM
1. Linux VM with image Ubuntu 18.04 LTS Gen 2
2. Update & Upgrade
3. We need to install a db called *Mongo*. It's a document database.
Once it's installed, we need to configure it so that it will accept connections from any VM. It's set up by default to only accept connections from the same machine. We have to change it so it will accept connections from other machines.
   
### Installation of Mongo
Download the key for the ruight version, which you can get from the mongo website.
```
wget -qO - https://www.mongodb.org/static/pgp/server-3.2.asc | sudo apt-key add -
```
We need to specify the mongo db version in the source list of packages.
```
echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.2.list
```
*Sources list* is written in this command.

Then we'll need to update **again**.

After this is dome, we need to install.

```
sudo apt-get install -y mongodb-org=3.2.20 mongodb-org-server=3.2.20 mongodb-org-shell=3.2.20 mongodb-org-mongos=3.2.20 mongodb-org-tools=3.2.20
```

### Configure mongo db to accept connections from app VM
Final step is to configure the mongo database. To do this we can navigate to the mongo nano configuration file.

```
sudo nano /etc/mongod.conf
```
Scrolling down to `# network interfaces` we can see the port that mongo db is going to use.

Now we need to open it up so that it can accept requests from any outside machine.

At `bindIP:` change the IP address to `0.0.0.0` so that any machine can access it.

**This must only be done for testing purposes**

Save then exit.

We can use `cat nano /etc/mongod.conf` to print the file to the screen.

Start mongo db
```
sudo systemctl start mongod
```

Check status to see if it's running
```
sudo systemctl status mongod
```

Enable mongod to run on every restart
```
sudo systemctl enable mongod
```

## Connecting the two VMs

Ensure both VMs are running.

Navigate to app folder in app VM.

Create an environment variable to store the IP address. IP address can be found on DB VM on Azure.

```
export DB_HOST=mongodb://<IP ADDRESS>:27017/posts
```
Check if it's there using `printenv DB_HOST`.

A new inbound security rule needs to be added to the network. Destination port ranges should be *27017*.