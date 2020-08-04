# C(ontinued)-MaNGOS - Helper  
  
Admin Helper Tool in bash  
![alt text](https://i.imgur.com/GBLQoJj.png)

#### Features

* login (command)     -  Console, Remote Access, Stats
* create account      -  Create/Delete Account
* check for updates   -  Checking for git updates. (core, database, helper)
* update CMaNGOS      -  Updating/Upgrading Core.
* update Database     -  Updating/Upgrading Database.
* update Helper       -  Updating/Upgrading Admin Helper
* shutdown server     -  Shut down server. (realmd, mangosd)
* restart server      -  Restart server. (realmd, mangosd)
* characters          -  Show characters on server.
* accounts            -  Show accounts on server.
* guilds              -  Show guilds on server.
* config              -  Edit config files (run/etc)
* patch               -  Create/Apply patch file. (classic-mangos dir)
* ping                -  Ping server. (internet/intranet)
* logs                -  Show logs. (Realmd.log, Server.log)
* quit                -  Exit the script.  
##### Note  
"Update Database" Converting myisam -> innodb? Works on MariaDB.  

#### What's the purpose of this tool?  
This tool introduce helping functions and features for admins running a WoW Vanilla server. 
#### How do you get it to work?
##### First time install
```mkdir /scripts/```  
```cd /scripts/```  
```git clone https://github.com/Daedalus-code/cmangos-script.git```  
```sudo cp /scripts/cmangos-script/mangos /usr/local/bin```  
```sudo chmod +x /usr/local/bin/mangos```  

You will be able to start 'mangos' from anywhere in terminal now.  

mangos script will look for config files inside your "install folder" (default: /scripts)  
You need to copy config files from cmangos-script folder into your "install folder".  

```cp /scripts/cmangos-script/server.* /scripts/```  

Edit config file 'server.cnf' with MySQL credentials.   
Edit config file 'server.txt' with correct information.  
#### Your own directory for configs?  

Edit mangos script at line 25:    
```source /scripts/server.txt # please edit if wrong.```  
server.txt at line 55:  
```folder_helper="/scripts/cmangos-script" # please edit if wrong.```  
server.txt at line 66:  
```sql_mycnf="/scripts/server.cnf" # please edit if wrong.```  
server.txt at line 51:  
```folder_install="/scripts" # please edit if wrong.```  
  
#### Planned Features  
* Time will tell.  

This script was built on a Ubuntu Linux System (Raspberry Pi4)  
https://ubuntu.com/download/raspberry-pi  

C(ontinued)-MaNGOS (Classic fork)

https://github.com/cmangos/mangos-classic  
https://github.com/cmangos/classic-db  
https://github.com/cmangos  
https://cmangos.net  





---What
