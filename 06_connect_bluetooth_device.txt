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
