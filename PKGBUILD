# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete <pellegrinoprevete@gmail.com>

pkgname="aspe"
pkgver=1.1.1.1
pkgrel=1
pkgdesc="Arch Linux build source file clone tool"
arch=(
  any
)
_host='https://github.com'
_ns='themartiancompany'
url="${_host}/${_ns}/${pkgname}"
license=(
  AGPL3
)
depends=(
  bash
  curl
)
makedepends=(
  'make'
)
checkdepends=(
  shellcheck
)
_url="file://${HOME}/${pkgname}"
source=(
  "${pkgname}-${pkgver}.tar.gz::${url}/archive/refs/tags/${pkgver}.tar.gz"
)
sha256sums=(
  "60ba3ffbc185a1c720878ad5f13eb7eefb6bd1e7fb02cf36c26e4e824daac350"
)

package() {
  cd \
    "${pkgname}-${pkgver}"
  make \
    PREFIX="/usr" \
    DESTDIR="${pkgdir}" \
    install
}

# vim:set sw=2 sts=-1 et:
