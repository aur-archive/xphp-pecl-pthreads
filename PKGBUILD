# Maintainer: Andrew Rose <hello@andrewrose.co.uk>
# Contributor: Andrew Rose <hello@andrewrose.co.uk>

pkgname=xphp-pecl-pthreads
pkgdesc='Threading API'
pkgver=2.0.10
pkgrel=1

arch=('x86_64' 'i686')
license=('PHP')
url='http://pecl.php.net/package/pthreads'

makedepends=('xphp')
source=("http://pecl.php.net/get/pthreads-${pkgver}.tgz")
md5sums=('6a753b418f9dd0953c77d3b90af48b5f')
depends=('xphp')

peclconfig="--prefix=/opt/xphp \
 --bindir=/opt/xphp/bin \
 --libdir=/opt/xphp/lib \
 --sysconfdir=/etc/xphp \
 --mandir=/opt/xphp/man \
 --with-php-config=/opt/xphp/bin/php-config
"

build() {

	export PATH="/opt/xphp/bin:$PATH"

	cd ${srcdir}/pthreads-${pkgver} || return 1
	/opt/xphp/bin/phpize || return 1
	./configure ${peclconfig} --enable-pthreads --enable-maintainer-zts || return 1
	make || return 1
}

package_xphp-pecl-pthreads() {

	install -d -m755 ${pkgdir}/opt/xphp/lib/modules/
	cp ${srcdir}/pthreads-${pkgver}/modules/pthreads.so ${pkgdir}/opt/xphp/lib/modules/pthreads.so
	install -D -m 644 $startdir/pthreads.ini ${pkgdir}/etc/xphp/conf.d/pthreads.ini || return 1
}
