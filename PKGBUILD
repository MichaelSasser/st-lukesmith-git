# $Id$
# Maintainer: Michael Sasser <Michael@MichaelSasser.de>

pkgname=st-lukesmith-git
pkgver=0.8.1.r998.ae9739f
pkgrel=1
pkgdesc="Luke Smith's patched version of Suckless Terminal"
arch=('i686' 'x86_64')
url="https://suckless.org/"
license=('MIT')
groups=()
depends=('libx11' 'libxft')
makedepends=()
optdepends=()
provides=('st')
conflicts=()
replaces=()
backup=()
options=()
changelog=
source=("${srcdir}/${pkgname}::git+https://github.com/LukeSmithxyz/st#branch=patched"
        "install-to-usr.patch")
noextract=()
md5sums=('SKIP'
         '2c73d2fe2c5eb9072039abb4241561a4')

pkgver() {
  cd "${srcdir}/${pkgname}"
  printf "%s.r%s.%s" \
    "$(sed -rn 's/VERSION\s=\s([0-9].[0-9].[0-9])\.*/\1/p' config.mk)" \
    "$(git rev-list --count HEAD)" \
    "$(git rev-parse --short HEAD)"
}

prepare() {
  cd "${srcdir}/${pkgname}"

  # Installs st to /usr and not to /usr/local
  patch -p1 -i ../install-to-usr.patch
}

build() {
  cd "${srcdir}/${pkgname}"

  make
}

package() {
  cd "${srcdir}/${pkgname}"

  make DESTDIR="${pkgdir}/" install
  install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README"
  install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

# vim:set ts=2 sw=2 et:

