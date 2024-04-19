# Maintainer: Hunter Wittenborn <hunter@hunterwittenborn.com>
pkgname=fd
pkgver=9.0.0
pkgrel=1
pkgdesc="A simple, fast and user-friendly alternative to 'find'"
arch=('any')
makedepends=('rustc>=1.56.0' 'cargo')
conflicts=('fdclone')
license=('Apache-2.0' 'MIT')
url='https://github.com/sharkdp/fd'

source=("${pkgname}-${pkgver}::git+${url}/#tag=v${pkgver}")
sha256sums=('SKIP')

build() {
    cd "${pkgname}-${pkgver}/"
    cargo build --release --all-features
}

package() {
    cd "${pkgname}-${pkgver}/"
    install -Dm 755 target/release/fd "${pkgdir}/usr/bin/fd"
    install -Dm 644 doc/fd.1 "${pkgdir}/usr/share/man/man1/fd.1"
    find target/release/build -name 'fd.bash' -exec install -Dm 644 '{}' "${pkgdir}/usr/share/bash-completion/completions/fd" \;
}

# vim: set sw=4 expandtab:
