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
sha256sums=('5bf480fe75078a562b3343e4872fa4215eb081fca7ecce9dc7547eaa5c881e5b')

prepare() {
    if [[ -f ../config.h ]]; then
	echo "Found custom config.h in $(readlink -f ../), copying..."
        cp -v ../config.h "${_pkgname}-${pkgver}/config.h"
    fi
}

build() {
    cd "${_pkgname}-${pkgver}"
    make
}

package() {
    cd "${_pkgname}-${pkgver}"

    make PREFIX=/usr DESTDIR="${pkgdir}" install
    install -Dm0644 LICENSE "${pkgdir}/usr/share/licenses/${_pkgname}/LICENSE"
}
