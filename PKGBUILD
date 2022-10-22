_pkgname=surf
pkgname=${_pkgname}-ditc
pkgver=2.1
pkgrel=1
pkgdesc='A simple web browser based on WebKit/GTK+. Patched by DemonInTheCloset'
arch=('x86_64')
url='https://surf.suckless.org/'
license=('MIT')
depends=('webkit2gtk' 'gcr' 'xorg-xprop')
optdepends=('dmenu: URL-bar'
            'ca-certificates: SSL verification'
            'xterm: default download handler'
            'curl: default download handler'
            'tabbed: tabbed frontend')
makedepends=()
source=("https://github.com/DemonInTheCloset/surf/archive/refs/tags/${pkgver}-patched.tar.gz")
sha256sums=('a1e666b36f5d0dc9ebb9134ebf1fcc4b5d8704170c87eb59fb3893c965f90095')

prepare() {
    if [[ -f ../config.h ]]; then
	echo "Found custom config.h in $(readlink -f ../), copying..."
        cp -v ../config.h "${_pkgname}-${pkgver}/config.h"
    fi
}

build() {
    cd "${_pkgname}-${pkgver}-patched"
    patch -p1 < patches/0000-All-Patches.patch
    make
}

package() {
    cd "${_pkgname}-${pkgver}-patched"

    make PREFIX=/usr DESTDIR="${pkgdir}" install
    install -Dm0644 LICENSE "${pkgdir}/usr/share/licenses/${_pkgname}/LICENSE"
}
