# Nginx Reverse Proxy

## What are ports?
In computer networking, a port or port number is a number assigned to uniquely identify a connection endpoint and to direct data to a specific service. 

Within an OS, a port is a logical construct that identifies a specific process or a type of network service.

## What is a reverse proxy? How is it different to a proxy?

A proxy (or forward proxy) enables computers isolated on a private network to connect to the public internet. A reverse proxy enables computers on the internet to access a private subnet.

<REVERSE/PROXY DIAGRAM>

## What is Nginx's default configuration
The default configuration for Nginx is proxy.

## How do you set up a Nginx reverse proxy?
1. Install Nginx on your Windows or Linux server.
2. Add the Nginx proxy_pass setting in a virtual host or the default config file.
3. Map a context root to the URL of a backend server. (Optional - set headers for the Nginx reverse proxy to use with the backend).
4. Restart Nginx reverse proxy and test the reverse proxy setup

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
```
**Ensure proxy_pass setting is added. It maps an incoming URL to a backend server.**
```
sudo nano /etc/nginx/sites-available/defaul
```
In the default file, `try_files $uri $uri/ =404;` needs to be changed to `proxy_pass http://localhost:3000;`.

Then nginx will need to be restarted.

`sudo systemctl restart nginx`

Command to setup nginx as a reverse proxy:

`sudo sed -i 's@try_files .*;@proxy_pass http://localhost:3000;@' /etc/nginx/sites-available/default`

## Script
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

# setup nginx as a reverse proxy
sudo sed -i 's@try_files .*;@proxy_pass http://localhost:3000;@' /etc/nginx/sites-available/default

# restart nginx again
sudo systemctl restart nginx

# get from url needed version of node
curl -sL https://deb.nodesource.com/setup_12.x | sudo -E bash -

# install nodejs
sudo apt install -y nodejs

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

# starting the app
pm2 -f start app.js
```
