# Maintainer: Morten Linderud <foxboron@archlinux.org>
# Maintainer: Lukas Fleischer <lfleischer@archlinux.org>
# Contributor: Pierre Neidhardt <ambrevar@gmail.com>
# Contributor: Florian Bruhin (The Compiler) <archlinux.org@the-compiler.org>

pkgname=qutebrowser-qt6-git
pkgver=2.5.1.r258.g64e8c7132
pkgrel=1
pkgdesc="A keyboard-driven, vim-like browser based on PyQt6"
arch=("any")
url="https://www.qutebrowser.org/"
license=("GPL")
depends=("python-jinja" "python-pyqt6" "python-yaml" "qt6-base" "python-pyqt6-webengine")
makedepends=("asciidoc" "python-setuptools")
optdepends=("python-adblock: adblocking backend"
            "python-pygments"
            "pdfjs: displaying PDF in-browser")
#            "gst-libav: media playback with qt5-webkit backend"
#            "gst-plugins-base: media playback with qt5-webkit backend"
#            "gst-plugins-good: media playback with qt5-webkit backend"
#            "gst-plugins-bad: media playback with qt5-webkit backend"
#            "gst-plugins-ugly: media playback with qt5-webkit backend"
#            "qt5-webkit: alternative backend")
options=(!emptydirs)
conflicts=('qutebrowser' 'qutebrowser-git')
provides=('qutebrowser' 'qutebrowser-git')
source=(git+https://github.com/qutebrowser/qutebrowser#branch=qt6-v2)
sha256sums=('SKIP')
#source=("https://github.com/qutebrowser/qutebrowser/releases/download/v$pkgver/qutebrowser-$pkgver.tar.gz"
#        "https://github.com/qutebrowser/qutebrowser/releases/download/v$pkgver/qutebrowser-$pkgver.tar.gz.asc")
#validpgpkeys=("E04E560002401B8EF0E76F0A916EB0C8FD55A072")
#sha256sums=('e6885886a84cd166a6ba633794a58a4c67d871c27188127e5ddbc5276d76edbc'
#            'SKIP')
pkgver() {
    cd "$srcdir/qutebrowser"
    # Minor releases are not part of the master branch
    _tag=$(git tag --sort=v:refname | tail -n1)
    printf '%s.r%s.g%s' "${_tag#v}" "$(git rev-list "$_tag"..HEAD --count)" "$(git rev-parse --short HEAD)"
}

build() {
    #cd "$pkgname-$pkgver"
    cd "$srcdir/qutebrowser"
    make -f misc/Makefile all
}

package() {
    #cd "$pkgname-$pkgver"
    cd "$srcdir/qutebrowser"
    make -f misc/Makefile DESTDIR="$pkgdir" PREFIX=/usr install
}
