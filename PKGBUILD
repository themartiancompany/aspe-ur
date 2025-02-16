# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
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
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>

_os="$( \
  uname \
    -o)"
_evmfs_available="$( \
  command \
    -v \
    "evmfs" || \
    true)"
if [[ ! -v "_evmfs" ]]; then
  if [[ "${_evmfs_available}" != "" ]]; then
    _evmfs="true"
  elif [[ "${_evmfs_available}" == "" ]]; then
    _evmfs="false"
  fi
fi
_offline="false"
_git="false"
_proj="hip"
pkgname=aspe
pkgver="1.1.1.1.1.1.1.1"
_commit="52a6cff326b2cfe72048a48f325c677306da4f6a"
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
_url="${url}"
_tag="${_commit}"
_tag_name="commit"
_tarname="${pkgname}-${_tag}"
if [[ "${_offline}" == "true" ]]; then
  _url="file://${HOME}/${pkgname}"
fi
_evmfs_network="100"
_evmfs_address="0x69470b18f8b8b5f92b48f6199dcb147b4be96571"
_evmfs_ns="0x87003Bd6C074C713783df04f36517451fF34CBEf"
_archive_sum="77110cf1486ac58602f4d11893c2ac863efc41945485c49367fc6ec5476128f6"
_evmfs_archive_uri="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}/${_archive_sum}"
_evmfs_archive_src="${_tarname}.zip::${_evmfs_archive_uri}"
_archive_sig_sum="a046135ceb6e9b3d146efd231c7fc0dc34bd64fc817f7d73763d75b8dba9ce16"
_archive_sig_uri="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}/${_archive_sig_sum}"
_archive_sig_src="${_tarname}.zip.sig::${_archive_sig_uri}"
if [[ "${_evmfs}" == "true" ]]; then
  makedepends+=(
    "evmfs"
  )
  _src="${_evmfs_archive_src}"
  _sum="${_archive_sum}"
  source+=(
    "${_archive_sig_src}"
  )
  sha256sums+=(
    "${_archive_sig_sum}"
  )
elif [[ "${_git}" == true ]]; then
  makedepends+=(
    "git"
  )
  _src="${_tarname}::git+${_url}#${_tag_name}=${_tag}?signed"
  _sum="SKIP"
elif [[ "${_git}" == false ]]; then
  if [[ "${_tag_name}" == 'pkgver' ]]; then
    _src="${_tarname}.tar.gz::${_url}/archive/refs/tags/${_tag}.tar.gz"
    _sum="d4f4179c6e4ce1702c5fe6af132669e8ec4d0378428f69518f2926b969663a91"
  elif [[ "${_tag_name}" == "commit" ]]; then
    _src="${_tarname}.zip::${_url}/archive/${_commit}.zip"
    _sum="${_archive_sum}"
  fi
fi
source=(
  "${_src}"
)
sha256sums=(
  "${_sum}"
)

package() {
  cd \
    "${_tarname}"
  make \
    PREFIX="/usr" \
    DESTDIR="${pkgdir}" \
    install
}

# vim:set sw=2 sts=-1 et:
