# Maintainer: Sergio Correia <sergio.correia@uece.net>
# Contributor: Anselmo L. S. Melo <anselmolsm@gmail.com>

pkgname=qt5-qtdeclarative-git
pkgver=20130303
pkgrel=1
pkgdesc="Qt 5: qtdeclarative module (QtQuick 2, QML)"
arch=('i686' 'x86_64')
url="https://qt.gitorious.org/qt/qtdeclarative"
license=('LGPL')
depends=('qt5-qtbase-git' 'qt5-qtxmlpatterns-git' 'qt5-qtjsbackend-git')
makedepends=('gcc' 'git')
source=()
md5sums=()

_gitroot="git://gitorious.org/qt/qtdeclarative.git"
_gitname=qt5-qtdeclarative
_gitbranch=dev

build() {
    if [ ! -d "${_gitname}" ]; then
        git clone -b ${_gitbranch} --depth 1 ${_gitroot} ${_gitname} && cd ${_gitname}
    else
        cd ${_gitname} && git reset --hard && git pull origin && git clean -dfx
    fi

    msg "GIT checkout done."

    /opt/qt5/bin/qmake
    make
}

package() {
    cd "${_gitname}"

    make INSTALL_ROOT="${pkgdir}" install
}
