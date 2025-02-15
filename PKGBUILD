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
_build="false"
_aggregated="true"
_pkg=chains
pkgname="evm-${_pkg}"
pkgver="20241213"
_gradle_pkgver="8.8"
_commit="e932cba113c5518a83f20960f3ff9b65593adf5b"
pkgrel=1
_pkgdesc=(
  "Provides metadata for EVM chains."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  any
)
_http="https://github.com"
# see https://github.com/ethereum-lists/chains/issues/6409
# to learn why we this package has been forked
_og_ns="ethereum-lists"
_tmc_ns="themartiancompany"
_ns="${_tmc_ns}"
url="${_http}/${_ns}/${pkgname}"
_gh_raw="https://raw.githubusercontent.com"
license=(
  'AGPL3'
)
depends=(
)
optdepends=()
if [[ "${_os}" != "GNU/Linux" ]] && \
   [[ "${_os}" == "Android" ]]; then
  depends+=(
  )
  optdepends+=(
  )
fi
optdepends+=(
)
makedepends=()
if [[ "${_build}" == "true" ]]; then
  makedepends+=(
    "gradle${_gradle_pkgver}"
  )
fi
checkdepends=(
  "shellcheck"
)
provides=(
  "${pkgname}-list=${pkgver}"
  "${_og_ns}-${_pkg}-list=${pkgver}"
)
source=()
sha256sums=()
_url_raw="${_gh_raw}/${_ns}/${_pkg}"
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
_archive_sum="ced54845395b7dc1b6fe21dc5acbc59c784c2b9baaaf163e4cf04d4a7dfe46ed"
_evmfs_archive_uri="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}/${_archive_sum}"
_evmfs_archive_src="${_tarname}.zip::${_evmfs_archive_uri}"
_archive_sig_sum="a9d532106be1b77fcf42d129e677a48f5b9f4cbada3f7244c577a6ebd41f8f6f"
_archive_sig_uri="evmfs://${_evmfs_network}/${_evmfs_address}/${_evmfs_ns}/${_archive_sig_sum}"
_archive_sig_src="${_tarname}.zip.sig::${_archive_sig_uri}"
if [[ "${_build}" == "true" ]]; then
  if [[ "${_git}" == true ]]; then
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
      _sum='955be86b162169b67c4497bfc3db2d03263f2e47a48a3bb6586d59b014595c31'
    fi
  fi
elif [[ "${_aggregated}" == "true" ]]; then
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
  elif [[ "${_evmfs}" == "false" ]]; then
    _src="${_url_raw}/${_tag}/chains.json"
    _sum='fd06aec69084e5e33dbbb3885d03e9869a2b56932e83e9665094f65d2ce51dec'
  fi
  _license="COPYING"
  _license_sum='0d96a4ff68ad6d4b6f1f30f713b18d5184912ba8dd389f86aa7710db079abcb0'
fi
source+=(
  "${_src}"
  "${_license}"
)
sha256sums+=(
  "${_sum}"
  "${_license_sum}"
)

validpgpkeys=(
  # Truocolo <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  'DD6732B02E6C88E9E27E2E0D5FC6652B9D9A6C01'
  # Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
  '12D8E3D7888F741E89F86EE0FEC8567A644F1D16'
)

check() {
  local \
    _msg=()
  msg=(
    "ahah, the developers of this shit"
    "don't even check the sums of the sources"
    "they depend on and you want a build check"
    "ahahahhahahahahaahahahahahahahahhahaha"
  )
  echo \
    "${_msg[*]}"
}

package() {
  local \
    _msg=()
  if [[ "${_build}" == "true" ]]; then
    _msg=(
      "actually building this package"
      "requires packaging half of java"
      "kirsh. Good luck with that;"
      "but it will happen, no worry,"
      "the heck I'll let these dishonests"
      "keep behaving as gnorris about their"
      "holes."
      "Besides, the heck when this will happen"
      "this software will useful to anything"
      "anymore. Jeez what a bunch of shameless"
      "hypocrites."
    )
    echo \
      "${_msg[*]}"
  elif [[ "${_aggregated}" == "true" ]]; then
    install \
      -Dm644 \
      "${srcdir}/chains.json" \
      "${pkgdir}/usr/lib/evm-${_pkg}/chains.json"
    install \
      -Dm644 \
      "${srcdir}/COPYING" \
      "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"

  fi
}

# vim: ft=sh syn=sh et
