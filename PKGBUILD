# Maintainer: Levente Polyak <anthraxx@archlinux.org>
# Maintainer: Daniel M. Capella <polyzen@archlinux.org>
# Maintainer: T.J. Townsend <blakkheim@archlinux.org>
# Contributor: Thorsten Töpper <atsutane-tu@freethoughts.de>
# Contributor: Jelle van der Waa <jelle@vdwaa.nl>

pkgname=i3-wm
pkgver=4.23
pkgrel=3
pkgdesc='Improved dynamic tiling window manager'
arch=('x86_64')
url="https://i3wm.org"
license=('BSD')
groups=('i3')
depends=('libev' 'libxkbcommon-x11' 'pango' 'startup-notification' 'ttf-font'
         'xcb-util-cursor' 'xcb-util-keysyms' 'xcb-util-wm' 'xcb-util-xrm'
         'yajl')
makedepends=('asciidoc' 'git' 'meson' 'xmlto')
optdepends=('dmenu: for the default program launcher'
            'rofi: for a modern dmenu replacement'
            'i3lock: for the default screen locker'
            'xss-lock: for the default screen locker'
            'i3status: for the default status bar generator'
            'perl: for i3-save-tree and i3-dmenu-desktop'
            'perl-anyevent-i3: for i3-save-tree'
            'perl-json-xs: for i3-save-tree')
replaces=('i3' 'i3bar' 'i3-gaps')
provides=('i3-gaps')
backup=('etc/i3/config')
#source=("$url/downloads/i3-$pkgver.tar.xz"{,.asc})
source=("git+https://github.com/i3/i3.git?signed#tag=${pkgver}")
b2sums=('695474513c3987843c3f8c9352cbaeae2268628ae81a57f97bd870120dbab2b45e94f6c0cd6aea2b05c8b5a0d6aea52e03a599c03fb03d81bf9656284c4dd51f'
        'SKIP'
        'tabbed-and-stacked-indic.patch')
validpgpkeys=('424E14D703E7C6D43D9D6F364E7160ED4AC8EE1D') # Michael Stapelberg <michael@stapelberg.de>

prepare() {
  cd i3

  patch -Np1 -i ../../tabbed-and-stacked-indic.patch
}

build() {
  cd i3
  arch-meson build -Dmans=true
  ninja -C build
}

package() {
  cd i3
  DESTDIR="$pkgdir" ninja -C build install
  install -Dm644 -t "$pkgdir"/usr/share/licenses/$pkgname LICENSE
}

# vim:set ts=2 sw=2 et:
