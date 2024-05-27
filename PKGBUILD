# Maintainer: Hunter Wittenborn <hunter@hunterwittenborn.com>
pkgname=toast
pkgver=0.45.5
pkgrel=1
pkgdesc='Containerize your development and continuous integration environments'
arch=('any')
depends=('docker.io>=17.06.0')
makedepends=('cargo')
url='https://github.com/stepchowfun/toast'

source=("${pkgname}-${pkgver}::git+${url}/#tag=v${pkgver}")
sha256sums=('SKIP')

build() {
    cd "${pkgname}-${pkgver}/"
    cargo build --release
}

package() {
    install -Dm 755 "${pkgname}-${pkgver}/target/release/toast" "${pkgdir}/usr/bin/toast"
}

# vim: set sw=4 expandtab:
