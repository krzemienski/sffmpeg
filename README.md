# Static FFmpeg Build
`sffmpeg` is a simple cmake-based full-featured FFmpeg build helper.

It currently works on Linux and other POSIX systems (with a few tweaks). It has been tested the most heavily on Linux/x86_64
(Ubuntu 18.04).  The helper will grab the latest versions of most FFmpeg dependencies, providing a way to effectively build,
test and compare multiple builds of FFmpeg on the same host.

## Requirements
`sffmpeg` requires:

- a POSIX-compliant system (virtually any system today).
- a recent version of [gcc](http://gcc.gnu.org/).
- a recent version of [cmake](http://www.cmake.org/) (3.0+).
- the [autoconf](http://www.gnu.org/software/autoconf/) and [libtool](http://www.gnu.org/software/libtool/) utilities.
- the [pkg-config](http://www.freedesktop.org/wiki/Software/pkg-config) utility.

## Usage
Just type the following commands at the shell prompt:

    $ git clone https://github.com/pyke369/sffmpeg
    $ cd sffmpeg
    $ make

Then go grab a coffee (or maybe ten). The helper will compile all FFmpeg dependencies for you. Once done, you should get an
FFmpeg binary in the `build/bin` directory (with all dependencies statically linked-in).
```
$ build/bin/ffmpeg
ffmpeg version 4.2.2 Copyright (c) 2000-2019 the FFmpeg developers
  libavutil      56. 31.100 / 56. 31.100
  libavcodec     58. 54.100 / 58. 54.100
  libavformat    58. 29.100 / 58. 29.100
  libavdevice    58.  8.100 / 58.  8.100
  libavfilter     7. 57.100 /  7. 57.100
  libswscale      5.  5.100 /  5.  5.100
  libswresample   3.  5.100 /  3.  5.100
  libpostproc    55.  5.100 / 55.  5.100
Hyper fast Audio and Video encoder
usage: ffmpeg [options] [[infile options] -i infile]... {[outfile options] outfile}...
```
From there, you may use the binary immediately or build a Debian package for later deployment (see below).

## Packaging
(requires devscripts package)

You may optionally build a Debian package by typing the following command at the shell prompt:
```
$ make deb
```

The `ffmpeg`, `ffprobe` and `frmxtract` binaries will be installed by the package in the `/usr/bin` directory.
```
$ sudo dpkg -i ../sffmpeg_4.2.2_amd64.deb
Selecting previously unselected package sffmpeg.
Unpacking sffmpeg (4.2.2) ...
Setting up sffmpeg (4.2.2) ...
```
