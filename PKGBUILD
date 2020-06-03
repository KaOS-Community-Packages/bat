pkgname=bat
pkgver=0.15.4
pkgrel=1
arch=('x86_64')
pkgdesc='A cat(1) clone with wings (binary release).'
url='https://github.com/sharkdp/bat'
license=('APACHE', 'custom:MIT')
source=("https://github.com/sharkdp/bat/releases/download/v${pkgver}/${pkgname}-v${pkgver}-x86_64-unknown-linux-gnu.tar.gz")
sha1sums=('2cda9c9e8a891ed65a014d919d8db2f6bce806e3')

package() {
  cd "${srcdir}/${pkgname}-v${pkgver}-x86_64-unknown-linux-gnu"
  install -Dm755 ${pkgname} "${pkgdir}/usr/bin/bat"
  install -Dm644 autocomplete/${pkgname}.fish "${pkgdir}/usr/share/fish/vendor_completions.d/${pkgname}.fish"
  install -Dm644 LICENSE-MIT "${pkgdir}/usr/share/licenses/$pkgname/LICENSE-MIT"
  install -Dm644 ${pkgname}.1 "${pkgdir}/usr/share/man/man1/${pkgname}.1"
}
