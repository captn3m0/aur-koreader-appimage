# Maintainer: Nemo <archlinux at captnemo dot in>
pkgname=koreader-appimage
pkgver=2018.04.10.beta
pkgrel=1

pkgdesc="An ebook reader application supporting PDF, DjVu, EPUB, FB2 and many more formats"
arch=('x86_64')
depends=('zlib')
url="http://koreader.rocks/"
license=('AGPL3')
noextract=('koreader-appimage-x86_64-linux-gnu-v2015.11-1644-ge39ed90_2018-04-09.AppImage')
options=('!strip')
install=${pkgname}.install
source=("https://github.com/koreader/koreader/releases/download/v2018.04.10-beta/koreader-appimage-x86_64-linux-gnu-v2015.11-1644-ge39ed90_2018-04-09.AppImage")
sha256sums=('85550ed003a906962e33db1b28132c1d2b8264185e1aa145e3a5693eb49a5e64')


prepare() {
    cd "${srcdir}"
    mv "koreader-appimage-x86_64-linux-gnu-v2015.11-1644-ge39ed90_2018-04-09.AppImage" "koreader.AppImage"
    7z x "${srcdir}/koreader.AppImage" koreader.png
    7z x "${srcdir}/koreader.AppImage" koreader.desktop
    mkdir -p usr/share/pixmaps
    mkdir -p usr/share/applications
    mkdir -p opt/appimages
    mv koreader.png usr/share/pixmaps
    patch -Np0 <../koreader.patch
    mv koreader.desktop usr/share/applications
    cp koreader.AppImage opt/appimages/
}

package() {
    cd "${srcdir}"
    cp -rp usr "${pkgdir}/usr"
    cp -rp opt "${pkgdir}/opt"
}