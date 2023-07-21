# Maintainer: Hunter Wittenborn <hunter@hunterwittenborn.com>
pkgname=rustup
pkgver=1.25.2
pkgrel=3
pkgdesc='The rust toolchain installer'
arch=('any')
makedepends=('cargo')
conflicts=(
    'rustc'
    'cargo'
    'libstd-rust-dev'
    'rust-all'
    'rust-clippy'
    'rust-doc'
    'rust-gdb'
    'rust-lldb'
    'rust-src'
    'rustfmt'
)
# Since rustup can always have the latest version of the rust toolchain, we want
# this to always provide for packages under the 'rustc' package base, regardless
# of version (at least for anything that wants to require a minimum version of
# rustc, cargo, etc etc).
#
# Rust's ideology seems to be to never have a 2.0 release, so we'll cleverly use
# that here.
provides=("${conflicts[@]/%/=2.0.0}")
postinst='rustup.postinst'
license=(
    'Apache-2.0'
    'MIT'
)
url='https://rust-lang.github.io/rustup'

source=("https://github.com/rust-lang/rustup/archive/refs/tags/${pkgver}.tar.gz")
sha256sums=('SKIP')

build() {
    cd "${pkgname}-${pkgver}/"
    cargo build --release --no-default-features --features no-self-update,reqwest-backend,reqwest-rustls-tls --bin rustup-init
}

package() {
    cd "${pkgname}-${pkgver}/"
    install -Dm 755 target/release/rustup-init "${pkgdir}/usr/bin/${pkgname}"

    for bin in 'cargo' 'cargo-clippy' 'cargo-fmt' 'clippy-driver' 'rustc' 'rustdoc' 'rustfmt' 'rust-gdb' 'rust-gdbgui' 'rust-lldb'; do
        ln -s "/usr/bin/${pkgname}" "${pkgdir}/usr/bin/${bin}"
    done

    "${pkgdir}/usr/bin/${pkgname}" completions bash | install -Dm 644 /dev/stdin "${pkgdir}/usr/share/bash-completion/completions/${pkgname}"
    "${pkgdir}/usr/bin/${pkgname}" completions bash cargo | install -Dm 644 /dev/stdin "${pkgdir}/usr/share/bash-completion/completions/cargo"

}

# vim: set sw=4 expandtab:
