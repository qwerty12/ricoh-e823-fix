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
sha512sums=('c94c75d81269eefc71a948f43e5546e36c4f82ac86a866ba3c4c6aed210c420dae45f3df377c3cbe76d40a432289752f5608ef6c78e6cda9c8ce83df7e6b6f62'
            'f01d60f84a71324d0ccd6b020ade0f1aa611f4b327d008ffa16f44b3b5a96e0b55f5ed6d034dccd690a956223835fc10705cc720f0e0afd17b162b02f153c1b6'
            'dbec1ae73b82921e735f6a84a76778c5cf4698f445b15f1bacf575676ba3ec079a2c41a65e4ec368853dce92431ab2f7523ffa5fde0d492995032cc0d88c48e1')

package() {
  cd "${srcdir}"
  install -Dm644 e823fix.modprobe.conf "${pkgdir}/etc/modprobe.d/e823fix.conf"
  install -Dm644 e823fix.service "${pkgdir}/usr/lib/systemd/system/e823fix.service"
  install -Dm755 e823fix.wrapper "${pkgdir}/usr/bin/e823fix_wrapper"
}

# vim:set ts=2 sw=2 et:
