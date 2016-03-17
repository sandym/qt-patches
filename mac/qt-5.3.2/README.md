
Building Qt-5.3.2 x64 on OS X 10.11 with Xcode
==============================================

This version of Qt is the last one to support Mac OS X 10.6.

Get the source code tarball, decompress it and rename the directory:

    > tar -zxf qt-everywhere-opensource-src-5.3.2.tar.gz
    > mv qt-everywhere-opensource-src-5.3.2 qt-src-5.3.2

Apply the patch. It fixes a compile error with Apple's latest SDK and
also fix a bug when using Objective-C souce code with precompiled
headers and generating an Xcode project (something I need).

    > cd  qt-src-5.3.2
	> patch -p1 < ../qt-patches/mac/qt-5.3.2/qt-5.3.2-mac.patch
	> cd ..

I do a shadow build, that is, build out of the source tree, so make a
directory where to build and configure. I also reset the PATH
to a sane value so that things like MacPorts don't interfere with the
build.


Openssl has been deprecated for a while on Mac OS X and the
OS X 10.11 SDK does not ship with the openssl headers anymore. Therefor,
openssl support will be disabled by default when you compile with
Xcode 7. I have worked around that by providing the openssl headers of
an older Mac OS X SDK. This will still work since openssl itself, the
librairies, are still part of Mac OS X.

This configuration will build qt with 'libc++', the c++11 library,
if you want to be able to deploy to Mac OS X 10.6, add '-no-c++11'
to the configuration. This will build with 'libstdc++' instead.

    > mkdir qt-build-5.3.2
    > cd qt-build-5.3.2
    > export PATH=/usr/bin:/bin:/usr/sbin:/sbin
    > ../qt-src-5.3.2/configure -debug-and-release -nomake examples -prefix /usr/local/Qt-5.3.2 -arch x86_64 -openssl -I "$PWD/../qt-patches/mac_openssl_include"

Build and install.

    > make -j3
    > sudo make install

Done!

Tested with Xcode 7.2.1 on Mac OS X 10.11
