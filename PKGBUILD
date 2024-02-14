# Maintainer: Brod8362 <brod8362@gmail.com>

pkgname=usb-notify-git
_pkgname=${pkgname%-git}
pkgver=0.0.0
pkgrel=00
pkgdesc="USB notifier daemon"
arch=('any')
license=('MIT')
url='https://github.com/brod8362/usb-notify'
source=("$pkgname::git+$url.git")
sha256sums=('SKIP')
depends=(
    'libnotify'
)
provides=(
    'usb-notify'
)

pkgver() {
  cd "$srcdir/$pkgname"

  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
    cd "$srcdir/$pkgname"
    make clean
}

build() {
    cd "$srcdir/$pkgname"
    make -B
}

package() {
    cd "$srcdir/$pkgname"
    install -Dm0755 -t "$pkgdir/usr/bin/" "bin/usb-notify"
    install -Dm0644 -t "$pkgdir/usr/lib/systemd/user" "usb-notify.service"
}
