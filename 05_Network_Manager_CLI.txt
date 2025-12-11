## Network Manager Command Line Interface - nmcli

```bash
sudo apt install network-manager
```
Hardware
```bash
#power on wifi
nmcli r wifi on
#power off wifi
nmcli r wifi off
```

Device
```bash
#connect a new device
nmcli d wifi list
#output : get SSID from list
nmcli d wifi connect "SSID-NAME-HERE" password "PASSWORD-HERE"
```

Connection
```bash
#modify connection property
nmcli c modify "SSID-NAME-HERE" connection.metered yes
nmcli c modify "SSID-NAME-HERE" connection.autoconnect no
#to check connection property
nmcli -f connection.metered c show "SSID-NAME-HERE"

#to disconnect
nmcli c down "SSID-NAME-HERE"
#to re-connect
nmcli c up "SSID-NAME-HERE"
```

Delete or Remove Connection
```bash
nmcli c show
nmcli c delete "SSID-NAME-HERE"
```
