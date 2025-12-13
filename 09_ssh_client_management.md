### SSH Client Management
```bash
sudo nano /etc/ssh/sshd_config
#add line at bottom
DenyUsers root user1 user2
```
Add groups
```bash
sudo addgroup owner_group
sudo addgroup client_group
```
Add users
```bash
sudo useradd -m owner_user && sudo passwd owner_user
sudo useradd -m client_user1 && sudo passwd client_user1
sudo useradd -m client user2 && sudo passwd client_user2
```
Link users to group
```bash
sudo usermod -aG owner_group owner_user
sudo usermod -aG client_group client_user1
sudo usermod -aG client_group client_user2
```
Disable system controls
```bash
sudo visudo
#sudoers file will open then goto 'Command Aliases' section
Cmnd_Alias SHUTDOWN=/sbin/shutdown, /sbin/reboot, /sbin/halt, /sbin/poweroff, /bin/su
Cmnd_Alias SYSTEM_CONTROL=/bin/systemctl
#goto %sudo section, add lines after %sudo
%owner_group ALL=(ALL) ALL, !SHUTDOWN
%client_group ALL=(ALL) ALL, !SHUTDOWN, !SYSTEM_CONTROL
#save file
reboot
```
