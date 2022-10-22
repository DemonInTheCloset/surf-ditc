pkgname=surf-ditc
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
install='surf.install'
source=("https://github.com/DemonInTheCloset/surf/archive/refs/tags/${pkgver}.tar.gz")
sha256sums=('')

prepare() {
    if [[ -f ../config.h ]]; then
	echo "Found custom config.h in $(readlink -f ../), copying..."
        cp -v ../config.h "${pkgname}-${pkgver}/config.h"
    fi
}

build() {
    cd "${pkgname}-${pkgver}"
    make
}

package() {
    cd "${pkgname}-${pkgver}"

    make PREFIX=/usr DESTDIR="${pkgdir}" install
    install -Dm0644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
