# Maintainer: Abdullah Cunuk <abdullahcunuk@hotmail.com>
pkgname="eta-touchdrv-git"
pkgver="0.2.0"
pkgrel="1"
pkgdesc="Touchscreen driver for Vestel 14MB24A (IRTOUCH)"
arch=("any")
url="https://github.com/abdullah-rgb/eta-touchdrv"
license=("custom")
depends=(dkms usbutils systemd)
makedepends=(git)
checkdepends=(dkms usbutils systemd)
optdepends=('touchegg: Touchscreen configuraton'
            'touche: Touchscreen configuraton tool')

prepare() {
	git clone "${url}"
}

build() {
	cd "$srcdir/eta-touchdrv/usr/src/eta-touchdrv/touch2"
	sudo make
	cd ../touch4
	sudo make
	cd ../
	sudo dkms install .
}

package() {
	# binary files
	$(install -Dm755 $srcdir/eta-touchdrv/usr/bin/* -t $pkgdir/usr/bin/)
	
	# lib files
	$(install -Dm644 $srcdir/eta-touchdrv/usr/lib/systemd/system/* -t $pkgdir/usr/lib/systemd/system/)
	$(install -Dm644 $srcdir/eta-touchdrv/usr/lib/udev/rules.d/* -t $pkgdir/usr/lib/udev/rules.d/)
	
	# src files
	$(install -Dm644 $srcdir/eta-touchdrv/usr/src/eta-touchdrv/touch2/* -t $pkgdir/usr/src/eta-touchdrv/touch2/)
	$(install -Dm644 $srcdir/eta-touchdrv/usr/src/eta-touchdrv/touch4/* -t $pkgdir/usr/src/eta-touchdrv/touch4/)
	$(install -Dm644 $srcdir/eta-touchdrv/usr/src/eta-touchdrv/dkms.conf -t $pkgdir/usr/src/eta-touchdrv/)
	$(install -Dm644 $srcdir/eta-touchdrv/usr/src/eta-touchdrv/version -t $pkgdir/usr/src/eta-touchdrv/)
	
	# share/doc files
	$(install -Dm644 $srcdir/eta-touchdrv/usr/share/doc/eta-touchdrv/* -t $pkgdir/usr/share/doc/eta-touchdrv/)
	$(install -Dm644 $srcdir/eta-touchdrv/usr/share/lintian/overrides/* -t $pkgdir/usr/share/lintian/overrides/)
}
