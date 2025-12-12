# Ubuntu Server tty commands

## SET FONT
```bash
sudo dpkg-reconfigure console-setup
```
* UTF-8
* Guess optimal character set
* TerminusBold
* 14x28

## STOP CURSOR BLINK
```bash
echo "w /sys/class/graphics/fbcon/cursor_blink - - - - 0" \
| sudo tee /etc/tmpfiles.d/cursor_blink.conf
reboot
```

## HIDE CURSOR
```bash
setterm -cursor off
setterm -cursor on
```

## SET SCREEN BRIGHTNESS
```bash
ls /sys/class/backlight/
#output : like intel_backlight

#[device_name] = intel_backlight
cat /sys/class/backlight/[device_name]/max_brightness
#output : like 96000
cat /sys/class/backlight/[device_name]/brightness
#output : current brightness value

#set brightness as you wish
echo 960 | sudo tee /sys/class/backlight/[device_name]/brightness
```
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
### Connect Bluetooth Device (Pairing Keyboard)

```bash
sudo apt update
sudo apt install bluez
sudo bluetoothctl
#[BT#] mode
power on
agent on
default-agent
exit
#to pair
sudo bluetoothctl
#[BT#] mode
scan on
#output : device list with MAC-ADDRESS
pair MAC-ADDRESS
trust MAC-ADDRESS
connect MAC-ADDRESS
exit
```
### Check Battary Percentage

```bash
#for laptops
cat /sys/class/power-supply/BAT0/capacity
```
