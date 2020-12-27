# Maintainer: Ben Mather <bwhmather@bwhmather.com>

pkgname=wmii-git
pkgver=r2820.489c9e47
pkgrel=1
pkgdesc="A dynamic window manager for X11."
arch=('i686' 'x86_64')
url="https://github.com/bwhmather/wmii"
license=('MIT')
categories=()
depends=('libixp' 'libx11' 'libxinerama' 'libxrandr')
makedepends=('git' 'txt2tags')
optdepends=(
  'dash: for use of the default wmiirc configs'
  'libxft: for anti-aliased font support'
  'xorg-xmessage: for use of the default wmiirc configs'
  'plan9port: for use of the alternative plan9port wmiirc'
  'python2: for use of the alternative Python wmiirc'
  'ruby-rumai: for use of the alternative Ruby wmiirc'
)
provides=(wmii)
conflicts=(wmii wmii-hg)
source=("wmii::git+$url")
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/wmii"
  printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
  cd "$srcdir/wmii"
  make PREFIX=/usr
}

package() {
  cd "$srcdir/wmii"
  make DESTDIR="$pkgdir/" PREFIX=/usr install
  install -Dm644 README.md $pkgdir/usr/share/doc/wmii/README.md
  install -Dm644 LICENSE $pkgdir/usr/share/licenses/wmii/LICENSE
  rm $pkgdir/usr/share/doc/wmii/LICENSE
}

