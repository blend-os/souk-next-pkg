# Maintainer: Rudra Saraswat <rs2009@ubuntu.com>
# Original maintainer: Philip Goto <philip.goto@gmail.com>

pkgname=souk-next-git
pkgver=r188.6afe19e
pkgrel=1
pkgdesc="Flatpak App Store"
arch=(i686 x86_64 armv7h aarch64)
url="https://gitlab.gnome.org/haecker-felix/souk"
license=(GPL3)
depends=(flatpak gtk4 libadwaita)
makedepends=(cargo git meson)
provides=(souk souk-next)
conflicts=(souk souk-next)
source=("git+${url}.git#branch=souk-next")
md5sums=(SKIP)

pkgver() {
	cd souk
	( set -o pipefail
		git describe --long --tags 2>/dev/null | sed 's/^v//;s/\([^-]*-g\)/r\1/;s/-/./g' ||
		printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
	)
}

build() {
	arch-meson souk build
	meson compile -C build
}

package() {
	DESTDIR="${pkgdir}" meson install -C build
}
