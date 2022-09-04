#!/bin/bash

# Adapted from the original PKGBUILD by Caleb Maclennan <caleb@alerque.com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# [ToDo]: Add files: User documentation
# [ToDo]: Add files: Tooling
# [FixMe]: Namcap warnings and errors

_prefix=python
_relname=uharfbuzz

pkgname=${_prefix}-${_relname}
pkgver=0.24.1
pkgrel=2
pkgdesc='Streamlined Cython bindings for the harfbuzz shaping engine'
arch=(x86_64)
url="https://github.com/harfbuzz/${_relname}"
license=(Apache)
depends=(
  "python"
)
makedepends=(
  "cython"
  "python-build"
  "python-installer"
  "python-setuptools-scm"
  "python-scikit-build"
  "python-wheel"
)
checkdepends=(
  "python-pytest"
)
source=(
  "https://files.pythonhosted.org/packages/source/${pkgname::1}/${_relname}/${_relname}-${pkgver}.zip"
)
sha512sums=(
  "61c601a1cccd20d316327d8ba743fb768c9ebccc4602a455369df54a039278a569eddae9a9df3ec9b09ef966308aa688aab32eaa6c7713cdf480104876a801f4"
)

build() {

  cd "${_relname}-${pkgver}"

  python -m build -wn
}

package() {

  cd "${_relname}-${pkgver}"

  pytest
}

package() {
  cd "${_relname}-${pkgver}"

  python -m installer -d "$pkgdir" dist/*.whl
}
