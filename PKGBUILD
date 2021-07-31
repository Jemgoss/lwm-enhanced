# Maintainer: Jeremy Goss <jem@goss-family.net>
# Copied from: https://github.com/archlinux/svntogit-community/blob/packages/lwm/trunk/PKGBUILD
# This builds a patched version of lwm with configurable border color.

pkgname=lwm
pkgver=1.2.4
pkgrel=4
pkgdesc="A very light weight window manager (modified)"
arch=('x86_64')
url="http://www.jfc.org.uk/software/lwm.html"
license=('GPL')
#depends=('xorg-server' 'libxext' 'libsm')
depends=('libxext' 'libsm')
makedepends=('imake')
source=(http://www.jfc.org.uk/files/${pkgname}/${pkgname}-${pkgver}.tar.gz
	    enhancements.patch)
md5sums=('69fc645ded46b6801092183e01be8518'
		 'SKIP')

prepare() {
	cd "$srcdir/$pkgname-$pkgver"

	patch -i ../enhancements.patch
}

build() {
	cd "$srcdir/$pkgname-$pkgver"

	xmkmf
	sed -i 's/^LOCAL_LIBRARIES.*/& $(ICELIB)/' Makefile
	make
	strip lwm
}

package() {
	cd "$srcdir/$pkgname-$pkgver"

	install -Dm755 lwm "$pkgdir/usr/bin/lwm"
	install -Dm644 lwm.man "$pkgdir/usr/share/man/man1/lwm.1"
}
