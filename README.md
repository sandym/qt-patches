qt-patches
==========

All my build recipes and patches for the Qt versions I
used over the years.

Interresting versions:

* Qt 4.8.7: the last Qt 4 release
* Qt 5.3.2: the last release to support Mac OS X 10.6
* Qt 5.5.1: the last release to have QtWebKit
* Qt 5.6.0: the latest

## Windows

I use the following hierarchy to build the different versions
and their dependencies:
* c:\Qt
   * VS2010
   * VS2010x64
   * VS2012
   * VS2012x64
   * VS2013
   * VS2013x64
   * VS2015
   * VS2015x64

In each of them I have:
* icu
* openssl
* qt-{version}  (qt-5.3.2, qt-5.5.1, etc)

## Mac

I build Qt in /usr/local (/usr/local/Qt-4.8.7, /usr/local/Qt-5.3.2, etc).