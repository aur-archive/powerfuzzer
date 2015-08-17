# Archtrack maintainer: Evan Teitelman <teitelmanevan at gmail dot com>
# Contributor: Francesco Piccinno <stack.box@gmail.com>

pkgname=powerfuzzer
pkgver=1_beta
pkgrel=1
pkgdesc="Powerfuzzer is a highly automated web fuzzer based on many other Open Source fuzzers available (incl. cfuzzer, fuzzled, fuzzer.pl, jbrofuzz, webscarab, wapiti, Socket Fuzzer). It can detect XSS, Injections (SQL, LDAP, commands, code, XPATH) and others."
url="http://www.powerfuzzer.com"
updateurl="http://sourceforge.net/projects/powerfuzzer/files/=>powerfuzzer_v"
arch=(any)
depends=('python' 'wxpython' 'python-utidylib')
license=('GPL')
source=(http://downloads.sourceforge.net/$pkgname/${pkgname}_v${pkgver}_patched.zip)
md5sums=('2c7fa861f7f17b68640f5ae5c75b781a')

groups=(archtrack archtrack-vulnerability-analysis archtrack-web-applications)

prepare() {
  cd "$srcdir/${pkgname}_v${pkgver}_patched"
  # convert tabs to spaces to fix python tab/space inconsistency errors
  expand $pkgname.py | sed 's/env python$/env python2/' > $pkgname
}

build() {
  cd "$srcdir/${pkgname}_v${pkgver}_patched"
  chmod -x *
  rm COPYING
  chmod +x $pkgname

  mkdir -p $pkgdir/usr/share/$pkgname/
  cp * $pkgdir/usr/share/$pkgname/

  mkdir $pkgdir/usr/bin
  cd $pkgdir/usr/bin
  ln -sf /usr/share/$pkgname/$pkgname $pkgname
}
