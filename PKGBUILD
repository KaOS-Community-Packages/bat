pkgname=bat
pkgver=0.16.0
pkgrel=1
arch=('x86_64')
pkgdesc='A cat(1) clone with wings (binary release).'
url='https://github.com/sharkdp/bat'
license=('APACHE' 'MIT')
makedepends=('cmake' 'rust')
depends=('curl' 'libssh2' 'oniguruma')
source=(${pkgname}-${pkgver}.tar.gz::"${url}/archive/v${pkgver}.tar.gz")
sha1sums=('9689bc8bee44593927e95a6176805d01d2697734')

build() {
	cd "${pkgname}-${pkgver}"

	cargo build --release
}

package() {
	cd "${pkgname}-${pkgver}"

	install -Dm755 "target/release/${pkgname}" "${pkgdir}/usr/bin/${pkgname}"
	install -Dm644 "assets/manual/bat.1.in" "${pkgdir}/usr/share/man/man1/${pkgname}.1"

	# Completion files
	#install -Dm644 "assets/completions/bat.bash.in" \
	#	"${pkgdir}/usr/share/bash-completion/completions/${pkgname}"
	install -Dm644 "assets/completions/bat.fish.in" \
		"${pkgdir}/usr/share/fish/vendor_completions.d/${pkgname}.fish"
	install -Dm644 "assets/completions/bat.zsh.in" \
		"${pkgdir}/usr/share/zsh/site-functions/_${pkgname}"

	# Licenses
	install -Dm644 LICENSE-APACHE "${pkgdir}/usr/share/licenses/${pkgname}/APACHE"
	install -Dm644 LICENSE-MIT "${pkgdir}/usr/share/licenses/${pkgname}/MIT"
}
