# Maintainer: AnClark Liu <clarklaw4701@gmail.com>

pkgname="mingw-w64-x86_64-lv2"
pkgver=1.18.2
pkgrel=4
pkgdesc="An extensible open standard for audio plugins"
arch=('x86_64')
url="https://lv2plug.in/"
license=('custom:ISC')
makedepends=('mingw-w64-x86_64-python' 'mingw-w64-x86_64-waf' 'mingw-w64-x86_64-gcc' 'make')
source=(http://lv2plug.in/spec/lv2-${pkgver}.tar.bz2)
sha256sums=('SKIP')

# Workaround: Add drive root (C:\) to force WAF installing files into the real Msys root.
#   For example, Msys is installed in C:\msys64\.
#   If you simply use prefix "/mingw64/", all files will be installed into C:\msys64\msys64\.
MINGW_PREFIX=C:/mingw64/
MINGW_GCC=/mingw64/bin/gcc.exe
MINGW_GXX=/mingw64/bin/g++.exe
LV2_BUNDLE_DIR=C:/opt/LV2/

build() {
  cd ${srcdir}/lv2-${pkgver}

  CC=${MINGW_GCC} CXX=${MINGW_GXX} \
  python waf configure \
    --prefix=${MINGW_PREFIX} \
    --lv2dir=${LV2_BUNDLE_DIR}
  python waf build $MAKEFLAGS
}

package() {
  cd ${srcdir}/lv2-${pkgver}

  python waf install --destdir="${pkgdir}"
}

post_install() {
  echo "=========================================================="
  echo "  LV2 Bundle is installed under Msys2's /opt/LV2."
  echo "  You may need to copy them manually into: "
  echo ""
  echo "    C:\Program Files\Common Files\LV2"
  echo ""
  echo "  Then check your DAW's searching path."
  echo "=========================================================="
}
