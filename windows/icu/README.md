Building icu on Windows
=======================

## Preparation

Start the appropriate VS Command Prompt
(VS2015 x86 Native Tools Command Prompt, etc). VS2010, VS2012,
VS2013 and VS2015, 32 or 64 bits should work.

You need cygwin in the PATH.

    > set PATH=%PATH%;C:\cygwin64\bin;

If you need Windows XP support, set those:

    > set INCLUDE=%ProgramFiles(x86)%\Microsoft SDKs\Windows\v7.1A\Include;%INCLUDE%
    > set LIB=%ProgramFiles(x86)%\Microsoft SDKs\Windows\v7.1A\Lib;%LIB%
    > set PATH=%ProgramFiles(x86)%\Microsoft SDKs\Windows\v7.1A\Bin;%PATH%
    > set CL=/D_USING_V110_SDK71_

## Building

Extract the latest icu source and build:

    > cd icu/source
    > chmod +x configure
    > bash ./runConfigureICU Cygwin/MSVC --prefix=C:/Qt/VS2015/icu
    > make
    > make install

Adjust the install prefix to your convinience. I use the
following hierarchy:
* c:\Qt
   * VS2010
    * icu
   * VS2010x64
    * icu
   * VS2012
    * icu
   * etc


Tested with VS2010, VS2012, VS2013 and VS2015, 32 and 64 bits.
