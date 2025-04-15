# backlight-ddc

Show the external screen brightness value given by `ddcutil`.
Clicking uses `xset` to turn off the backlight, scrolling increases or decreases
the brightness.

## Setup / Usage

Example i3blocks configuration:

```
[backlight-ddc]
#command=$SCRIPT_DIR/backlight-ddc/backlight-ddc
#label=☀
label=BL
interval=once
signal=13
#STEP=1
#DISPLAY_NUM=1  # Use ddcutil detect to check
```

- right click: turn off backlight
- scroll: increase/decrease the brightness in percentage steps according to `STEP`

## Dependencies

- `xorg-xset`
- `ddcci-driver-linux-dkms`
- `ddcutil`

For example: ArchLinux

```sh
pacman -S xorg-xset
pacman -S ddcci-driver-linux-dkms   # reboot after install
pacman -S ddcutil
lsmod | grep -i 'i2c'   # Check if the i2c module is loaded in the kernel
```
