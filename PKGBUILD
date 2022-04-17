# Maintainer: Brendan de la Cour <brendan.dlc@gmail.com>
pkgname=st-cour64-git
_pkgname=st
pkgver=0.8.5.1
pkgrel=1
epoch=1
pkgdesc="Brendan's simple terminal (st - from suckless)."
url="https://github.com/cour64/st"
arch=('x86_64')
license=('MIT')
options=('zipman')
depends=('libxft')
makedepends=('ncurses' 'libxext' 'git')
source=("$_pkgname::git+https://github.com/cour64/st.git")
sha1sums=('SKIP')

provides=("${_pkgname}")
conflicts=("${_pkgname}")

prepare() {
  cd "$_pkgname"
	# skip terminfo which conflicts with ncurses
	sed -i '/tic /d' Makefile
}

build() {
  cd "$_pkgname"
	make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
  cd "$_pkgname"
	make PREFIX=/usr DESTDIR="${pkgdir}" install
	install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
	install -Dm644 README "${pkgdir}/usr/share/doc/${pkgname}/README"
}
