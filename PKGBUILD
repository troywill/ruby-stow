# Maintainer: Thomas Dziedzic <gostrc@gmail.com>
# Contributor: Allan McRae <allan@archlinux.org>
# Contributor: John Proctor <jproctor@prium.net>
# Contributor: Jeramy Rutley <jrutley@gmail.com>

pkgname=ruby-stow
pkgver=1.9.3_p194
pkgrel=1
pkgdesc='An object-oriented language for quick and easy programming'
arch=('i686' 'x86_64')
url='http://www.ruby-lang.org/en/'
license=('BSD' 'custom')
backup=('etc/gemrc')
provides=('rubygems' 'rake')
conflicts=('rake')
depends=('openssl' 'libffi' 'libyaml')
makedepends=('tk')
optdepends=('tk: for Ruby/TK'
            'ruby-docs: Ruby documentation')
options=('!emptydirs' '!makeflags')
install='ruby.install'
source=("ftp://ftp.ruby-lang.org/pub/ruby/${pkgver%.*}/ruby-${pkgver//_/-}.tar.bz2"
        'gemrc')
md5sums=('2278eff4cfed3cbc0653bc73085caa34'
         '6fb8e7a09955e0f64be3158fb4a27e7a')

build() {
  cd ruby-${pkgver//_/-}

  PKG_CONFIG=/usr/bin/pkg-config ./configure \
      --prefix=/usr/local \
      --sysconfdir=/etc \
      --enable-shared \
      --enable-pthread \
      --disable-rpath \
      --disable-install-doc \
      --bindir=/usr/local/bin/ruby-1.9.3_p194 \
      --mandir=/usr/local/man 

  make
}

check() {
  cd ruby-${pkgver//_/-}

  make test
}

package() {
  cd ruby-${pkgver//_/-}

  make DESTDIR="${pkgdir}/stow/ruby-1.9.3_p194" install-nodoc

  install -D -m644 ${srcdir}/gemrc "${pkgdir}/etc/gemrc"

  install -D -m644 COPYING "${pkgdir}/usr/share/licenses/ruby/LICENSE"
  install -D -m644 BSDL "${pkgdir}/usr/share/licenses/ruby/BSDL"
}
