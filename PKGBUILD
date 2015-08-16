# Maintainer: 謝致邦 <Yeking@Red54.com>

pkgname=mali-libs
pkgver=20130220
pkgrel=1
pkgdesc="Mali implementation of OpenGL ES, OpenVG and EGL"
arch=('armv7h')
url="http://github.com/linux-sunxi/mali-libs"
license=('custom')
depends=('libump')
makedepends=('git')
provides=('khrplatform-devel' 'libegl' 'libgles' 'mali400')
conflicts=('khrplatform-devel' 'libegl' 'libgles' 'mali400')
replaces=('khrplatform-devel' 'libegl' 'libgles' 'mali400')

build() {
	cd $srcdir
	if [[ -d $pkgname ]]; then
		cd $pkgname && git pull origin
	else
		git clone $url --depth 1
	fi
	rm -rf $srcdir/build
	cp -r $srcdir/$pkgname $srcdir/build
}

package() {
	cd $srcdir/build
	mkdir -p $pkgdir/usr/{include,lib}
	make headers prefix=$pkgdir/usr
	make VERSION=r3p0 ABI=armhf x11 prefix=$pkgdir/usr/
}
