# Original author: Xiao-Long Chen <chenxiaolong@cxl.epac.to>
pkgname=ricoh-e823-fix
pkgver=1
pkgrel=1
pkgdesc="Fix for the Ricoh e823 card reader used in Lenovo laptops"
arch=('any')
url="https://github.com/qwerty12/ricoh-e823-fix"
license=('GPL')
depends=('pciutils')
optdepends=('systemd: systemd support')
source=('e823fix.modprobe.conf'
        'e823fix.wrapper'
        'e823fix.service')
sha512sums=('7c97052acf2c3c8535f0bd4e9e5b8e466c4fce165edc105a4895ddf1a607b13818a1bb6134dc2a7df9d417d0fda16db4487acc360ad6fefd0cb9ff81de3cd696'
            '0cf95aa3c01b5f63f547d1fdc969495b04c9524b976df1f9628f2a5c68dca4fac29be8f4abcda7f416a20cf576a1d2bdc6ee3c7e9ad3d6362d12845160f4a658'
            'dbec1ae73b82921e735f6a84a76778c5cf4698f445b15f1bacf575676ba3ec079a2c41a65e4ec368853dce92431ab2f7523ffa5fde0d492995032cc0d88c48e1')

package() {
  cd "${srcdir}"
  install -Dm644 e823fix.modprobe.conf "${pkgdir}/etc/modprobe.d/e823fix.conf"
  install -Dm644 e823fix.service "${pkgdir}/usr/lib/systemd/system/e823fix.service"
  install -Dm755 e823fix.wrapper "${pkgdir}/usr/bin/e823fix_wrapper"
}

# vim:set ts=2 sw=2 et:
