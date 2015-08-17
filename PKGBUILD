# Maintainer: Florian Léger <florian6 dot leger at laposte dot net>

pkgbase=nwn-nwmouse
pkgname=nwn-nwmouse
arch=("i686" "x86_64")
pkgdesc="Hardware mouse cursors for Neverwinter Nights."
pkgver=3.1
pkgrel=2
license=("custom")
url="http://home.roadrunner.com/~nwmovies/nwmouse/"
depends=("nwn" "elfutils" "libxcursor" "sdl")
makedepends=("perl")
[ "x$CARCH" = "xx86_64" ] && pkgname="lib32-nwn-nwmouse"
[ "x$CARCH" = "xx86_64" ] && depends=("nwn" "lib32-elfutils" "lib32-libxcursor" "lib32-sdl")
[ "x$CARCH" = "xx86_64" ] && makedepends+=("gcc-multilib" "elfutils" "libxcursor" "sdl")
[ "x$CARCH" = "xx86_64" ] && provides=("nwn-nwmouse")
[ "x$CARCH" = "xx86_64" ] && conflicts=("nwn-nwmouse")
source=("http://home.roadrunner.com/~nwmovies/nwmouse/nwmouse-v2-public.20090906.183839.tar.gz"
        "80-nwmouse.conf"
        "20-nwmouse.sh")
md5sums=('02bf7f5610c928a5910d1cab4bf3f87a'
         '7cc58b40ef7e2d32291c5a68f3178c9f'
         'd898af5d4ebf686ea75ddb2f8c59fa81')

build() {
  cd "${srcdir}"
  ./nwmouse_install.pl
}

package() {
  install -Dm644 "nwmouse/nwmouse.so" "${pkgdir}/opt/nwn/nwmouse/nwmouse/nwmouse.so"
  install -Dm644 "nwmouse/libdis/libdisasm.so" "${pkgdir}/opt/nwn/nwmouse/nwmouse/libdis/libdisasm.so"
  install -Dm644 "nwmouse/nwmouse.README.txt" "${pkgdir}/usr/share/licenses/${pkgname}/readme.txt"
  cp -r "nwmouse/cursors" "${pkgdir}/opt/nwn/nwmouse/nwmouse/"
  install -Dm644 "80-nwmouse.conf" "${pkgdir}/etc/nwn/branches.d/80-nwmouse.conf"
  install -Dm644 "20-nwmouse.sh" "${pkgdir}/etc/nwn/hooks.d/20-nwmouse.sh"
}
