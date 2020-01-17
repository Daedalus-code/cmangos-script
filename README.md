# C(ontinued)-MaNGOS  

Admin Helper Tool in bash written for (Classic fork)

![alt text](https://i.imgur.com/KUucM03.png)

#### Features

* login (command)     -  Console, Remote Access.
* check for updates   -  Checking for git updates. (core, database, helper)
* update CMaNGOS      -  Updating/Upgrading Core.
* update Database     -  Updating/Upgrading Database.
* shutdown server     -  Shut down server. (realmd, mangosd)
* restart server      -  Restart server. (realmd, mangosd)
* online check        -  Ping server. (internet/intranet)
* characters          -  Show characters on server.
* accounts            -  Show accounts on server.
* guilds              -  Show Guilds on server.
* create .patch file  -  Create patch file. (classic-mangos dir)
* update Helper       -  Updating/Upgrading Admin Helper
* check logs          -  Show logs. (Realmd.log, Server.log)
* quit                -  Exit the script.

#### What's the purpose of this tool?  
This tool introduce helping functions and features for admins running a WoW Vanilla server. 
#### How do you get it to work?
##### First time install
```mkdir /scripts/```  
```cd /scripts/```  
```git pull https://github.com/Daedalus-code/cmangos-script.git```  
```cp /scripts/cmangos-script/mangos /usr/local/bin```  
```sudo chmod +x /usr/local/bin/mangos```  

You will be able to start 'mangos' from anywhere in terminal now.  

mangos script will look for config files inside /scripts/  
You need to copy config files from cmangos-script folder into /scripts/ folder.  

```cp /scripts/cmangos-script/config.* /scripts/```  

Edit config file 'config.cnf' with MySQL credentials.   
Edit config file 'config.txt' with correct information.  
#### Your own directory for configs  
Remember to edit mangos script at line 21:    
```source /scripts/server.txt # please edit if wrong.```  
server.txt at line 39:  
```folder_helper="/scripts/cmangos-script" # please edit if wrong.```  
#### Updating/Upgrading Admin Helper  
"update Helper" will "install" mangos into /usr/local/bin and chmod it.  
There will be made a mangos.old version next to it. (non executeable)  

The updater will install automatically if any changes and then exit.  
If there is no new changes you will be asked if you want to Install regardless.  
#### Planned Features  
* Time will tell.  
#### Services  
Server is using systemd Services to run mangosd and realmd:  
Please edit username 'ubuntu' if it's wrong.

/etc/systemd/system/realmd.service  

```
[Unit]
Description=WoW Vanilla realmd service
After=network.target mysql.service

[Service]
Type=simple
User=ubuntu
ExecStart=/home/ubuntu/wow/mangos-classic/run/bin/realmd -c /home/ubuntu/wow/mangos-classic/run/etc/realmd.conf
Restart=on-abort

[Install]
WantedBy=multi-user.target
```
/etc/systemd/system/mangosd.service  

```
[Unit]
Description=WoW Vanilla mangosd service
After=network.target mysql.service realmd.service getty@tty3.service

[Service]
Type=simple
User=ubuntu
StandardInput=tty
TTYPath=/dev/tty3
TTYReset=yes
TTYVHangup=yes
WorkingDirectory=/home/ubuntu/wow/mangos-classic/run/bin
ExecStart=/home/ubuntu/wow/mangos-classic/run/bin/mangosd -c /home/ubuntu/wow/mangos-classic/run/etc/mangosd.conf -a /home/ubuntu/wow/mangos-classic/run/etc/playerbot.conf
Restart=on-abort

[Install]
WantedBy=multi-user.target
```
Make sure to reload systemd so that the new files are discovered.
```
sudo systemctl daemon-reload
```
The command to ensure both services are automatically started at boot are:
```
sudo systemctl enable realmd
sudo systemctl enable mangosd
```

This script was build on a Ubuntu 19.10 - Linux 5.3.0-1014-raspi2 - (Raspberry Pi2/4)  
https://ubuntu.com/download/raspberry-pi  

C(ontinued)-MaNGOS (Classic fork)

https://github.com/cmangos/mangos-classic  
https://github.com/cmangos/classic-db  
https://github.com/cmangos  
https://cmangos.net  





---What
