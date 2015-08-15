pkgname=coinor-bcp
pkgver=1.3.8
pkgrel=1
pkgdesc="COIN-OR parallel branch-cut-price algorithms for mixed-integer linear programs"
arch=('i686' 'x86_64')
url="https://projects.coin-or.org/Bcp"
license=('EPL')
groups=('coinor')
depends=('coinor-cgl' 'coinor-clp')
source=("http://www.coin-or.org/download/source/Bcp/Bcp-${pkgver}.tgz")
sha1sums=('192112b530e13aacb3b4186fff63eb57464cd3eb')

build() {
  cd "$srcdir/Bcp-$pkgver"
  COIN_SKIP_PROJECTS="Sample" \
  ./configure --prefix=/usr \
              --with-osi-lib="$(pkg-config --libs osi)" \
              --with-osi-incdir="/usr/include/coin/" \
              --with-clp-lib="$(pkg-config --libs clp)" \
              --with-clp-incdir="/usr/include/coin/" \
              --with-cgl-lib="$(pkg-config --libs cgl)" \
              --with-cgl-incdir="/usr/include/coin/" \
              --with-vol-lib="$(pkg-config --libs vol)" \
              --with-vol-incdir="/usr/include/coin/" \
              --with-coinutils-lib="$(pkg-config --libs coinutils)" \
              --with-coinutils-incdir="/usr/include/coin/" -C
  make
}

package() {
  cd "$srcdir/Bcp-$pkgver/Bcp"
  PKG_CONFIG_LIBDIR="${pkgdir}/usr/lib/pkgconfig/" \
  make DESTDIR="$pkgdir/" install
}
