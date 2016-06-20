
Building Qt-5.5.1 x64 on OS X 10.11
===================================

This version of Qt might be interresting since it's the last one
to have QtWebKit.

Get the source code tarball, decompress it and rename the directory:

    > tar -zxf qt-everywhere-opensource-src-5.5.1.tar.gz
    > mv qt-everywhere-opensource-src-5.5.1 qt-src-5.5.1

Apply the patch. It fixes a compile error with Apple's latest SDK and
also fix a bug when using Objective-C souce code with precompiled
headers and generating an Xcode project (something I need).

    > cd  qt-src-5.5.1
	> patch -p1 < ../qt-patches/mac/qt-5.5.1/qt-5.5.1-mac.patch
	> cd ..

I do a shadow build, that is, build out of the source tree, so make a
directory where to build and configure. I also reset the PATH
to a sane value so that things like MacPorts don't interfere with the
build.

This is the configuration I use and know to work, you might
have some luck with something different, but some do fail. You’re on
your own if you do it differently. Also, not all examples build,
so I disable them.

Openssl has been deprecated for a while on Mac OS X and the
OS X 10.11 SDK does not ship with the openssl headers anymore. Therefor,
openssl support will be disabled by default when you compile with
Xcode 7. I have worked around that by providing the openssl headers of
an older Mac OS X SDK. This will still work since openssl itself, the
librairies, are still part of Mac OS X.

This configuration build qt with 'libc++', the c++11 library.

    > mkdir qt-build-5.5.1
    > cd qt-build-5.5.1
    > export PATH=/usr/bin:/bin:/usr/sbin:/sbin
    > ../qt-src-5.5.1/configure -debug-and-release -nomake examples -prefix /usr/local/Qt-5.5.1 -openssl -I "$PWD/../qt-patches/mac_openssl_include"

Build and install.

    > make -j3
    > sudo make install

Done!

If you need the documentation installed as well:

    > make generate_docs
    > make qch_docs
    > sudo make install_qch_docs

Tested with Xcode 7.2.1 on Mac OS X 10.11
