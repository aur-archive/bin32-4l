# Contributor: ugaciaka <ugaciaka@gmail.com>
# Thank's Imanol Celaya <ilcra1989@gmail.com> for arch x86
# Florian Bäuerle <florian.bae@gmail.com>

pkgname=bin32-4l
pkgver=1.0r6
_realname=4L-1.0-r6
pkgrel=7
pkgdesc="4L: LaCie LightScribe Labeler for Linux"
arch=('x86_64')
url="http://www.lacie.com/products/product.htm?pid=10803"
license=('unknown')
install=4l.install
depends=('lib32-fontconfig' 'lib32-gcc-libs' 'lib32-libxcursor' 'lib32-libxi' 'lib32-libxinerama' 'lib32-libxrandr' 'bin32-lightscribe')
makedepends=('rpmextract')
conflicts=('4l_x86_64')
source=(http://www.lacie.com/download/drivers/$_realname.i586.rpm lightscribe.png lightscribe.desktop)
md5sums=('11fc8b2daeaed2b61a567056413bdefd'
	 '582b6cce827c8909115a31c7bc10d6ce' 
	 '48d1af9e30a21f6ec1f8c85151b3a652')

build() {
  echo "startdir: $startdir, pkgdir: $pkgdir"
  cd $startdir/src
  rpmextract.sh 4L-1.0-r6.i586.rpm 2> /dev/null
  mkdir -p $startdir/pkg/{opt,usr/bin}
  cp -R usr/4L $startdir/pkg/opt
  cd $startdir/pkg/usr/bin
  ln -s ../../opt/4L/4L-cli 4L-cli
  ln -s ../../opt/4L/4L-gui 4L-gui
  find $startdir/pkg/opt -type d -exec chmod 755 {} \;
  chmod -x $startdir/pkg/opt/4L/*/*
  chmod +s $startdir/pkg/opt/4L/4L-cli
  install -D -m644 ${startdir}/lightscribe.png ${pkgdir}/usr/share/pixmaps/lightscribe.png
  install -D -m644 ${startdir}/lightscribe.desktop ${pkgdir}/usr/share/applications/lightscribe.desktop
  mv $startdir/pkg/opt $pkgdir
  mv $startdir/pkg/usr/bin $pkgdir/usr
}
