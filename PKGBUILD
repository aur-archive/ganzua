# Contributor: David Watzke <david@watzke.cz>

pkgname=ganzua
pkgver=1.01
pkgrel=2
pkgdesc="A cryptanalysis tool for classical ciphers"
url="http://ganzua.sourceforge.net/"
arch=('i686' 'x86_64')
license=('GPL-2')
depends=('apache-ant')
#provides=()
#conflicts=()
source=('http://heanet.dl.sourceforge.net/sourceforge/ganzua/Ganz_a/1.01/ganzua-1.01-src.tar.gz')
md5sums=('f48e9011318fd8ce4b83991f8ddced61')

build() {
	cd "$srcdir/$pkgname-$pkgver"
	/usr/bin/ant
}

package() {
	cd "$srcdir/$pkgname-$pkgver"

	install -D -m 0644 "$pkgname.jar" "$pkgdir/usr/share/java/$pkgname/$pkgname.jar"
	install -D -m 0644 "langFreq.jar" "$pkgdir/usr/share/java/$pkgname/langFreq.jar"

	install -d "$pkgdir/usr/bin"

	printf "#!/bin/bash\njava -jar /usr/share/java/$pkgname/$pkgname.jar \"\$@\"\n" > "$pkgdir/usr/bin/$pkgname"
	chmod 0755 "$pkgdir/usr/bin/$pkgname"

	printf "#!/bin/bash\njava -jar /usr/share/java/$pkgname/langFreq.jar \"\$@\"\n" > "$pkgdir/usr/bin/$pkgname-langFreq"
	chmod 0755 "$pkgdir/usr/bin/$pkgname-langFreq"
}
