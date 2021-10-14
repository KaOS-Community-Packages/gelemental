pkgname=gelemental
pkgver=2.0.1
pkgrel=1
pkgdesc="gElemental is a periodic table viewer that provides detailed information on the chemical elements"
arch=('x86_64')
url="https://github.com/ginggs/gelemental"
license=('GPL')
depends=('gtkmm' 'gdk-pixbuf2')
makedepends=('gawk' 'make' 'gettext' 'libtool' 'pkg-config' 'intltool' 'perl>=5.8.1')
makeoptdepends=('doxygen')
source=(${pkgname}-${pkgver}.tar.gz::https://github.com/ginggs/${pkgname}/archive/v${pkgver}.tar.gz)
md5sums=('3a44c8ff878ec3436343299608a31a26')

build() {
  cd ${srcdir}/${pkgname}-${pkgver}
  ./configure --prefix=/usr
  make || return 1
}

package() {
  cd ${srcdir}/${pkgname}-${pkgver}
  make DESTDIR=${pkgdir} install

  install -dpm755 "${pkgdir}/usr/share/licenses/${pkgname}/"
  install -Dpm644 COPYING COPYING.DATA  "${pkgdir}/usr/share/licenses/${pkgname}/"

  install -dpm755 "${pkgdir}/usr/share/doc/${pkgname}/"
  install -Dpm644 AUTHORS ChangeLog INSTALL NEWS* README TODO TRANSLATORS "${pkgdir}/usr/share/doc/${pkgname}/"
}
