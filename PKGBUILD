# Maintainer: Troy Will <troydwill@gmail.com>

pkgname=ruby-stow
pkgver=20120615
pkgrel=1
pkgdesc="Packages ruby for installation with GNU Stow"
arch=('i686')
url="http://ruby-lang-org/en"
license=('BSD' 'custom')
depends=('stow' 'libyaml' 'openssl' 'libffi')
options=('!emptydirs')
source=("http://ftp.ruby-lang.org/pub/ruby/1.9/ruby-1.9.3-p194.tar.gz")
md5sums=('bc0c715c69da4d1d8bd57069c19f6c0e')

build() {
  cd  $srcdir/ruby-1.9.3-p194

  PKG_CONFIG=/usr/bin/pkg-config ./configure \
      --prefix=/usr/local \
      --bindir=/usr/local/bin/ruby-1.9.3-p194 \
      --sysconfdir=/etc \
      --enable-shared \
      --enable-pthread \
      --disable-rpath \
      --disable-install-doc
}

package() {
  cd  $srcdir/ruby-1.9.3-p194
  make DESTDIR=/stow/ruby-ruby-ruby-1.9.3.p194 install
}
