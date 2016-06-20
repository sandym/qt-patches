
Building Qt-5.6.1 x64 on ubuntu
===============================

Dependencies: This is the list of all development package I have installed, a subset of it might be enough but I don't know which one... Install what you need.

    > sudo apt-get install libao-dev libasound2-dev libatk1.0-dev libaudio-dev libbison-dev libbz2-dev libcairo2-dev libcups2-dev libdbus-1-dev libdmx-dev libdrm-dev libexpat1-dev libfontconfig1-dev libfontenc-dev libfreetype6-dev libgdk-pixbuf2.0-dev libgl1-mesa-dev libglib2.0-dev libgstreamer-plugins-base0.10-dev libgstreamer0.10-dev libgtk2.0-dev libharfbuzz-dev libice-dev libicu-dev libinput-dev libltdl-dev libpango1.0-dev libpcre3-dev libpixman-1-dev libpng12-dev libproxy-dev libpthread-stubs0-dev libpulse-dev libsm-dev libssl-dev libudev-dev libx11-dev libx11-xcb-dev libxau-dev libxcb-composite0-dev libxcb-damage0-dev libxcb-dri2-0-dev libxcb-dri3-dev libxcb-glx0-dev libxcb-icccm4-dev libxcb-image0-dev libxcb-keysyms1-dev libxcb-present-dev libxcb-randr0-dev libxcb-record0-dev libxcb-render-util0-dev libxcb-render0-dev libxcb-res0-dev libxcb-shape0-dev libxcb-shm0-dev libxcb-sync-dev libxcb-util-dev libxcb-util0-dev libxcb-xevie0-dev libxcb-xfixes0-dev libxcb-xinerama0-dev libxcb-xkb-dev libxcb-xv0-dev libxcb-xvmc0-dev libxcb1-dev libxcomposite-dev libxcursor-dev libxdamage-dev libxdmcp-dev libxext-dev libxfixes-dev libxfont-dev libxft-dev libxi-dev libxinerama-dev libxkbcommon-dev libxkbcommon-x11-dev libxkbfile-dev libxml2-dev libxmu-dev libxpm-dev libxrandr-dev libxrender-dev libxshmfence-dev libxt-dev libxv-dev libxxf86vm-dev mesa-common-dev x11proto-bigreqs-dev x11proto-composite-dev x11proto-core-dev x11proto-damage-dev x11proto-dmx-dev x11proto-dri2-dev x11proto-fixes-dev x11proto-fonts-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-resource-dev x11proto-video-dev x11proto-xext-dev x11proto-xf86vidmode-dev x11proto-xinerama-dev xtrans-dev zlib1g-dev

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


Tested with gcc 5.3.1 20160413 on ubuntu 16.04
