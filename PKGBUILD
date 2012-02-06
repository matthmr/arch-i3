# Maintainer: Thorsten Töpper <atsutane-tu@freethoughts.de>

pkgname=i3-wm
_pkgsourcename=i3
pkgver=4.1.2
pkgrel=4
pkgdesc="An improved dynamic tiling window manager"
arch=('i686' 'x86_64')
url="http://i3wm.org/"
license=('BSD')
replaces=("i3" "i3bar")
groups=("i3")
depends=('libxcursor' 'xcb-util-wm' 'xcb-util-keysyms' 'libev' 'yajl' 'startup-notification' 'pcre')
makedepends=('bison' 'flex')
optdepends=('rxvt-unicode: The terminal emulator used in the default config.'
            'dmenu: As menu.'
            'i3lock: For locking your screen.'
            'i3status: To display systeminformation with a bar.'
            'perl: To migrate your configuration to v4 format.')
options=('docs' '!strip')
source=("http://i3wm.org/downloads/${_pkgsourcename}-${pkgver}.tar.bz2")
md5sums=('0e81c381f9bf3ebf155aaa394e71834f')

build() {
  cd "$srcdir/$_pkgsourcename-$pkgver"
  
  # In order to avoid problems with bison use only a single process
  MAKEFLAGS="-j1"
  make
}

package() {
  cd "$srcdir/$_pkgsourcename-$pkgver"

  make DESTDIR="$pkgdir/" install
  
  install -Dm644 man/i3.1 \
    ${pkgdir}/usr/share/man/man1/i3.1
  install -Dm644 i3bar/doc/i3bar.1 \
    ${pkgdir}/usr/share/man/man1/i3bar.1
  install -Dm644 man/i3-config-wizard.1 \
    ${pkgdir}/usr/share/man/man1/i3-config-wizard.1
  install -Dm644 man/i3-input.1 \
    ${pkgdir}/usr/share/man/man1/i3-input.1
  install -Dm644 man/i3-msg.1 \
    ${pkgdir}/usr/share/man/man1/i3-msg.1
  install -Dm644 man/i3-migrate-config-to-v4.1 \
    ${pkgdir}/usr/share/man/man1/i3-migrate-config-to-v4.1
  install -Dm644 man/i3-nagbar.1 \
    ${pkgdir}/usr/share/man/man1/i3-nagbar.1
  install -Dm644 LICENSE \
    ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE
  
  make clean
}

# vim:set ts=2 sw=2 et:
