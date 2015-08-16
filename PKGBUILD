# Maintainer: senft <senftt@gmail.com>
pkgname=i3bar-icons-git
_gitname='i3'
pkgver=4.6.114.g454f117
pkgrel=1
pkgdesc='A patched version of i3bar that displays xbm icons'
arch=('i686' 'x86_64')
url='http://i3wm.org/'
license=('BSD')
depends=('libev' 'yajl' 'pango' 'xcb-util-image')
makedepends=('git' 'docbook-xsl' 'pkgconfig')
optdepends=('conky: For creating status output.')
conflicts=()
replaces=()
source=('git://code.i3wm.org/i3#branch=next'
        'https://raw.github.com/ashinkarov/i3-extras/master/i3bar-xbm-icons.patch')
sha1sums=('SKIP'
          'c93f9f212764ccf6e6dfc5b1bc24b363c5a5514d')

pkgver() {
  cd "$srcdir/$_gitname"
  git describe --tags | sed 's/-/./g'
}

build() {
  cd "$_gitname"
  patch -Np1 -i ../i3bar-xbm-icons.patch || return 1
  cd i3bar
  make
}

package() {
  cd "$_gitname/i3bar"
  install -D -m755 i3bar $pkgdir/usr/bin/i3bar-icons
}

# vim:set ts=2 sw=2 et:
