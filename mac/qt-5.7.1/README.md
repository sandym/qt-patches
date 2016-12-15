
Building Qt-5.7.1 x64 on OS X 10.11
===================================

Get the source code tarball, decompress it and rename the directory:

    > tar -zxf qt-everywhere-opensource-src-5.7.1.tar.gz
    > mv qt-everywhere-opensource-src-5.7.1 qt-src-5.7.1

I do a shadow build, that is, build out of the source tree, so make a
directory where to build and configure. I also reset the PATH
to a sane value so that things like MacPorts don't interfere with the
build.

Openssl has been deprecated on Mac OS X but Qt 5.7.1 now uses the
Mac OS X SDK ssl libraries, no need to configure openssl anymore.

    > mkdir qt-build-5.7.1
    > cd qt-build-5.7.1
    > export PATH=/usr/bin:/bin:/usr/sbin:/sbin
    > ../qt-src-5.7.1/configure -debug-and-release -nomake examples -prefix /usr/local/Qt-5.7.1

Build and install.

    > make -j3
    > sudo make install

Done!

If you need the documentation installed as well:

    > make generate_docs
    > make qch_docs
    > sudo make install_qch_docs


Tested with Xcode 8.2 on Mac OS X 10.12
