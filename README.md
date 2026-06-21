# wl-wheel-scroll

Circular rim scrolling daemon for Wayland touchpads. Move your finger around the edge of the pad to scroll — like a scroll wheel.

Built for the Panasonic Let's Note wheel pad but works on any touchpad with a circular rim zone.

## Install

```sh
git clone <repo-url>
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

Edit the constants at the top of `/usr/bin/wl-wheel-scroll`:

| Constant | Default | Description |
|---|---|---|
| `RIM_THRESHOLD` | `0.65` | How far from centre the rim zone starts (0–1) |
| `ANGLE_PER_TICK` | `0.15` | Radians of rotation per scroll tick (~8.6°) |
| `SCROLL_SPEED` | `1` | Scroll units per tick |
| `TOUCH_TIMEOUT` | `0.5` | Seconds before state resets if touch is lost |
| `HORIZONTAL_SCROLL` | `False` | Scroll horizontally instead of vertically |
