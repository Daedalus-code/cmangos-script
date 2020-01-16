# C(ontinued)-MaNGOS
admin helper in bash  
This script was build on a Ubuntu 19.10 - Linux 5.3.0-1014-raspi2 - (Raspberry Pi2/4)  
https://ubuntu.com/download/raspberry-pi

![alt text](https://i.imgur.com/KUucM03.png)

edit server.cnf & server.txt  
edit inside mangos script at line 21: 
```
source /scripts/server.txt # please edit if wrong.
```  
# Services
Server is using systemd Services to run mangosd and realmd:  


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

https://github.com/cmangos  
https://cmangos.net  





---What
