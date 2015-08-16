# Contributor: Andrea Scarpino <andrea@archlinux.org>
# Contributor: Pierre Schmitz <pierre@archlinux.de>

pkgname=kcoloredit
pkgver=2.0.0
_kdever=4.4.0
pkgrel=7
pkgdesc="A usefull tool that makes more easy and fun edit and create color"
arch=('i686' 'x86_64')
url='http://extragear.kde.org/apps/kcoloredit/'
license=('GPL')
depends=('kdebase-runtime')
makedepends=('pkgconfig' 'cmake' 'automoc4')
options=('docs')
install=${pkgname}.install
source=("http://download.kde.org/stable/extragear/${pkgname}-${pkgver}-kde${_kdever}.tar.bz2"
        kcoloredit-2.0.0-underlinking.patch
       )

build() {
  cd "$srcdir/${pkgname}-${pkgver}-kde${_kdever}"
  patch -p1 -i ../kcoloredit-2.0.0-underlinking.patch
  cd $srcdir
  mkdir build
  cd build
  cmake ../${pkgname}-${pkgver}-kde${_kdever} \
    -DCMAKE_BUILD_TYPE=Release \
    -DQT_QMAKE_EXECUTABLE=qmake-qt4 \
    -DCMAKE_INSTALL_PREFIX=/usr
  make
}

package() {
  cd ${srcdir}/build
  make DESTDIR=$pkgdir install
}
md5sums=('c28d476835caefc3736bcac912554cb5'
         '13db3b1ac05fed4aa9158c4c24afb8de')
