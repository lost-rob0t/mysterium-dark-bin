pkgname=mysterium-dark-bin
pkgver=10.17.10
pkgrel=1
pkgdesc='Legacy Mysterium Dark desktop VPN client for Mysterium Network (binary release)'
arch=('x86_64')
url='https://www.mysteriumdark.com/downloads-dark'
license=('MIT')
depends=(
  'at-spi2-core'
  'gtk3'
  'libappindicator-gtk3'
  'libnotify'
  'libsecret'
  'libxss'
  'libxtst'
  'nss'
  'openresolv'
  'util-linux-libs'
  'xdg-utils'
)
provides=('mysterium-vpn-desktop')
conflicts=('mysterium-vpn-desktop')
options=('!strip' '!debug')
_deb="mysterium-vpn-desktop_${pkgver}_amd64.deb"
source=('LICENSE')
source_x86_64=("https://github.com/mysteriumnetwork/mysterium-vpn-desktop/releases/download/${pkgver}/${_deb}")
noextract=("${_deb}")
sha256sums=('070d2f42e03987ec349cdb0f4c8668dda323ce30996c848703e70ae3944d3aa8')
sha256sums_x86_64=('6970a940466e25057f1ce0e08cbd0a9fb0e8fb2d8067a7f1454bfbc20461ee29')

prepare() {
  rm -rf "${srcdir}/deb"
  mkdir -p "${srcdir}/deb"

  cd "${srcdir}/deb"
  ar x "${srcdir}/${_deb}"

  [[ -f data.tar.xz ]] || {
    printf 'error: data.tar.xz missing from %s\n' "${_deb}" >&2
    return 1
  }
}

package() {
  tar -xJf "${srcdir}/deb/data.tar.xz" -C "${pkgdir}"

  install -d "${pkgdir}/usr/bin"
  ln -s '/opt/MysteriumDark/mysterium-vpn-desktop'     "${pkgdir}/usr/bin/mysterium-vpn-desktop"

  chmod 4755 "${pkgdir}/opt/MysteriumDark/chrome-sandbox"

  install -Dm644 "${srcdir}/LICENSE"     "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}
