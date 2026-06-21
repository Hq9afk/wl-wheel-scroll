# Maintainer: Hq9afk <hieubuiduc1@gmail.com>
pkgname=wl-wheel-scroll
pkgver=1.0.0
pkgrel=1
pkgdesc="Circular rim scrolling daemon for touchpads on Wayland"
arch=('any')
license=('MIT')
depends=('python' 'python-evdev')
source=("wl-wheel-scroll"
        "wl-wheel-scroll.service"
        "99-uinput.rules"
        "config.ini")
sha256sums=('fe39fb01f811040032eb2a0dadb671cca02fbdb658ab25e3fd2b6e9d037e6abe'
            'ccd7b6f2fbd5fc6be4f8694e8c7155f1390192d9e68634bef9a14176cf00147a'
            '1536c6b31c712927bb493685323939b1c096fc378f341432dd99c9b2f7c5fbc4'
            'e40c63732346306a0cd6edc254468865fe539a9578d2a3768f50d36cba32b690')

package() {
    install -Dm755 "$srcdir/wl-wheel-scroll" \
        "$pkgdir/usr/bin/wl-wheel-scroll"

    install -Dm644 "$srcdir/wl-wheel-scroll.service" \
        "$pkgdir/usr/lib/systemd/user/wl-wheel-scroll.service"

    install -Dm644 "$srcdir/99-uinput.rules" \
        "$pkgdir/usr/lib/udev/rules.d/99-uinput.rules"

    printf '%s\n' uinput | install -Dm644 /dev/stdin \
        "$pkgdir/etc/modules-load.d/uinput.conf"

    install -Dm644 "$srcdir/config.ini" \
        "$pkgdir/usr/share/wl-wheel-scroll/config.ini"
}
