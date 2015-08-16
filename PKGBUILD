# Maintainer: Karol "Kenji Takahashi" Woźniak <kenji.sx>
# Contributor: Mantas Mikulėnas <grawity@gmail.com>

pkgname=morituri
pkgver=0.2.0
pkgrel=2
pkgdesc="a CD ripper aiming for accuracy over speed, modelled after Exact Audio Copy"
arch=('i686' 'x86_64')
url="https://github.com/thomasvs/morituri"
license=("GPL3")
depends=(
    "cdparanoia"
    "cdrdao"
    "gstreamer0.10-base"
    "gstreamer0.10-python"
    "python2-musicbrainz2"
    "cddb-py"
    "python2-distribute"
)
optdepends=(
    "python2-pycdio: for 'rip drive list'"
    "gstreamer0.10-base-plugins"
    "gstreamer0.10-good-plugins"
    "gstreamer0.10-bad-plugins"
    "gstreamer0.10-ugly-plugins"
)
source=("http://thomas.apestaart.org/download/morituri/$pkgname-$pkgver.tar.bz2")
sha1sums=('63f5923611ba9e0883a7cef668a43260c7196dda')

build() {
    cd "$srcdir/$pkgname-$pkgver"
    export PYTHON="python2"
    sed -i '27s/\<python\>/&2/' doc/Makefile.am
    sed -i '1s/\<python\>/&2/' bin/rip.in etc/bash_completion.d/bash-compgen
    autoreconf -i -f
    ./configure --prefix=/usr --sysconfdir=/etc
    make
}

package() {
    cd "$srcdir/$pkgname-$pkgver"
    make DESTDIR="$pkgdir" install
    install -Dm 0644 "README" "$pkgdir/usr/share/doc/morituri/README"
}

# vim: ft=sh:ts=4:sw=4:et
