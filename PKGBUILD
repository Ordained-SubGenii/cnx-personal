# Maintainer: feindsdeluna 
pkgname=cnx-personal-git
pkgver=0.3.0.r3.g6684b06
pkgrel=1
pkgdesc='cnx - A simple X11 status bar for use with simple WMs in Rust. custom git pkg'
arch=('x86_64')
# url='https://github.com/mjkillough/cnx'
url='https://github.com/Ordained-SubGenii/cnx-personal'
license=('MIT')
makedepends=('cargo' 'git')
depends=('libxcb' 'xcb-util' 'xcb-util-wm' 'xcb-util-keysyms' 'pango' 'cairo')
optdepends=('alsa-lib' 'alsa-utils' 'wireless_tools' 'lm_sensors')
provides=("${pkgname%-git}")
conflicts=("${pkgname%-git}")
source=("${pkgname%-git}::git+$url")
sha1sums=('SKIP')
md5sums=('SKIP')
sha256sums=('SKIP')

pkgver() {
  cd "${pkgname%-git}"
  echo $(grep '^version =' cnx/Cargo.toml|head -n1|cut -d\" -f2).r$(git rev-list --count HEAD).g$(git describe --always)
}

build() {
  cd "${pkgname%-git}"
  cargo build --release 
}

package() {
  cd "${pkgname%-git}"
  install -Dm755 target/release/cnx-bin -t "$pkgdir/usr/bin"
  install -Dm644 LICENSE                -t "$pkgdir/usr/share/licenses/${pkgname%-git}"
  install -Dm644 README.md              -t "$pkgdir/usr/share/doc/${pkgname%-git}"
}
