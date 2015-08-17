# Maintainer: Andy Weidenbaum <archbaum@gmail.com>

pkgname=vim-unstack-git
pkgver=20140312
pkgrel=1
pkgdesc="Vim plugin for parsing stack traces and opening the files"
arch=('any')
depends=('vim')
makedepends=('git')
groups=('vim-plugins')
url="https://github.com/mattboehm/vim-unstack"
license=('custom:vim')
source=(git+https://github.com/mattboehm/vim-unstack)
sha256sums=('SKIP')
provides=('vim-unstack')
conflicts=('vim-unstack')
install=vimdoc.install

pkgver() {
  cd ${pkgname%-git}
  git log -1 --format="%cd" --date=short | sed "s|-||g"
}

package() {
  cd ${pkgname%-git}

  msg 'Installing documentation...'
  install -Dm 644 README.markdown "$pkgdir/usr/share/doc/vim-unstack/README.markdown"

  msg 'Installing appdirs...'
  install -dm 755 "$pkgdir/usr/share/vim/vimfiles"
  for _appdir in autoload doc plugin; do
    cp -dpr --no-preserve=ownership $_appdir "$pkgdir/usr/share/vim/vimfiles/$_appdir"
  done

  msg 'Cleaning up pkgdir...'
  find "$pkgdir" -type d -name .git -exec rm -r '{}' +
  find "$pkgdir" -type f -name .gitignore -exec rm -r '{}' +
}
