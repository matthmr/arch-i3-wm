# Maintainer: Thorsten Töpper <atsutane-tu@freethoughts.de>

pkgname=i3-wm
_pkgsourcename=i3
pkgver=4.7.2
pkgrel=1
pkgdesc='An improved dynamic tiling window manager'
arch=('i686' 'x86_64')
url='http://i3wm.org/'
license=('BSD')
replaces=('i3' 'i3bar')
groups=('i3')
depends=('xcb-util-cursor' 'xcb-util-keysyms' 'xcb-util-wm' 'libev' 'yajl'
         'startup-notification' 'pango')
makedepends=('bison' 'flex')
optdepends=('dmenu: As menu.'
            'i3lock: For locking your screen.'
            'i3status: To display systeminformation with a bar.')
options=('docs' '!strip')
source=("http://i3wm.org/downloads/${_pkgsourcename}-${pkgver}.tar.bz2"
        "http://i3wm.org/downloads/${_pkgsourcename}-${pkgver}.tar.bz2.asc")
md5sums=('64141f7c23f97cd1e52c52918476c1c8'
         'SKIP')

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
  install -Dm644 man/i3bar.1 \
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
  install -Dm644 man/i3-dmenu-desktop.1 \
    ${pkgdir}/usr/share/man/man1/i3-dmenu-desktop.1
  install -Dm644 man/i3-dump-log.1 \
    ${pkgdir}/usr/share/man/man1/i3-dump-log.1
  install -Dm644 man/i3-sensible-editor.1 \
    ${pkgdir}/usr/share/man/man1/i3-sensible-editor.1
  install -Dm644 man/i3-sensible-pager.1 \
    ${pkgdir}/usr/share/man/man1/i3-sensible-pager.1
  install -Dm644 man/i3-sensible-terminal.1 \
    ${pkgdir}/usr/share/man/man1/i3-sensible-terminal.1

  install -Dm644 LICENSE \
    ${pkgdir}/usr/share/licenses/${pkgname}/LICENSE
  
  make clean
}

# vim:set ts=2 sw=2 et:
