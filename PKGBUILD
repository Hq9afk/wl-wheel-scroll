# Maintainer: Hq9afk <hieubuiduc1@gmail.com>
pkgname=wl-wheel-scroll
pkgver=1.0.0
pkgrel=1
pkgdesc="Circular rim scrolling daemon for touchpads on Wayland"
arch=('any')
license=('MIT')
depends=('python' 'python-evdev')
install=wl-wheel-scroll.install
source=("wl-wheel-scroll"
        "wl-wheel-scroll.service"
        "99-uinput.rules")
sha256sums=('SKIP'
            'SKIP'
            'SKIP')

package() {
    install -Dm755 "$srcdir/wl-wheel-scroll" \
        "$pkgdir/usr/bin/wl-wheel-scroll"

    install -Dm644 "$srcdir/wl-wheel-scroll.service" \
        "$pkgdir/usr/lib/systemd/user/wl-wheel-scroll.service"

    install -Dm644 "$srcdir/99-uinput.rules" \
        "$pkgdir/usr/lib/udev/rules.d/99-uinput.rules"

    printf '%s\n' uinput | install -Dm644 /dev/stdin \
        "$pkgdir/etc/modules-load.d/uinput.conf"
}
