# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

_py="python2"
_pkg="dill"
pkgname="${_py}-${_pkg}"
pkgver=0.3.5
pkgrel=1
pkgdesc="Serialize all of python (almost)"
_ns="uqfoundation"
url="https://github.com/${_ns}/${_pkg}"
depends=(
  "${_py}"
)
makedepends=(
  "${_py}-setuptools"
)
optdepends=(
  "${_py}-objgraph: graph support"
)
license=('CUSTOM')
arch=('any')
_pypi_url="https://files.pythonhosted.org/packages/source"
source=(
  "${_pypi_url}/${_pkg::1}/${_pkg}/${_pkg}-${pkgver}.tar.gz"
)
sha256sums=(
  '3a11d19c15d409296a2ee714b1dbd5efb733a329f0d89c0e58aad6154ab6f2f5'
)

build() {
  cd "${srcdir}/${_pkg}-${pkgver}"
  "${_py}" setup.py build
}

package() {
  cd "${srcdir}/${_pkg}-${pkgver}"
  "${_py}" setup.py install --root="${pkgdir}" \
                           --optimize=1

  mv "${pkgdir}/usr/bin/get_objgraph" \
     "${pkgdir}/usr/bin/get_objgraph2.7"

  mv "${pkgdir}/usr/bin/undill" \
     "${pkgdir}/usr/bin/undill2.7"

  install -D -m644 LICENSE \
          "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
# vim:set sw=2 sts=-1 et:
