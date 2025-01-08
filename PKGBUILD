pkgname=bat
pkgver=0.25.0
pkgrel=1
pkgdesc='Cat clone with syntax highlighting and git integration | Bat supports syntax highlighting for a large number of programming and markup languages'
arch=('x86_64')
url='https://github.com/sharkdp/bat'
license=('APACHE' 'MIT')
makedepends=('cmake' 'rust')
depends=('curl' 'libssh2' 'oniguruma' 'libgit2')
source=(${pkgname}-${pkgver}.tar.gz::"${url}/archive/v${pkgver}.tar.gz")
sha1sums=('37a2d682fcd2e5b85062d37cf0ccbd745d0269ee')

build() {
  cargo build --locked --manifest-path $pkgname-$pkgver/Cargo.toml --release
}

#check() {
#  cargo test --locked --manifest-path $pkgname-$pkgver/Cargo.toml
#}

package() {
  export CFLAGS+=' -ffat-lto-objects -w'
  install -Dm755 $pkgname-$pkgver/target/release/$pkgname "$pkgdir/usr/bin/$pkgname"

  cd $pkgname-$pkgver/target/release/build

  # Find and package the man page (because cargo --out-dir is too new)
  find . -name bat.1 -type f -exec install -Dm644 {} \
    "$pkgdir/usr/share/man/man1/bat.1" \;

  # Find and package the bash completion file
  find . -name bat.bash -type f -exec install -Dm644 {} \
    "$pkgdir/usr/share/bash-completion/completions/bat" \;

  # Find and package the zsh completion file (not in zsh-completions yet)
  find . -name bat.zsh -type f -exec install -Dm644 {} \
    "$pkgdir/usr/share/zsh/site-functions/_bat" \;

  # Find and package the fish completion file
  find . -name bat.fish -type f -exec install -Dm644 {} \
    "$pkgdir/usr/share/fish/vendor_completions.d/bat.fish" \;


  # Package licenses
  install -Dm644 $srcdir/$pkgname-$pkgver/LICENSE-APACHE \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE-APACHE"
  install -Dm644 $srcdir/$pkgname-$pkgver/LICENSE-MIT \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE-MIT"
}
