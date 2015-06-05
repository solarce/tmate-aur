# Maintainer: huma
# thanks to adlaiff6, Invie
pkgname=tmate
pkgver=1.8.10
pkgrel=1
pkgdesc="Instant terminal sharing"
arch=('i686' 'x86_64')
license=('MIT')
url="http://tmate.io/"
makedepends=('cmake' 'libevent' 'ncurses' 'openssl' 'zlib' 'ruby')
md5sums=()

gitroot="https://github.com/nviennot/tmate.git"
gitname="tmate"
gitrev="a1c9d8784f55f5aa8f5a3ed00d997bd1217fcc9b"

build() {
  cd ${srcdir}

  if [[ -d ${gitname} ]] ; then
    cd ${gitname}
    git fetch -q
    git reset -q --hard origin/master
    git checkout -f -q ${gitrev}
  else
    git clone ${gitroot}
    cd ${gitname}
    git checkout -f -q ${gitrev}
  fi

  patch -p1 -i $srcdir/../pedantic.patch

  ./autogen.sh
  ./configure --prefix=/usr
  make
}

package() {
  cd ${pkgname}
  make DESTDIR=${pkgdir} install
}

