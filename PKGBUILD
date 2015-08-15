# Maintainer: Bruno Nova <brunomb.nova@gmail.com>
pkgname=drmips-nodoc
_pkgname=drmips
pkgver=1.2.2
pkgrel=1
pkgdesc="Graphical MIPS simulator to support computer architecture teaching and learning - This package doesn't include the documentation"
arch=('any')
url="https://bitbucket.org/brunonova/drmips"
license=('GPL3')
depends=('java-environment' 'desktop-file-utils' 'hicolor-icon-theme')
makedepends=('jdk7-openjdk' 'cmake')
conflicts=('drmips')
install="$pkgname.install"
source=("https://bitbucket.org/brunonova/$_pkgname/downloads/DrMIPS_v$pkgver.tar.gz"
        "https://bitbucket.org/brunonova/$_pkgname/raw/v$pkgver/debian/$_pkgname.desktop"
        "https://bitbucket.org/brunonova/$_pkgname/raw/v$pkgver/debian/$_pkgname.1"
        "https://bitbucket.org/brunonova/$_pkgname/raw/v$pkgver/debian/$_pkgname.pt.1")
md5sums=('499bc462d6b9aa3367fd7d41fa2bdd24'
         '02ba7efa585b621e978f6a23e8fd210e'
         '4910bafb9087b68ed9fa40bfd46838c5'
         '70954b479c35eeaff5f9306d0ec5eff9')

build() {
	cd "$srcdir"
	cmake . -DCMAKE_INSTALL_PREFIX=/usr -DDRMIPS_BUILD_MANUALS=off
	make
}

package() {
	cd "$srcdir"
	make DESTDIR="$pkgdir" install
	for _size in 16 24 32 48 64 96 128 256 512; do
		install -Dm644 "src/pc/DrMIPS/src/res/icons/x$_size/$_pkgname.png" "$pkgdir/usr/share/icons/hicolor/${_size}x${_size}/apps/$_pkgname.png"
	done
	install -Dm644 "$_pkgname.desktop" "$pkgdir/usr/share/applications/$_pkgname.desktop"
	install -Dm644 "$_pkgname.1" "$pkgdir/usr/share/man/man1/$_pkgname.1"
	install -Dm644 "$_pkgname.pt.1" "$pkgdir/usr/share/man/pt/man1/$_pkgname.1"
}
