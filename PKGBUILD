# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete <pellegrinoprevete@gmail.com>

pkgname=aspe
pkgver=1.1.1.1.1
_commit="f0a8ef9f107432ada77e679cb91518921660dad8"
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
if [[ "${_git}" == "false" ]]; then
  _src="${pkgname}-${pkgver}.tar.gz::${url}/archive/refs/tags/${pkgver}.tar.gz"
  _sum="60ba3ffbc185a1c720878ad5f13eb7eefb6bd1e7fb02cf36c26e4e824daac350"
elif [[ "${_git}" == "true" ]]; then
  _src="${pkgname}-${pkgver}::git+${url}#_commit=${_commit}"
  _sum="60ba3ffbc185a1c720878ad5f13eb7eefb6bd1e7fb02cf36c26e4e824daac350"
fi
source=(
  "${_src}"
)
sha256sums=(
  "${_sum}"
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
