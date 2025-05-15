# Maintainer: Doridian <archlinux at doridian dot net>

# Make sure to put "sd-pcr8lock" in /etc/mkinitcpio.conf

pkgname=mkinitcpio-sd-pcr8lock-hook
pkgver=1.1
pkgrel=1
pkgdesc='An initcpio hook to extend PCRs after sd-encrypt to prevent unsealing the root volume key after initramfs'
arch=('any')
url='https://aur.archlinux.org/mkinitcpio-cleviseal-hook'
license=('MIT')
depends=('tpm2-tools' 'mkinitcpio' 'python' 'python-yaml')
conflicts=('mkinitcpio-sd-pcr7lock-hook')
source=(
  'systemd-cryptenroll-pcr8lock'
  'initcpio.install'
  'systemd-pcrphase-pcr8lock.service'
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
  install -Dm644 "${srcdir}/initcpio.install" "${pkgdir}/etc/initcpio/install/sd-pcr8lock"
  install -Dm644 "${srcdir}/systemd-pcrphase-pcr8lock.service" "${pkgdir}/usr/lib/systemd/system/systemd-pcrphase-pcr8lock.service"
  mkdir -p "${pkgdir}/usr/lib/systemd/system/initrd.target.wants"
  ln -sf ../systemd-pcrphase-pcr8lock.service "${pkgdir}/usr/lib/systemd/system/initrd.target.wants/systemd-pcrphase-pcr8lock.service"
  install -Dm755 "${srcdir}/systemd-cryptenroll-pcr8lock" "${pkgdir}/usr/bin/systemd-cryptenroll-pcr8lock"
}
