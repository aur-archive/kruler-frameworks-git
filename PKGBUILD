# Maintainer: Gustavo Alvarez <sl1pkn07@gmail.com>

pkgname=kruler-frameworks-git
pkgver=r493.ad4c287
pkgrel=1
pkgdesc="A pixel measuring tool for KDE. KF5 Frameworks branch. (GIT version)"
url="https://www.kde.org/applications/graphics/kruler"
arch=('i686' 'x86_64')
license=('GPL' 'LGPL' 'FDL')
depends=('kxmlgui' 'knotifications' 'desktop-file-utils')
makedepends=('extra-cmake-modules' 'kdoctools' 'git')
conflicts=('kdegraphics-kruler' 'kruler')
provides=('kruler')
source=("git://anongit.kde.org/kruler.git#branch=frameworks")
sha1sums=('SKIP')
install="kruler-frameworks-git.install"
_gitname=kruler

pkgver() {
  cd "${_gitname}"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
  rm -fr build
  mkdir -p build
}

build() {
  cd build

  cmake "../${_gitname}" \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DLIB_INSTALL_DIR=lib \
    -DKDE_INSTALL_USE_QT_SYS_PATHS=ON
  make
}

package() {
  make -C build DESTDIR="${pkgdir}" install
}
