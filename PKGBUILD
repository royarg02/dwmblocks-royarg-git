# Maintainer: Anurag Roy <anuragr9847@gmail.com>
_pkgname="dwmblocks"
pkgname="$_pkgname-royarg-git"
pkgver=1.0.r86.7d0fa72
pkgrel=1
pkgdesc="A modified version of the modular status bar for dwm written in C."
arch=('x86_64')
url="https://github.com/RoyARG02/$_pkgname"
license=('ISC')
depends=('sh' 'libx11')
makedepends=('git')
optdepends=('btop: system resource monitor'
  'figlet: expanded time display'
  'ncpamixer: audio mixer'
  'noto-fonts-emoji: for emoji support'
  'pulsemixer: audio mixer'
  'playerctl: Control media players'
  'ttf-joypixels: for emoji support'
  'xorg-xbacklight: for controlling display backlight'
  'xorg-xset: for controlling display sleep'
)
provides=("$_pkgname")
conflicts=("$_pkgname")
install="$pkgname.install"
source=(
  "git+$url.git"
)
md5sums=('SKIP')

pkgver() {
  cd "$_pkgname"
  commits="$(git rev-list --count HEAD)"
  gitref="$(git rev-parse --short=7 HEAD)"
  printf "1.0.r%s.%s" "$commits" "$gitref"
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
}
