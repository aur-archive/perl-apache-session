# Maintainer: Maxwell Pray a.k.a. Synthead <synthead@gmail.com>

pkgname="perl-apache-session"
_cpanname="Apache-Session"
pkgver="1.93"
pkgrel="1"
pkgdesc="A persistence framework for session data."
arch=("any")
url="http://search.cpan.org/~chorny/$_cpanname-$pkgver/"
license=("GPL" "PerlArtistic")
depends=("perl>=5.5.0" "perl-test-deep")
checkdepends=("perl-test-exception")
options=("!emptydirs")
source=("http://search.cpan.org/CPAN/authors/id/C/CH/CHORNY/$_cpanname-$pkgver.tar.gz")
sha1sums=("764405935853333c2f470569185b5f3336bb1b23")

# Function to change to the working directory and set
# environment variables to override undesired options.
prepareEnvironment() {
	cd "$srcdir/$_cpanname-$pkgver"
	export \
		PERL_MM_USE_DEFAULT=1 \
		PERL_AUTOINSTALL=--skipdeps \
		PERL_MM_OPT="INSTALLDIRS=vendor DESTDIR='$pkgdir'" \
		PERL_MB_OPT="--installdirs vendor --destdir '$pkgdir'" \
		MODULEBUILDRC=/dev/null
}

build() {
	prepareEnvironment
	/usr/bin/perl Makefile.PL
	make
}

check() {
	prepareEnvironment
	make test
}

package() {
	prepareEnvironment
	make install

	# Remove "perllocal.pod" and ".packlist".
	find "$pkgdir" -name .packlist -o -name perllocal.pod -delete
}
