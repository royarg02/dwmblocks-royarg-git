# Maintainer: Anurag Roy <anuragr9847@gmail.com>
_pkgname="dwmblocks"
pkgname="$_pkgname-royarg-git"
pkgver=1.0.f46922a
pkgrel=1
pkgdesc="A modified version of the modular status bar for dwm written in C."
arch=('x86_64')
url="https://github.com/RoyARG02/$_pkgname"
license=('ISC')
depends=('sh' 'libx11')
makedepends=('git')
optdepends=('acpilight: for controlling display backlight'
  'btop: system resource monitor'
  'noto-fonts-emoji: for emoji support'
  'pulsemixer: for volume control'
  'ttf-joypixels: for emoji support'
  'xorg-xbacklight: for controlling display backlight'
  'xorg-xset: for controlling display sleep'
)
provides=("$_pkgname")
conflicts=("$_pkgname")
install="$pkgname.install"
source=(
  "git+$url.git"
  https://raw.githubusercontent.com/RoyARG02/user_files/master/files/scripts/sb-battery
  https://raw.githubusercontent.com/RoyARG02/user_files/master/files/scripts/sb-clock
  https://raw.githubusercontent.com/RoyARG02/user_files/master/files/scripts/sb-memory
  https://raw.githubusercontent.com/RoyARG02/user_files/master/files/scripts/sb-nettraf
  https://raw.githubusercontent.com/RoyARG02/user_files/master/files/scripts/sb-pa-sink
  https://raw.githubusercontent.com/RoyARG02/user_files/master/files/scripts/sb-pa-source
)
md5sums=('SKIP'
         '93dd35a28c01d5c3321f5e840e8c83bb'
         '649278834432ad707cb9ce4df0a6b159'
         'ed858e38ec51a983f1b9a9e53a0b51c3'
         '8aca79f031f40cbd4bcdabf6eacf0855'
         '9e43871322c76383d66bfe0b60930e86'
         '15d9d20528f6bdefc7ac83184079ec7e')

pkgver() {
  cd "$_pkgname"
  git describe --always --long | sed 's/^/1\.0\./'
}

build() {
  cd "$_pkgname"
  make
}

package() {
  cd "$_pkgname"
  make PREFIX=/usr DESTDIR="$pkgdir" install
  install -Dm644 README.md "$pkgdir"/usr/share/doc/$pkgname/README.md
  install -Dm644 LICENSE "$pkgdir"/usr/share/licenses/$pkgname/LICENSE
  install -Dm755 "$startdir"/sb-* "$pkgdir"/usr/bin/
}
