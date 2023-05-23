# Maintainer: Hunter Wittenborn <hunter@hunterwittenborn.com>
pkgname=glab
pkgver=1.30.0
pkgrel=1
pkgdesc='A GitLab CLI tool bringing GitLab to your command line'
arch=('any')
makedepends=('golang-go>=2:1.13')
license=('MIT')
url='https://gitlab.com/gitlab-org/cli'

source=("${pkgname}-${pkgver}::git+${url}/#tag=v${pkgver}")
sha256sums=('SKIP')

build() {
    cd "${pkgname}-${pkgver}/"
    make
}

package() {
    cd "${pkgname}-${pkgver}/"
    install -Dm 755 "bin/${pkgname}" "${pkgdir}/usr/bin/${pkgname}"
    "bin/${pkgname}" completion -s bash | install -Dm 644 /dev/stdin "${pkgdir}/usr/share/bash-completion/completions/${pkgname}"
}

# vim: set sw=4 expandtab:
