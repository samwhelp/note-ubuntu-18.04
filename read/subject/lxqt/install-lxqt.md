---
layout: page
title: 如何安裝 lxqt
date: 2018-05-05 13:31:55 +0800
description: >
  如何安裝 lxqt
parent:
  title: lxqt
  url: '/read/subject/lxqt'
source_url: '/read/subject/lxqt/index.md'
---


## 相關腳本

* play-ubuntu-18.04-plan/prototype/de-basic/[play-lxqt](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/prototype/de-basic/play-lxqt)
* play-ubuntu-18.04-plan/plan/de-basic/[play-lxqt](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/plan/de-basic/play-lxqt)


## 安裝操作步驟

執行下面指令，安裝「[lxqt](https://packages.ubuntu.com/bionic/lxqt)」這個「[Metapackage](https://help.ubuntu.com/community/MetaPackages)」。

``` sh
$ sudo apt-get install lxqt
```


然後我採用的是「xfwm4」，當做「Window Manager」，這是在「17.10」學到的經驗。

所以執行下面的指令安裝「[xfwm4](https://packages.ubuntu.com/bionic/xfwm4)」這個套件。


``` sh
$ sudo apt-get install xfwm4
```

然後重新登入，登入的「Session」要選擇「LXQt-Desktop」。

然後一開始使用「lxqt」，會讓您選擇要採用的「Window Manager」，這時候就可以選擇「xfwm4」。

或是事先也可以先寫好設定檔，

設定檔的路徑是「~/.config/lxqt/session.conf」，可以參考「[這裡](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/de-basic/play-lxqt/config/lxqt/session.conf#L4)」和「[這裡](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/plan/de-basic/play-lxqt/prj/play-lxqt/app/usr/share/play-lxqt/sub/on/lxqt/conf/set/session.conf#L4)」

主要其中有一行如下

```
window_manager=xfwm4
```
