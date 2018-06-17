---
layout: page
title: 如何安裝 Qt 相關文件
date: 2018-05-17 12:49:53 +0800
description: >
  如何安裝 Qt 相關文件
parent:
  title: qt
  url: '/read/subject/qt'
source_url: '/read/subject/qt/doc/install-qt5-doc-all.md'
---

## 操作步驟

只要執行下面指令，就會安裝Qt大部分的相關說明文件。

``` sh
$ sudo apt-get install qt5-doc qt5-doc-html
```

## 套件探索

執行

``` sh
$ apt-cache showsrc qt5-doc | grep '^Binary:' -B 3
```

顯示

```
Package: qtdoc-opensource-src
Format: 3.0 (quilt)
Binary: qt5-doc, qt5-doc-html
```


## Package

* [qt5-doc](https://packages.ubuntu.com/bionic/qt5-doc)
* [qt5-doc-html](https://packages.ubuntu.com/bionic/qt5-doc-html)


## Source Package

* [qtdoc-opensource-src](https://packages.ubuntu.com/source/bionic/qtdoc-opensource-src)

## 後續

接下來先來看「[安裝qt5-doc-html](install-qt5-doc-html)」的說明。
