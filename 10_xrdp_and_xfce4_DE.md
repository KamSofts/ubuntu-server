## Connect server using SSH

### On Server 
```bash
ip a
#output : note <IP-ADDRESS> 
#in my case 192.168.0.104 (WLAN Connection)
```

### On Client
```bash
#if PORT = 22 (Default PORT)
ssh owner_user@192.168.0.104
#if different PORT NUMBER like PORT = 8022
ssh -p 8022 owner_user@192.168.0.104
#enter owner_user's password
```

### XRDP AND XFCE4-DE (Internet connection required)
```bash
#insall xrdp and xfce4 desktop environment
sudo apt install xrdp
sudo apt install xfce4 xfce4-goodies

#configure
sudo nano /etc/xrdp/startwm.sh
#append line at bottom
startxfce4
#save and close startwm.sh

#configure to owner_user
echo xfce4-session > ~/.xsession

#configure to client_user1
su client_user1
#enter client_user1 password
echo xfce4-session > /home/client_user1/.xsession
#exit from client_user1. return to owner_user
exit

#change firewall setting
sudo ufw allow 3389/tcp
sudo systemctl start xrdp
sudo systemctl enable xrdp

#disable GUI on server (enable only for user)
sudo systemctl set-default multi-user.target
exit
```

### On Server
```bash
reboot
```



