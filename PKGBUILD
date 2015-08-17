#Maintainer: David Campbell <davekong@archlinux.us>
#Contributor: Cilyan Olowen <gaknar@gmail.com>
pkgname=python-weberror
pkgver=0.10.3
pkgrel=1
pkgdesc="Web Error handling and exception catching."
arch=('any')
url="http://pylonshq.com/"
license=('custom:MIT')
depends=('python2' 'python2-webob' 'python2-tempita' 'python-simplejson'
         'python-paste>=1.7.1' 'python-pygments')
makedepends=('python2-distribute')
source=(http://pypi.python.org/packages/source/W/WebError/WebError-${pkgver}.tar.gz)
md5sums=('84b9990b0baae6fd440b1e60cdd06f9a')

build() {
  cd ${srcdir}/WebError-${pkgver}

  # Fix permission for files in egg-info
  chmod 0644 WebError.egg-info/*
  python2 setup.py install --root="${pkgdir}" --optimize=1
  install -Dm644 LICENSE ${pkgdir}/usr/share/licenses/$pkgname/LICENSE
  sed -i -e "s|#![ ]*/usr/bin/python$|#!/usr/bin/python2|" \
         -e "s|#![ ]*/usr/bin/env python$|#!/usr/bin/env python2|" \
    $(find $pkgdir -name '*.py')
}
