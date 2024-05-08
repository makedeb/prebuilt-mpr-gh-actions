# Maintainer: Hunter Wittenborn <hunter@hunterwittenborn.com>
pkgname=hugo
pkgver=0.125.7
pkgrel=1
pkgdesc="The world's fastest framework for building websites"
arch=('any')
makedepends=('git' 'golang-go>=2:1.18')
license=('Apache-2.0')
url='https://gohugo.io/'

source=("${pkgname}-${pkgver}::git+https://github.com/gohugoio/hugo/#tag=v${pkgver}")
sha256sums=('SKIP')

build() {
	cd "${pkgname}-${pkgver}/"
	CGO_ENABLED=1 go build --tags extended --trimpath

	./hugo gen man
	./hugo completion bash > "${pkgname}.bash"
}

package() {
	cd "${pkgname}-${pkgver}/"
	install -Dm 755 "./${pkgname}" "${pkgdir}/usr/bin/${pkgname}"
	install -Dm 644 man/*.1 -t "${pkgdir}/usr/share/man/man1/"
	install -Dm 644 "${pkgname}.bash" "${pkgdir}/usr/share/bash-completion/completions/${pkgname}"
}
