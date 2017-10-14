#Maintainer: Heropoo <aiyouyou1000@163.com>

_pkgname='sublime_text_3'
pkgname=sublime-text-stable-imfix
pkgver=3.3143
pkgrel=1
pkgdesc='Sublime text 3 stable imfix'
arch=('x86_64')
license=('custom')
depends=('libpng' 'gtk2')
#install="sublime-text-stable-imfix.install"
url="http://www.sublimetext.com/"
source=("sublime_text_3_build_3143_x64.tar.bz2" "sublime_text.desktop" "sublime_imfix.c")
sha256sums=("9ce120c4f28b239d3b3860ee672d9d87e1397a4c08ee6c4e62fd6e261a296519"
"17266195f442ad8a8e80df2c942d7f5261896ac7b375560c0150c341ceeb4191"
"f55a5c290cc09abfe0c9f71472224c08f6c396f102c2ddc7257a6b8da3f56f52"
)

package() {
  gcc -shared -o libsublime-imfix.so sublime_imfix.c `pkg-config --libs --cflags gtk+-2.0` -fPIC
  
  cd "${srcdir}"

  install -dm755 "${pkgdir}/opt"
  cp --preserve=mode -r "sublime_text_3" "${pkgdir}/opt/sublime_text_3"

  install -Dm644 "libsublime-imfix.so" "${pkgdir}/opt/sublime_text_3/"
  
  for res in 128x128 16x16 256x256 32x32 48x48; do
    install -dm755 "${pkgdir}/usr/share/icons/hicolor/${res}/apps"
    ln -s "/opt/sublime_text_3/Icon/${res}/sublime-text.png" "${pkgdir}/usr/share/icons/hicolor/${res}/apps/sublime-text.png"
  done

  install -dm755 "${pkgdir}/usr/share/applications"
  install -Dm644 "sublime_text.desktop" "${pkgdir}/usr/share/applications/sublime_text_3.desktop"

  install -dm755 "${pkgdir}/usr/bin"
  ln -s "/opt/sublime_text_3/sublime_text" "${pkgdir}/usr/bin/subl3"
}
