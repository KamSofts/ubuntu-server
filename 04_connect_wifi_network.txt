## WIFI CONNECTION
```bash
#Identify the Wi-Fi interface: 
ip a
#look for an interface starting with w, such as wlan0
sudo nano /etc/netplan/50-cloud-init.yaml
```

```yaml
network:
  version: 2
  renderer: networkd
  wifis:
    wlan0: # Replace with your actual interface name
      optional: true
      access-points:
        "SSID-NAME-HERE":
          password: "PASSWORD-HERE"
      dhcp4: true
```
save and exit from 50-cloud-init.yaml
```bash
sudo netplan apply
sudo netplan try
#check ip address
ip a
#check internet connection
ping -c 2 google.com
```
