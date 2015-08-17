# Author: Enverex <ben@xnode.org>

pkgname=uade-git
pkgver=20130205
pkgrel=1
pkgdesc="Unix Amiga Delitracker Emulator"
arch=('i686' 'x86_64')
url="http://zakalwe.fi/uade"
license=('GPL')
depends=('libao')
makedepends=('pkgconfig' 'git' 'bencode-tools-git')
conflict=('uade')
provides=('uade')
install=uade.install

_gitroot="git://zakalwe.fi/uade"
_gitname="uade"

build() {
  cd "${srcdir}"
  msg "Connecting to GIT server...."

  if [ -d ${_gitname} ] ; then
    cd ${_gitname} && git pull origin
    msg "Local files updated."
  else
    git clone ${_gitroot} ${_gitname}
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting make..."

  cd "${srcdir}/${_gitname}"
  ./configure --prefix="/usr/" --package-prefix="${pkgdir}"
  make uadecore uade123
}

package() {
  cd "${srcdir}/${_gitname}"
  make install
}

