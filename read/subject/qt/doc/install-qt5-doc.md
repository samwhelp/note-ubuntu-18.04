---
layout: page
title: 如何安裝 Qt 相關文件 (qch版)
date: 2018-05-17 12:49:53 +0800
description: >
  如何安裝 Qt 相關文件 (qch版)
parent:
  title: qt
  url: '/read/subject/qt'
source_url: '/read/subject/qt/doc/install-qt5-doc.md'
---


## 操作步驟

只要執行下面指令，就會安裝Qt大部分的相關說明文件(qch版)。

``` sh
$ sudo apt-get install qt5-doc
```

然後就可以透過「[Qt Assistant](url=http://doc.qt.io/qt-5/qtassistant-index.html)」來觀看文件。

套件是「[qt5-assistant](https://packages.ubuntu.com/bionic/qt5-assistant)」。

指令是「assistant」，路徑在「/usr/lib/qt5/bin/assistant」，並且可以透過「qtchooser」來呼叫。

而「Desktop Entry」的路徑，則是在「/usr/share/applications/assistant-qt5.desktop」。
