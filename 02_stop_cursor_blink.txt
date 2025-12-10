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

