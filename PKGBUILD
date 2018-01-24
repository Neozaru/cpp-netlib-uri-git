# Maintainer: Jitang Zheng <jitang.zheng@gmail.com>

pkgname=cpp-netlib-uri-git
pkgver=70f233c
pkgrel=1
pkgdesc='cpp-netlib URI'
arch=(i686 x86_64)
url='https://github.com/Neozaru/cpp-netlib-uri'
license=(BOOST)
conflicts=(cpp-netlib-uri)
provides=(cpp-netlib-uri)
replaces=(cpp-netlib-uri)
depends=()
makedepends=(git cmake clang)
source=(git+https://github.com/Neozaru/cpp-netlib-uri.git)
md5sums=(SKIP)

pkgver() {
  cd cpp-netlib-uri
  git rev-parse --short HEAD
}

prepare() {
  [ -d cpp-netlib-uri-build ] && rm -r cpp-netlib-uri-build
  cd cpp-netlib-uri
  git submodule init
  git submodule update
}

build() {
  mkdir cpp-netlib-uri-build
  cd cpp-netlib-uri-build
  cmake -DCMAKE_BUILD_TYPE=Release \
  	-DCMAKE_C_COMPILER=clang \
	-DCMAKE_CXX_COMPILER=clang++ \
	-DBUILD_SHARED_LIBS=ON \
	-DUri_BUILD_TESTS=OFF \
  	-DUri_BUILD_DOCS=OFF \
	-DUri_DISABLE_LIBCXX=ON \
  	-DCMAKE_INSTALL_PREFIX=$pkgdir/usr ../cpp-netlib-uri
  make
}

check() {
  cd cpp-netlib-uri-build
  #make check
}

package() {
  cd cpp-netlib-uri-build
  make install
}
