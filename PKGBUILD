# Maintainer: Doridian <archlinux at doridian dot net>

# Make sure to put "sd-pcr7lock" in /etc/mkinitcpio.conf

pkgname=mkinitcpio-sd-pcr7lock-hook
pkgver=1.1
pkgrel=1
pkgdesc='An initcpio hook to extend PCRs after sd-encrypt to prevent unsealing the root volume key after initramfs'
arch=('any')
url='https://aur.archlinux.org/mkinitcpio-cleviseal-hook'
license=('MIT')
depends=('tpm2-tools' 'mkinitcpio' 'python' 'python-yaml')
source=(
  'systemd-cryptenroll-pcr7lock'
  'initcpio.install'
  'systemd-pcrphase-pcr7lock.service'
)
md5sums=(
  'SKIP'
  'SKIP'
  'SKIP'
)

build() {
  echo 'No build step needed'
}

package() {
  install -Dm644 "${srcdir}/initcpio.install" "${pkgdir}/etc/initcpio/install/sd-pcr7lock"
  install -Dm644 "${srcdir}/systemd-pcrphase-pcr7lock.service" "${pkgdir}/usr/lib/systemd/system/systemd-pcrphase-pcr7lock.service"
  mkdir -p "${pkgdir}/usr/lib/systemd/system/initrd.target.wants"
  ln -sf ../systemd-pcrphase-pcr7lock.service "${pkgdir}/usr/lib/systemd/system/initrd.target.wants/systemd-pcrphase-pcr7lock.service"
  install -Dm755 "${srcdir}/systemd-cryptenroll-pcr7lock" "${pkgdir}/usr/bin/systemd-cryptenroll-pcr7lock"
}
