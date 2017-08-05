# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://projects.archlinux.org/svntogit/packages.git/tree/trunk?h=packages/xf86-input-vmmouse
# 						Maintainer: Jan de Groot <jgc@archlinux.org>

pkgname=xf86-input-vmmouse
pkgver=13.1.0
pkgrel=6
pkgdesc="X.org VMWare Mouse input driver"
arch=(x86_64)
license=('custom')
url="https://xorg.freedesktop.org/"
#depends=('glibc' 'sh')
makedepends=('xorg-server-devel' 'X-ABI-XINPUT_VERSION=24.1' 'resourceproto' 'scrnsaverproto')
conflicts=('xorg-server<1.19' 'X-ABI-XINPUT_VERSION<24.1' 'X-ABI-XINPUT_VERSION>=25')
groups=('xorg-drivers')
source=(${url}/releases/individual/driver/${pkgname}-${pkgver}.tar.bz2)
sha256sums=('0af558957ac1be1b2863712c2475de8f4d7f14921fd01ded2e2fde4921b19319')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

build() {
  cd ${pkgname}-${pkgver}
  ./configure --prefix=/usr \
    --with-udev-rules-dir=/usr/lib/udev/rules.d
  make
}

package() {
  cd ${pkgname}-${pkgver}
  make DESTDIR="${pkgdir}" install
  install -m755 -d "${pkgdir}/usr/share/licenses/${pkgname}"
  install -m644 COPYING "${pkgdir}/usr/share/licenses/${pkgname}/"
  rm -rfv ${pkgdir}/usr/{lib,share}/hal
}
