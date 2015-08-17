# Maintainer: kfgz <kfgz at interia pl>
# Contributor: scj <scj(at)archlinux(dot)us>

pkgname=syasokoban
pkgver=2.0.1
pkgrel=3
pkgdesc="Still Yet Another implementation of the puzzle game Sokoban"
arch=('i686' 'x86_64')
url="http://grayskygames.com/sokoban.html"
license=('GPL')
depends=('sdl')
options=(!makeflags)
source=(http://grayskygames.com/sokoban/${pkgname}-${pkgver}.tar.gz
        fix_path.patch
        fix_chdir.patch
        ${pkgname}.desktop)
md5sums=('3735ea7f164587165d4d03805a87b1a5'
         '9804a24b30d718c60396706e09321365'
         '40b5be9087468833c476fcf9cf0c7e36'
         '11465cf53141238888d1cdc0e725599e')

build() {
  cd "${srcdir}"/${pkgname}-${pkgver}
  patch -p1 < ../fix_path.patch
  patch -p1 < ../fix_chdir.patch
  make
}

package() {
  cd "${srcdir}"/${pkgname}-${pkgver}
  mkdir -p "${pkgdir}"/usr/bin "${pkgdir}"/usr/share/syasokoban
  cp syasokoban "${pkgdir}"/usr/bin/syasokoban
  cp -r data/* "${pkgdir}"/usr/share/syasokoban/
  find "${pkgdir}" -perm 544 -exec chmod 644 {} \;
  find "${pkgdir}" -perm 744 -exec chmod 644 {} \;
  install -Dm644 "${srcdir}"/${pkgname}.desktop \
                 "${pkgdir}"/usr/share/applications/${pkgname}.desktop
}
