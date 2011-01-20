# Maintainer: Thorsten Töpper <atsutane-tu@freethoughts.de>

pkgname=i3-wm
_pkgsourcename=i3
pkgver=3.e_bf2
_pkgver=3.e-bf2
pkgrel=1
pkgdesc="An improved dynamic tiling window manager"
arch=('i686' 'x86_64')
url="http://i3.zekjur.net/"
license=('BSD')
replaces=("i3")
groups=("i3")
depends=('libx11' 'xcb-util' 'libev' 'yajl')
makedepends=('bison' 'flex')
optdepends=('rxvt-unicode: The terminal emulator used in the default config.'
            'dmenu: As menu.')
options=('docs' '!strip')
source=(http://i3.zekjur.net/downloads/${_pkgsourcename}-${_pkgver}.tar.bz2)
md5sums=('dc2c59623fdc9e69003b8807a0443544')

build() {
  cd "$srcdir/$_pkgsourcename-$_pkgver"
  
  make
}

package() {
  cd "$srcdir/$_pkgsourcename-$_pkgver"

  make DESTDIR="$pkgdir/" install
  
  install -Dm644 man/i3.1 \
    ${pkgdir}/usr/share/man/man1/i3.1
  install -Dm644 man/i3-msg.1 \
    ${pkgdir}/usr/share/man/man1/i3-msg.1
  install -Dm644 man/i3-input.1 \
    ${pkgdir}/usr/share/man/man1/i3-input.1
  install -Dm644 LICENSE \
    ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE
  
  #i3-wsbar will be provided by another package
  rm ${pkgdir}/usr/bin/i3-wsbar

  make clean
}

# vim:set ts=2 sw=2 et:
