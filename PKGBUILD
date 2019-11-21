# $Id$
# Maintainer: Michael Sasser <Michael@MichaelSasser.de>

pkgname=st-lukesmith-git
pkgver=0.8.2.r1101.131bdf6
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
source=("${srcdir}/${pkgname}::git+https://github.com/LukeSmithxyz/st#branch=master"
        "install-to-usr.patch")
noextract=()
md5sums=('SKIP'
         'b9b5e1a168e51cacf251a4fa6ae7ceee')

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

