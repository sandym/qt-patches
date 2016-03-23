Building openssl on Windows
===========================

## Preparation

Start the appropriate VS Command Prompt
(VS2015 x86 Native Tools Command Prompt, etc). VS2010, VS2012,
VS2013 and VS2015, 32 or 64 bits should work.

Remove cygwin from PATH if needed.

    > set PATH=%PATH:C:\cygwin\bin;=%

We need perl:

    > set PATH=C:\Qt\Perl64\bin;%PATH%

If you need Windows XP support, set those:

    > set INCLUDE=%ProgramFiles(x86)%\Microsoft SDKs\Windows\v7.1A\Include;%INCLUDE%
    > set LIB=%ProgramFiles(x86)%\Microsoft SDKs\Windows\v7.1A\Lib;%LIB%
    > set PATH=%ProgramFiles(x86)%\Microsoft SDKs\Windows\v7.1A\Bin;%PATH%
    > set CL=/D_USING_V110_SDK71_

## Building

Extract the latest openssl source and build:

    > cd openssl-src-folder
    > perl Configure VC-WIN32 no-asm --prefix=C:\Qt\VS2015\openssl
    > ms\do_ms
    > nmake -f ms\ntdll.mak
    > nmake -f ms\ntdll.mak install

Or if you build for Windows 64 bits:

    > cd openssl-src-folder
    > perl Configure VC-WIN64A no-asm --prefix=C:\Qt\VS2015x64\openssl
    > ms\do_win64a
    > nmake -f ms\ntdll.mak
    > nmake -f ms\ntdll.mak install

Adjust the install prefix to your convinience. I use the
following hierarchy:
* c:\Qt
   * VS2010
    * openssl
   * VS2010x64
    * openssl
   * VS2012
    * openssl
   * etc


Tested with VS2010, VS2012, VS2013 and VS2015, 32 and 64 bits.
