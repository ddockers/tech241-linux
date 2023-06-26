Processes

#! /bin/bash

# update
sudo apt update -y

# upgrade
sudo apt upgrade -y

# install nginx
sudo apt install nginx -y

# restart nginx
sudo systemctl restart nginx

# enable nginx - will autostart on reboot
sudo systemctl enable nginx

Environment variable
- Value stored variable
accessible by other tools in Linux
set: `export MYNAME=deanne`
retrieve: `printenv MYNAME`

Normal Variable
To set  variable, `MYNAME=deanne`
To retrieve it, `$MYNAME`


To make a persistent environment variable 
go into .bashrc and edit it there
if in there currently, reload: source .bashrc

Processes
2 types - system and user
Every process has a processor id PID

`ps` for user processes

`ps aux` for all processes inc system processes

`sudo systemctl` controls system processes

## Start then kill a process
`sleep` puts system to sleep for however many seconds is specified
`sleep 5000 &` lists PID as well
### Gentle kill
`kill -1 [PID NUMBER]`

### Harsher kill
`kill 3000` without the signal(`-1` or others). It automatically uses `-15`, which is terminate.

If you kill a parent process it will also kill the child process

### What if the parent process doesn't die?
`kill -9` brute force kill, kills parent processes. But child processes might not die and they will be zombie processes.

Sparta test app
- node js app
- port 3000
- 2 features
  - front page (no database)
  - posts - displats data retrieved from the database

Requirements to run Sparta app
1. Linum VM - Ubuntu 18.04 LTS
2. web server - nginx
3. right version of node js - version 12 (dependency)
4. app folder
5. inside app folder, run 2 commands:
   1. npm install (note package manager
   2. node app.js OR npm start