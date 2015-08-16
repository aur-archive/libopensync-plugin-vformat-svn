# Maintainer: Samuele Disegna <smldis@gmail.com>

pkgname=libopensync-plugin-vformat-svn
pkgver=5558
pkgrel=1
pkgdesc="vformat format plugin for OpenSync"
arch=('i686' 'x86_64')
url="http://www.opensync.org"
license=('LGPL2')
depends=('libopensync-svn')
makedepends=('subversion' 'cmake')
provides=('libopensync-plugin-vformat')
conflicts=('libopensync-plugin-vformat')
source=()
md5sums=()

_svnmod="libopensync-plugin-vformat"
_svntrunk="http://svn.opensync.org/format-plugins/vformat/"

build() {
  cd $startdir/src
  msg "Connecting to $_svntrunk...."
  svn co $_svntrunk $_svnmod -r $pkgver 

  [ -d ./$_svnmod-build ] && rm -fr ./$_svnmod-build
  cp -r ./$_svnmod ./$_svnmod-build
  cd ./$_svnmod-build
  
  msg "SVN checkout done or server timeout"
  msg "Starting cmake..."

  mkdir build
  cd build
  cmake .. -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr || return 1
  make || return 1
  make DESTDIR=$pkgdir install || return 1

  rm  -rf  $startdir/src/$_svnmod-build
}
 
