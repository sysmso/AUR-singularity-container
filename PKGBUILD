# Maintainer: Maciej Sieczka <msieczka at sieczka dot org>

pkgname='singularity-container'
pkgver='3.3.0'
pkgrel='1'
pkgdesc='Container platform focused on supporting "Mobility of Compute".'
arch=('i686' 'x86_64')
url='https://www.sylabs.io/singularity/'
license=('BSD')
makedepends=('go' 'dep')
depends=('squashfs-tools' 'libseccomp')
source=("https://github.com/sylabs/singularity/releases/download/v${pkgver}/singularity-${pkgver}.tar.gz")
noextract=("singularity-${pkgver}.tar.gz")
md5sums=('cd5c4864c6166143f28e1780797198cc')

prepare() {
  export GOPATH="${srcdir}/singularity"
  mkdir -p "${GOPATH}/src/github.com/sylabs"
  tar -zxf singularity-${pkgver}.tar.gz -C "${GOPATH}/src/github.com/sylabs"
}

build() {
  export GOPATH="${srcdir}/singularity"
  cd "${GOPATH}/src/github.com/sylabs/singularity"
  ./mconfig --prefix=/usr --sysconfdir=/etc --localstatedir=/var --sbindir=/usr/bin
  cd builddir
  make
}

package() {
  export GOPATH="${srcdir}/singularity"
  cd "${GOPATH}/src/github.com/sylabs/singularity/builddir"
  make DESTDIR="${pkgdir}" install
}

