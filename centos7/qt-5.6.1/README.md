
Building Qt-5.6.1 x64 on centos7
================================

Dependencies: This is the list of all development package I have installed, a subset of it might be enough but I don't know which one... Install what you need.

    > sudo yum install alsa-lib-devel at-spi2-atk-devel atk-devel bzip2-devel cairo-devel cairo-gobject-devel cups-devel dbus-devel expat-devel fontconfig-devel freetype-devel gdk-pixbuf2-devel glib2-devel glibc-devel gtk2-devel gtk3-devel harfbuzz-devel keyutils-libs-devel krb5-devel libX11-devel libXau-devel libXcomposite-devel libXcursor-devel libXdamage-devel libXext-devel libXfixes-devel libXft-devel libXi-devel libXinerama-devel libXrandr-devel libXrender-devel libXxf86vm-devel libcom_err-devel libcurl-devel libdrm-devel libgudev1-devel libicu-devel libpng-devel libquadmath-devel libselinux-devel libsepol-devel libstdc++-devel libverto-devel libxcb-devel libxkbfile-devel libxshmfence-devel libzip-devel mesa-libEGL-devel mesa-libGL-devel mesa-libGLU-devel mtdev-devel ncurses-devel openssl-devel pango-devel pcre-devel pixman-devel pulseaudio-libs-devel readline-devel sqlite-devel xcb-util-devel xcb-util-image-devel xcb-util-keysyms-devel xcb-util-renderutil-devel xcb-util-wm-devel xorg-x11-proto-devel xorg-x11-xkb-utils-devel zlib-devel

Get the source code tarball, decompress it and rename the directory:

    > tar -zxf qt-everywhere-opensource-src-5.6.1.tar.gz
    > mv qt-everywhere-opensource-src-5.6.1 qt-src-5.6.1

I do a shadow build, that is, build out of the source tree, so make a
directory where to build and configure.

    > mkdir qt-build-5.6.1
    > cd qt-build-5.6.1
    > ../qt-src-5.6.1/configure -nomake examples -prefix /usr/local/Qt-5.6.1

Build and install.

    > make -j3
    > sudo make install

Done!

If you need the documentation installed as well:

    > make generate_docs
    > make qch_docs
    > sudo make install_qch_docs


Tested with gcc 4.8.5 20150623 on centos7
