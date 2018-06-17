---
layout: page
title: 如何安裝 Qt 相關文件 (HTML版)
date: 2018-05-17 12:49:53 +0800
description: >
  如何安裝 Qt 相關文件 (HTML版)
parent:
  title: qt
  url: '/read/subject/qt'
source_url: '/read/subject/qt/doc/install-qt5-doc-html.md'
---


## 操作步驟

只要執行下面指令，就會安裝Qt大部分的相關說明文件(HTML版)。

``` sh
$ sudo apt-get install qt5-doc-html
```

## 觀看文件首頁

執行

``` sh
$ dpkg -L qt5-doc-html | grep index.html
```

顯示

```
/usr/share/qt5/doc/qtdoc/index.html
```

所以可以執行下面指令，觀看文件首頁

``` sh
$ firefox /usr/share/qt5/doc/qtdoc/index.html
```

或是也可以濃縮成一行，直接執行下面指令

``` sh
$ firefox $(dpkg -L qt5-doc-html | grep index.html)
```

首頁的內容類似於「[http://doc.qt.io/qt-5/](http://doc.qt.io/qt-5/)」這一頁。

## topics

執行

``` sh
$ dpkg -L qt5-doc-html | grep topics
```

顯示

``` sh
/usr/share/qt5/doc/qtdoc/topics-app-development.html
/usr/share/qt5/doc/qtdoc/topics-core.html
/usr/share/qt5/doc/qtdoc/topics-data-storage.html
/usr/share/qt5/doc/qtdoc/topics-graphics.html
/usr/share/qt5/doc/qtdoc/topics-network-connectivity.html
/usr/share/qt5/doc/qtdoc/topics-scripting.html
/usr/share/qt5/doc/qtdoc/topics-ui.html
/usr/share/qt5/doc/qtdoc/topics-web-content.html
```

上面的頁面，可以對應到網路上的文件網址

* [http://doc.qt.io/qt-5/topics-app-development.html](http://doc.qt.io/qt-5/topics-app-development.html)
* [http://doc.qt.io/qt-5/topics-core.html](http://doc.qt.io/qt-5/topics-core.html)
* [http://doc.qt.io/qt-5/topics-data-storage.html](http://doc.qt.io/qt-5/topics-data-storage.html)
* [http://doc.qt.io/qt-5/topics-graphics.html](http://doc.qt.io/qt-5/topics-graphics.html)
* [http://doc.qt.io/qt-5/topics-network-connectivity.html](http://doc.qt.io/qt-5/topics-network-connectivity.html)
* [http://doc.qt.io/qt-5/topics-scripting.html](http://doc.qt.io/qt-5/topics-scripting.html)
* [http://doc.qt.io/qt-5/topics-ui.html](http://doc.qt.io/qt-5/topics-ui.html)
* [http://doc.qt.io/qt-5/topics-web-content.html](http://doc.qt.io/qt-5/topics-web-content.html)


## index.html

執行

``` sh
$ dpkg -L qtbase5-doc-html | grep '\-index.html'
```

顯示

```
/usr/share/qt5/doc/qtconcurrent/qtconcurrent-index.html
/usr/share/qt5/doc/qtcore/qtcore-index.html
/usr/share/qt5/doc/qtdbus/qtdbus-index.html
/usr/share/qt5/doc/qtgui/qtgui-index.html
/usr/share/qt5/doc/qtnetwork/qtnetwork-index.html
/usr/share/qt5/doc/qtopengl/qtopengl-index.html
/usr/share/qt5/doc/qtplatformheaders/qtplatformheaders-index.html
/usr/share/qt5/doc/qtprintsupport/qtprintsupport-index.html
/usr/share/qt5/doc/qtsql/qtsql-index.html
/usr/share/qt5/doc/qttestlib/qttest-index.html
/usr/share/qt5/doc/qtwidgets/qtwidgets-index.html
/usr/share/qt5/doc/qtxml/qtxml-index.html
```

上面的頁面，可以對應到網路上的文件網址

* [http://doc.qt.io/qt-5/qtconcurrent-index.html](http://doc.qt.io/qt-5/qtconcurrent-index.html)
* [http://doc.qt.io/qt-5/qtcore-index.html](http://doc.qt.io/qt-5/qtcore-index.html)
* [http://doc.qt.io/qt-5/qtdbus-index.html](http://doc.qt.io/qt-5/qtdbus-index.html)
* [http://doc.qt.io/qt-5/qtgui-index.html](http://doc.qt.io/qt-5/qtgui-index.html)
* [http://doc.qt.io/qt-5/qtnetwork-index.html](http://doc.qt.io/qt-5/qtnetwork-index.html)
* [http://doc.qt.io/qt-5/qtopengl-index.html](http://doc.qt.io/qt-5/qtopengl-index.html)
* [http://doc.qt.io/qt-5/qtplatformheaders-index.html](http://doc.qt.io/qt-5/qtplatformheaders-index.html)
* [http://doc.qt.io/qt-5/qtprintsupport-index.html](http://doc.qt.io/qt-5/qtprintsupport-index.html)
* [http://doc.qt.io/qt-5/qtsql-index.html](http://doc.qt.io/qt-5/qtsql-index.html)
* [http://doc.qt.io/qt-5/qttest-index.html](http://doc.qt.io/qt-5/qttest-index.html)
* [http://doc.qt.io/qt-5/qtwidgets-index.html](http://doc.qt.io/qt-5/qtwidgets-index.html)
* [http://doc.qt.io/qt-5/qtxml-index.html](http://doc.qt.io/qt-5/qtxml-index.html)


## 閱讀入門

建議可以先從「/usr/share/qt5/doc/qtwidgets/qtwidgets-index.html」閱讀起。

執行下面指令

``` sh
$ dpkg -L qtbase5-doc-html | grep index.html | grep qtwidgets
```

顯示

```
/usr/share/qt5/doc/qtwidgets/qtwidgets-index.html
```

執行

``` sh
$ firefox /usr/share/qt5/doc/qtwidgets/qtwidgets-index.html
```

或是執行

``` sh
$ firefox $(dpkg -L qtbase5-doc-html | grep index.html | grep qtwidgets)
```

## tutorial.html

執行

``` sh
$ dpkg -L qtbase5-doc-html | grep '\-tutorial.html'
```

顯示

```
/usr/share/qt5/doc/qmake/qmake-tutorial.html
/usr/share/qt5/doc/qttestlib/qtest-tutorial.html
/usr/share/qt5/doc/qtwidgets/widgets-tutorial.html
```

上面的頁面，可以對應到網路上的文件網址

* [http://doc.qt.io/qt-5/qmake-tutorial.html](http://doc.qt.io/qt-5/qmake-tutorial.html)
* [http://doc.qt.io/qt-5/qtest-tutorial.html](http://doc.qt.io/qt-5/qtest-tutorial.html)
* [http://doc.qt.io/qt-5/widgets-tutorial.html](http://doc.qt.io/qt-5/widgets-tutorial.html)

執行

``` sh
$ firefox $(dpkg -L qtbase5-doc-html | grep tutorial.html | grep qtwidgets)
```

## manual

執行

``` sh
$ dpkg -L qtbase5-doc-html | grep '\-manual.html'
```

顯示

``` sh
/usr/share/qt5/doc/qmake/qmake-manual.html
```

上面的頁面，可以對應到網路上的文件網址

* [http://doc.qt.io/qt-5/qmake-manual.html](http://doc.qt.io/qt-5/qmake-manual.html)

執行

``` sh
$ firefox $(dpkg -L qtbase5-doc-html | grep '\-manual.html' | grep qmake)
```

除了上面建議，可以先從「/usr/share/qt5/doc/qtwidgets/qtwidgets-index.html」閱讀起。

入門時，也建議閱讀「/usr/share/qt5/doc/qmake/qmake-manual.html」，初步了解「[qmake](http://doc.qt.io/qt-5/qmake-running.html)」的用法。
