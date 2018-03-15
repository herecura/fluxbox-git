# Maintainer: Eric Bélanger <eric@archlinux.org>

_gitname=fluxbox
pkgname="$_gitname-git"
pkgver=1.3.7+168+g248b15c2
pkgrel=1
pkgdesc="A lightweight and highly-configurable window manager"
arch=('x86_64')
url="http://www.fluxbox.org"
license=('MIT')
depends=('libxft' 'libxpm' 'libxinerama' 'libxrandr' 'imlib2' 'fribidi')
makedepends=('git')
optdepends=('xorg-xmessage: for using the fbsetbg and fluxbox-generate_menu utilities')
provides=("$_gitname")
conflicts=("$_gitname")
options=('!makeflags')
source=("$_gitname::git://git.fluxbox.org/fluxbox.git"
        fluxbox.desktop)
sha1sums=('SKIP'
          'f3f83b8ce84d79c2f8670ef687e0dd89ab0552b8')

pkgver() {
  cd "$_gitname"
  git describe --tags | sed -e 's/Release-//' -e 's/-/+/g' -e 's/_/\./g'
}

build() {
  cd "$_gitname"
  autoreconf -fi
  ./configure --prefix=/usr \
    --enable-xft --enable-xinerama \
    --enable-imlib2 --enable-nls
  make
}

package() {
  cd "$_gitname"
  make DESTDIR="$pkgdir" install
  install -D -m644 "$srcdir/fluxbox.desktop" "$pkgdir/usr/share/xsessions/fluxbox.desktop"
  install -D -m644 COPYING "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
