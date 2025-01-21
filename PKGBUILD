# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete <pellegrinoprevete@gmail.com>

_git="false"
_proj="hip"
pkgname=aspe
pkgver=1.1.1.1.1.1.1
_commit="5f509e13ccd0cc61de71a6b9f52bbe6018f12a08"
pkgrel=1
_pkgdesc=(
  "Build recipes retrieval"
  "tool."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  'any'
)
_host='https://github.com'
_ns='themartiancompany'
url="${_host}/${_ns}/${pkgname}"
license=(
  'AGPL3'
)
depends=(
  'evm-contracts-tools'
  'evm-wallet'
  'evmfs'
  'libcrash-bash'
  'libevm'
  'ur-contracts'
  'ur'
)
makedepends=(
  'make'
)
checkdepends=(
  'shellcheck'
)
optdepends=(
  'git: to download sources from censorable sources.'
)
group=(
  "${_proj}"
)
_url="file://${HOME}/${pkgname}"
if [[ "${_git}" == "false" ]]; then
  _src="${pkgname}-${pkgver}.tar.gz::${url}/archive/refs/tags/${pkgver}.tar.gz"
  _sum='3be1df805d609534963e9d1e7d2ce1a3922a4d02a1dd41c2d364eeff86769802'
elif [[ "${_git}" == "true" ]]; then
  _src="${pkgname}-${pkgver}::git+${url}#_commit=${_commit}"
  _sum='3be1df805d609534963e9d1e7d2ce1a3922a4d02a1dd41c2d364eeff86769802'
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
