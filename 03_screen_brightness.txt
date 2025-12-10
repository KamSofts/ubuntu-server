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
