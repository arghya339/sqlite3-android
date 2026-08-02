SQLite package build workflow
---
[![Build workflow](../../actions/workflows/build.yml/badge.svg)](../../actions/workflows/build.yml)

This repository contains a workflow to build the sqlite binaries for Android.

[Termux](https://github.com/termux/termux-app/releases/)
---
```sh
curl -L --progress-bar -C - -o ~/sqlite3 "https://raw.githubusercontent.com/arghya339/sqlite3-android/refs/heads/master/binary/$(getprop ro.product.cpu.abi)/sqlite3" && chmod +x ~/sqlite3 && ~/sqlite3 --version && rm -f ~/sqlite3
```

Overview
--------
Makefile and Android.mk necessary to compile sqlite3 for Android.

Requirements
------------
* aria2c (or wget). Replace URL_DOWNLOADER variable in Makefile for other downloader.
* Android NDK

Build
-----
Install/extract the [Android NDK](https://developer.android.com/ndk/downloads/index.html) then:

    PATH=/path/to/ndk/dir:$PATH
    cd sqlite3-android
    make

By default, it will build binaries for armeabi-v7. To build for other arch, replace the TARGET_ABI variable in Makefile.

Available ABIS:

armeabi (Deprecated in Android NDK r16. Will be removed in Android NDK r17)

armeabi-v7a

arm64-v8a

x86

x86_64
