# Maintainer: jbreams@gmail.com
pkgname=gonepass-git
pkgver=r22.0931c63
pkgrel=1
pkgdesc="GTK+ 1Password reader"
arch=('x86_64')
url="https://github.com/jbreams/gonepass"
license=('Apache2')
groups=()
depends=(
  'openssl'
  'jansson'
  'gtk3'
)
makedepends=(
  'git'
  'cmake'
)
install=
source=('git+https://github.com/jbreams/gonepass')
md5sums=('SKIP')

pkgver() {
	cd "$srcdir/${pkgname%-git}"
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

prepare() {
	cd "$srcdir/${pkgname%-git}"
    mkdir build
}

build() {
	cd "$srcdir/${pkgname%-git}/build"
    cmake -DCMAKE_INSTALL_PREFIX=/usr -DGSETTINGS_COMPILE=OFF ..
    make
}

package() {
	cd "$srcdir/${pkgname%-git}/build"
	make DESTDIR=$pkgdir/ install
}
