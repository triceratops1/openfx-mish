# Maintainer: Hugo Courtial <hugo [at] courtial [not colon] me>
# Maintainer: Luca Weiss <luca (at) z3ntu (dot) xyz>

pkgname=openfx-misc
pkgver=2.2.0
pkgrel=1
arch=("i686" "x86_64")
pkgdesc="Miscellaneous OpenFX plugins"
url="https://github.com/devernay/openfx-misc"
license=("GPL2")
makedepends=("git")
depends=("libgl")
depends_x86_64=("gcc-libs-multilib")
source=("$pkgname::git+https://github.com/devernay/openfx-misc.git#tag=Natron-$pkgver"
        )
sha512sums=('SKIP'
            )

_bits=32 ; [[ "$CARCH" = 'x86_64' ]] && _bits=64

prepare() {
  cd "$srcdir/$pkgname"
  git submodule update --recursive
}

build() {
  cd "$srcdir/$pkgname"
  make CONFIG=release BITS=$_bits
}

package() {
  cd "$srcdir/$pkgname"
  mkdir -p "$pkgdir/usr/OFX/Plugins"
  make install PLUGINPATH=$pkgdir/usr/OFX/Plugins CONFIG=release BITS=$_bits
}
