
Building Qt-5.6.2 x64 on OS X 10.12
===================================

Get the source code tarball, decompress it and rename the directory:

    > tar -zxf qt-everywhere-opensource-src-5.6.2.tar.gz
    > mv qt-everywhere-opensource-src-5.6.2 qt-src-5.6.2

Apply the patch. It fixes a compile error with Apple's latest SDK and
also fix a bug when using Objective-C souce code with precompiled
headers and generating an Xcode project (something I need).

    > cd  qt-src-5.6.2
	> patch -p1 < ../qt-patches/mac/qt-5.6.2/qt-5.6.2-mac.patch
	> cd ..

I do a shadow build, that is, build out of the source tree, so make a
directory where to build and configure. I also reset the PATH
to a sane value so that things like MacPorts don't interfere with the
build.

Openssl has been deprecated on Mac OS X but Qt 5.6.1 now uses the
Mac OS X SDK ssl libraries, no need to configure openssl anymore.

Qt 5.6.2 build with libc++, so c++11 is usable from client code.

    > mkdir qt-build-5.6.2
    > cd qt-build-5.6.2
    > export PATH=/usr/bin:/bin:/usr/sbin:/sbin
    > ../qt-src-5.6.2/configure -debug-and-release -nomake examples -prefix /usr/local/Qt-5.6.2

Build and install.

    > make -j3
    > sudo make install

Done!

If you need the documentation installed as well:

    > make generate_docs
    > make qch_docs
    > sudo make install_qch_docs


Tested with Xcode 8 on Mac OS X 10.12
