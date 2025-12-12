### SSH and Firewall
```bash
#install ssh
sudo apt install openssh-server
sudo systemctl start ssh.service
sudo systemctl enable ssh.service
#check ssh status
sudo systemctl status ssh.service
```
Firewall
```bash
#give PORT access
sudo ufw allow 22
#activate firewall
sudo ufw enable
#check firewall status
sudo ufw status

#TO DISABLE FIREWALL
sudo ufw reset
```
