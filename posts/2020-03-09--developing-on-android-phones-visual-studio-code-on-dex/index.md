---
permalink: "/developing-on-android-phones-visual-studio-code-on-dex/"
cover: img.jpg
title: "Developing on Android phones, Visual Studio Code on DeX"
description: "As you may have seen from some of my previous articles I like doing software development through my phone. These instructions work in regular android but I am using Samsung DeX to get a full desktop experience because having a full keyboard and mouse works well for me."
category: Samsung Internet
img: https://miro.medium.com/max/1200/1*tY0IS5y4HxT_eO45h5-ZPw.png
author: Ada Rose Cannon
authorImg: https://miro.medium.com/fit/c/96/96/1*Dn8pr_cbYLtc_KfmUNhnBA.png
tags: [Samsung Internet, Visual Studio Code, Vscode, Web Development, Terminal]
---

# Developing on Android phones, Visual Studio Code on DeX



As you may have seen from some of my previous articles I like doing software development through my phone. These instructions work in regular android but I am using Samsung DeX to get a full desktop experience because having a full keyboard and mouse works well for me.

The trick here is to run a Ubuntu in an Android App called [Termux,](https://termux.com/) then in that run [Visual Studio code as a local Web Server](https://github.com/cdr/code-server/releases), where it is available as a Progressive Web App, installable from a localhost URL.

### Step by step guide

1. Install [Termux](https://termux.com/)

1. Set up Ubuntu in Termux, follow these instructions: [https://wiki.termux.com/wiki/Ubuntu](https://wiki.termux.com/wiki/Ubuntu)

1. Download and Extract [code-server](https://github.com/cdr/code-server/releases) for ARM64

    wget [https://github.com/cdr/code-server/releases/download/2.1698/code-server2.1698-vsc1.41.1-linux-arm64.tar.gz](https://github.com/cdr/code-server/releases/download/2.1698/code-server2.1698-vsc1.41.1-linux-arm64.tar.gz)

    tar -xvf ./[code-server2.1698-vsc1.41.1-linux-arm64.tar.gz](https://github.com/cdr/code-server/releases/download/2.1698/code-server2.1698-vsc1.41.1-linux-arm64.tar.gz)

    rm ./[code-server2.1698-vsc1.41.1-linux-arm64.tar.gz](https://github.com/cdr/code-server/releases/download/2.1698/code-server2.1698-vsc1.41.1-linux-arm64.tar.gz)

    cp ./[code-server2.1698-vsc1.41.1-linux-arm64](https://github.com/cdr/code-server/releases/download/2.1698/code-server2.1698-vsc1.41.1-linux-arm64.tar.gz)/code-server /bin

4. start code-server with code-server , copy the passcode it generates

5. Open localhost:8080 in the browser and paste the passcode generated in the terminal

6. Install as a progressive Web App

![Press ‘Add page to’](https://cdn-images-1.medium.com/max/2000/1*jZuxF4x0cdF1Jt1czVBJkg.png)*Press ‘Add page to’*

![Press ‘Home screen’](https://cdn-images-1.medium.com/max/2000/1*PBVksLkWZis2zLDLpq1qCQ.png)*Press ‘Home screen’*

### Note

In the future the code-server maintainers will stop releasing it as a single binary but as loose files. In which case move the whole folder to/lib/code-server then create a symlink to the binary in /lib/code-server from /bin .

Thanks for Reading!

![This is for the article’s preview image!](https://cdn-images-1.medium.com/max/3840/1*tY0IS5y4HxT_eO45h5-ZPw.png)*This is for the article’s preview image!*



By Ada Rose Cannon on March 9, 2020.

[Canonical link](https://medium.com/samsung-internet-dev/developing-on-android-phones-visual-studio-code-on-dex-4c99d2e80e91)
