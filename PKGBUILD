# Maintainer: ewhal4 <ewhal4 at live dot com>

pkgname='fastcoin-qt'
pkgver=8.7.2
pkgrel=1
arch=('i686' 'x86_64')
url="http://www.fastcoin.ca/"
makedepends=('boost' 'automoc4' 'qrencode' 'miniupnpc')
license=('MIT')
pkgdesc="Peer-to-peer network based digital currency (QT)"
depends=(boost-libs qt4 miniupnpc qrencode)
conflicts=(fastcoin)
install=fastcoin-qt.install
source=("https://github.com/fastcoinproject/fastcoin/archive/fastcoin-$pkgver.tar.gz"
"$pkgname.desktop")
sha256sums=('2d3231edb8a21b251ccfd5a230ccbf25a7f4ec8fae0aee50a2ccb3e6b17a81c4'
'2d1e5de50d1946937f37217f0d318f6d2c123c1635072952fa030b8c632f3f12')

prepare() {
    tar xvfz fastcoin-$pkgver.tar.gz
}

build() {
  cd "$srcdir/fastcoin-fastcoin-$pkgver"

  # and make qt gui
  qmake-qt4 USE_QRCODE=1 USE_UPNP=1
  make
}


package() {
  install -Dm644 fastcoin-qt.desktop "$pkgdir"/usr/share/applications/fastcoin.desktop
  cd "$srcdir/fastcoin-fastcoin-$pkgver"
  install -Dm755 Fastcoin-qt "$pkgdir"/usr/bin/fastcoin-qt
  install -Dm644 share/pixmaps/bitcoin128.png "$pkgdir"/usr/share/pixmaps/fastcoin128.png

  install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}


