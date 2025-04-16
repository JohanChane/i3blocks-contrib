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

Add current user to `i2c` group:

```sh
sudo usermod -aG i2c $USER  # Relogin required after this command
groups  # Verify group membership changes
```

Check the capabilities:

```sh
ddcutil capabilities | grep "Feature: 10"
```

Detect:

```sh
ddcutil detect
```

## Dependencies

- `xorg-xset`
- `ddcutil`

For example: ArchLinux

```sh
pacman -S xorg-xset
pacman -S ddcutil
lsmod | grep -i 'i2c'   # Check if the i2c module is loaded in the kernel
```
