# wl-wheel-scroll

Circular rim scrolling daemon for Wayland touchpads. Move your finger around the edge of the pad to scroll — like a scroll wheel.

Built for the Panasonic Let's Note wheel pad but works on any touchpad with a circular rim zone.

## Install

```sh
git clone https://github.com/hq9afk/wl-wheel-scroll.git
cd wl-wheel-scroll
makepkg -si
```

Then run prerequisites:

```bash
sudo usermod -aG input $USER
sudo modprobe uinput
sudo udevadm control --reload && sudo udevadm trigger
```

Log out and back in for group membership to take effect.

Then enable the systemd user service:

```sh
systemctl --user enable --now wl-wheel-scroll.service
```

## Uninstall

```sh
sudo pacman -R wl-wheel-scroll
```

## Tuning

Edit `~/.config/wl-wheel-scroll/config.ini` (created automatically on first run if absent). Changes are picked up live — no restart needed. Any keys missing from an existing file fall back to the defaults below.

```ini
[scroll]
# outer fraction of pad radius that triggers rim scrolling (0-1)
rim_threshold = 0.75

# radians of rotation per scroll tick — smaller = more sensitive
angle_per_tick = 0.15

# REL_WHEEL units per tick
scroll_speed = 1

# seconds before state resets if touch is lost
touch_timeout = 0.5

# true to scroll horizontally instead of vertically
horizontal_scroll = false
```
