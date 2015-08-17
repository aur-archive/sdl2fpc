pkgname=sdl2fpc
pkgver=1.14
pkgrel=1
pkgdesc="Complete SDL 2 headers translation for Free Pascal Compiler"
url="https://bitbucket.org/p_daniel/sdl-2-for-free-pascal-compiler"
license=("zlib")
arch=(i686 x86_64)
makedepends=(fpc dos2unix)
depends=(sdl2)
source=("http://downloads.sourceforge.net/sdl2fpc/SDL2_for_FPC_$pkgver-src.zip")
sha1sums=('da5b4df4cb6925e615392d603ee34c6d0bd45465')
_unittgt=`fpc -iSP`-`fpc -iSO`
_fpcver=`fpc -iV`

prepare() {
	find "$srcdir" -type f -exec dos2unix {} \;
}

build() {
  find "$srcdir" -name '*.pas' -exec fpc -O3 -Xs -XX {} \;
}

package() {
  cd "${srcdir}/SDL2"
  find . -name '*.o' -o -name '*.ppu' -o -name '*.rst' -o -name '*.a'|
    xargs -rtl1 -I {} install -Dm644 {} "$pkgdir/usr/lib/fpc/$_fpcver/units/$_unittgt/sdl2/"{}
}
