# Maintainer: Hunter Wittenborn <hunter@hunterwittenborn.com>
pkgname=golang-go
pkgver=1.22.4
pkgrel=1
epoch=2
pkgdesc='The Go programming language'
arch=('any')
optdepends=('r!g++' 'r!gcc' 'r!libc6-dev' 'r!pkg-config')
makedepends=('gcc' 'golang-go')
url='https://go.dev'
extensions=()
preinst='./preinst'

source=("${url}/dl/go${pkgver}.src.tar.gz")
sha256sums=('SKIP')

build() {
    cd go/src
    GOROOT_FINAL='/usr/lib/go' ./make.bash
}

package() {
    cd go/
    
    # Create needed directories.
    install -d "${pkgdir}/usr/bin/" "${pkgdir}/usr/lib/go"
    
    # Go library.
    cp ./ "${pkgdir}/usr/lib/go/" -R

    # Go binaries.
    ln -s /usr/lib/go/bin/go "${pkgdir}/usr/bin/go"
    ln -s /usr/lib/go/bin/gofmt "${pkgdir}/usr/bin/gofmt"
}

# vim: set ts=4 sw=4 expandtab:
