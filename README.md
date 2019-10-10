# rtty([中文](/README_ZH.md))

[1]: https://img.shields.io/badge/license-MIT-brightgreen.svg?style=plastic
[2]: /LICENSE
[3]: https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=plastic
[4]: https://github.com/zhaojh329/rtty/pulls
[5]: https://img.shields.io/badge/Issues-welcome-brightgreen.svg?style=plastic
[6]: https://github.com/zhaojh329/rtty/issues/new
[7]: https://img.shields.io/badge/release-6.6.1-blue.svg?style=plastic
[8]: https://github.com/zhaojh329/rtty/releases
[9]: https://travis-ci.org/zhaojh329/rtty.svg?branch=master
[10]: https://travis-ci.org/zhaojh329/rtty

[![license][1]][2]
[![PRs Welcome][3]][4]
[![Issue Welcome][5]][6]
[![Release Version][7]][8]
[![Build Status][9]][10]

[Xterm.js]: https://github.com/xtermjs/xterm.js
[libev]: http://software.schmorp.de/pkg/libev.html
[openssl]: https://github.com/openssl/openssl
[mbedtls(polarssl)]: https://github.com/ARMmbed/mbedtls
[CyaSSl(wolfssl)]: https://github.com/wolfSSL/wolfssl
[vue]: https://github.com/vuejs/vue
[iview]: https://github.com/iview/iview
[server]: https://github.com/zhaojh329/rttys

![](https://raw.githubusercontent.com/zhaojh329/rtty/doc/rtty.png)
![](https://raw.githubusercontent.com/zhaojh329/rtty/doc/screen.gif)
![](https://raw.githubusercontent.com/zhaojh329/rtty/doc/file.gif)

It is composed of a client and a [server]. The client is written in pure C. The [server] is written in go language
and the front-end interface is written in [iview] & [Vue].

You can access your device's terminal from anywhere via the web. Differentiate your different device by device ID.

rtty is very suitable for remote maintenance your or your company's thousands of Linux devices deployed around
the world.

# Features
* Simple to deployment and easy to use
* Access different devices based on device ID
* Provide a dashboard to visualize online devices
* Fully-featured terminal based on [Xterm.js]
* Support transfer file
* SSL support: openssl, mbedtls, CyaSSl(wolfssl)
* Support device authorization
* Support Execute a command remote
* The client is very small, suitable for embedded Linux: rtty(20.1K) + libev(48.5K) = 68K. If you want
  to support ssl, +libwolfssl(595.9K) = 664K

# Dependencies of the Client side
* [libev] - A full-featured and high-performance event loop
* [mbedtls(polarssl)], [CyaSSl(wolfssl)] or [openssl] - If you want to support SSL

# [Deploying the server side](https://github.com/zhaojh329/rttys)

# How to install and run the Client - rtty
## For Linux distribution: Ubuntu, Debian, ArchLinux, Centos
Install

    wget -qO- https://raw.githubusercontent.com/zhaojh329/rtty/master/tools/install.sh | sudo bash

Command-line Options

    Usage: rtty [option]
      -I id        # Set an ID for the device(Maximum 63 bytes, valid character:letter,
                          number, underline and short line)
      -h host      # Server's host or ipaddr
      -p port      # Server port(Default is 5912)
      -a           # Auto reconnect to the server
      -v           # verbose
      -d           # Adding a description to the device(Maximum 126 bytes)
      -s           # SSL on
      -k keepalive # keep alive in seconds for this client. Defaults to 5
      -V           # Show version
      -D           # Run in the background
      -t token     # Authorization token

Run RTTY(Replace the following parameters with your own parameters)

    sudo rtty -I 'My-device-ID' -h 'your-server' -p 5912 -a -v -s -d 'My Device Description'

If your rttys is configured with a token, add the following parameter(Replace the following token with your own)

    -t 34762d07637276694b938d23f10d7164

## [For OpenWRT](/OPENWRT.md)

## [For Other Embedded Linux Platform](/CROSS_COMPILE.md)

# Usage
Use your web browser to access your server: `https://your-server-host:5912`, then click the connection button

You can easily embed RTTY into your existing platform: `https://your-server-host:5912/#/?id=your-id`

Automatic login: `https://your-server:5912/#/?id=device-id&username=device-username&password=device-password`

## Transfer file
Transfer file from local to remote device

	rtty -R

Transfer file from remote device to the local

	rtty -S test.txt

## [Execute command remotely](/COMMAND.md)

# [Donate](https://gitee.com/zhaojh329/rtty#project-donate-overview)

# Contributing
If you would like to help making [rtty](https://github.com/zhaojh329/rtty) better,
see the [CONTRIBUTING.md](https://github.com/zhaojh329/rtty/blob/master/CONTRIBUTING.md) file.

