# Maintainer: Doni Halim <donihaalim@gmail.com>

pkgname=jetporch-git
pkgver=r341.40f8151
pkgrel=1
pkgdesc="Jet is a general-purpose, community-driven IT automation platform for configuration, deployment, orchestration, patching, and arbitrary task execution workflows."
arch=('x86_64')
url="https://www.jetporch.com/"
license=('GPL')
makedepends=('git' 'rust' 'cargo' 'openssl')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
source=('git+https://git.sr.ht/~mpdehaan/jetporch')
sha256sums=('SKIP')

pkgver () {
  cd "${pkgname%-git}"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short=7 HEAD)"
}

build() {
  cd "${pkgname%-git}"
  make
}

package() {
  cd "${pkgname%-git}"
  install -Dm755 target/release/jetp "${pkgdir}/usr/bin/jetp"
  install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname%-git}/README.md"
  cp -R examples "${pkgdir}/usr/share/doc/${pkgname%-git}/"
}
