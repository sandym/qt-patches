Building Qt-4.8.7 on Windows
============================

###Preparation

Get the source code zip, decompress it and rename the directory
to qt-src-4.8.7.

Apply the patch. It fixes compile errors with VS2015.

    > cd  qt-src-4.8.7
	> patch -p1 < ../qt-patches/windows/qt-4.8.7/qt-4.8.7-win.patch
	> cd ..

Start the appropriate VS Command Prompt
(VS2015 x86 Native Tools Command Prompt, etc). VS2010, VS2012,
VS2013 and VS2015, 32 or 64 bits should work.

Remove cygwin from PATH if needed.

    > set PATH=%PATH:C:\cygwin\bin;=%

We need perl:

    > set PATH=C:\Qt\Perl64\bin;%PATH%

Setup openssl include path (see openssl readme to build):

    > set INCLUDE=C:\Qt\VS2015\openssl\include;%INCLUDE%

If you need Windows XP support, set those:

    > set INCLUDE=%ProgramFiles(x86)%\Microsoft SDKs\Windows\v7.1A\Include;%INCLUDE%
    > set LIB=%ProgramFiles(x86)%\Microsoft SDKs\Windows\v7.1A\Lib;%LIB%
    > set PATH=%ProgramFiles(x86)%\Microsoft SDKs\Windows\v7.1A\Bin;%PATH%
    > set CL=/D_USING_V110_SDK71_

I tested WinXP builds with VS2010 and VS2013 only.

Set a directory for the build and configure

    > mkdir C:\Qt\qt-build-4.8.7
    > cd C:\Qt\qt-build-4.8.7
    > ..\qt-src-4.8.7\configure.exe -prefix C:\Qt\VS2015\qt-4.8.7 \
      -debug-and-release -no-qt3support -no-multimedia \
      -no-audio-backend -no-phonon -no-phonon-backend -no-libtiff \
      -no-libmng -no-dbus -no-nis -webkit -platform win32-msvc2015

Adjust the install path and the platform to suit your needs.

Tested with VS2010 and VS2015, 32 and 64 bits.