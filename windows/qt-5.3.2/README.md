
Building Qt-5.3.2 on Windows
============================

### Preparation

Get the source code zip, decompress it and rename the directory
to qt-src-5.3.2.

Start the appropriate VS Command Prompt
(VS2015 x86 Native Tools Command Prompt, etc). VS2010, VS2012,
VS2013 and VS2015, 32 or 64 bits should work.

Remove cygwin from PATH if needed.

    > set PATH=%PATH:C:\cygwin\bin;=%

We need perl, python and ruby:

    > set PATH=C:\Qt\Perl64\bin;%PATH%
    > set PATH=C:\Qt\Python27;%PATH%
    > set PATH=C:\Qt\Ruby193\bin;%PATH%

If you need Windows XP support, set those:

    > set INCLUDE=%ProgramFiles(x86)%\Microsoft SDKs\Windows\v7.1A\Include;%INCLUDE%
    > set LIB=%ProgramFiles(x86)%\Microsoft SDKs\Windows\v7.1A\Lib;%LIB%
    > set PATH=%ProgramFiles(x86)%\Microsoft SDKs\Windows\v7.1A\Bin;%PATH%
    > set CL=/D_USING_V110_SDK71_

Setup openssl include path (see openssl readme to build):

    > set INCLUDE=C:\Qt\VS2015\openssl\include;%INCLUDE%

Setup icu paths (see icu readme to build):

    > set PATH=C:\Qt\VS2015\icu\bin;%PATH%
    > set PATH=C:\Qt\VS2015\icu\lib;%PATH%
    > set INCLUDE=C:\Qt\VS2015\icu\include;%INCLUDE%
    > set LIB=C:\Qt\VS2015\icu\lib;%LIB%

Adjust the path to icu and openssl to match your version of MSVC.

Add some qt tools:

    > set PATH=C:\Qt\qt-src-5.3.2\gnuwin32\bin;%PATH%

### Building

Configure and compile:

    > mkdir C:\Qt\qt-build-5.3.2
    > cd C:\Qt\qt-build-5.3.2
    > ..\qt-src-5.3.2\configure.bat -icu -debug-and-release -nomake examples -prefix c:\Qt\VS2015\qt-5.3.2 -platform win32-msvc2015 -force-debug-info
    > jom
    > jom install

Add '-target xp' to the configure line if you want Windows XP support. Adjust the install path and platform to match your versin of MSVC.

If you need the documentation installed:

    > jom generate_docs
    > jom qch_docs
    > jom install_qch_docs

Done!

Tested with VS2012, VS2013, VS2015.
