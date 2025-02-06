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
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

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
_os="$( \
  uname \
    -o)"
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
_url_raw="${_gh_raw}/${_ns}/${_pkg}"
_url="${url}"
_tag="${_commit}"
_tag_name="commit"
_tarname="${pkgname}-${_tag}"
if [[ "${_offline}" == "true" ]]; then
  _url="file://${HOME}/${pkgname}"
fi
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
  _src="${_url_raw}/${_tag}/chains.json"
  _sum='fd06aec69084e5e33dbbb3885d03e9869a2b56932e83e9665094f65d2ce51dec'
  _license="COPYING"
  _license_sum='0d96a4ff68ad6d4b6f1f30f713b18d5184912ba8dd389f86aa7710db079abcb0'
fi
source=(
  "${_src}"
  "${_license}"
)
sha256sums=(
  "${_sum}"
  "${_license_sum}"
)

validpgpkeys=(
  # Truocolo <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
  'DD6732B02E6C88E9E27E2E0D5FC6652B9D9A6C01'
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
