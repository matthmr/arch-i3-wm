# Maintainer: Levente Polyak <anthraxx@archlinux.org>
# Maintainer: Daniel M. Capella <polyzen@archlinux.org>
# Maintainer: T.J. Townsend <blakkheim@archlinux.org>
# Contributor: Thorsten Töpper <atsutane-tu@freethoughts.de>
# Contributor: Jelle van der Waa <jelle@vdwaa.nl>

pkgname=i3-wm
pkgver=4.24
pkgrel=1
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
source=("git+https://github.com/i3/i3.git?signed#tag=${pkgver}")
b2sums=('0ddae1f84952bc9cab4225fea1a76e9fda26414dc7d920aee4fb78c2914452ebea932a57e83c175a29362ee457d15226a85c5c5fe32d1eaf508ef4ebcd8e318a'
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
