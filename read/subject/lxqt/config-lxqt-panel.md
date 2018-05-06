---
layout: page
title: 如何設定 lxqt-panel
date: 2018-05-06 07:50:35 +0800
description: >
  如何設定 lxqt-panel
parent:
  title: lxqt
  url: '/read/subject/lxqt'
source_url: '/read/subject/lxqt/config-lxqt-panel.md'
---


## 相關腳本

* play-ubuntu-18.04-plan/prototype/de-basic/[play-lxqt](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/prototype/de-basic/play-lxqt)
* play-ubuntu-18.04-plan/plan/de-basic/[play-lxqt](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/plan/de-basic/play-lxqt)


## 操作步驟

一開始使用「lxqt」，預設的背景顏色是黑色的，

然後「panel」也沒有任何「widget」，

而「panel」一開始是放在最下方，可以將滑鼠游標移到最下方，按下滑鼠右鍵，會出現一個選單

可以選擇「Configure Panel」，就會出現另一個設定視窗。

可以在「Widgets」那個頁簽，加入「Widget」。

或是也可以事先編輯「~/.config/lxqt/panel.conf」這個設定檔。

可以參考「[這裡](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/de-basic/play-lxqt/config/lxqt/panel.conf)」和「[這裡](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/plan/de-basic/play-lxqt/prj/play-lxqt/app/usr/share/play-lxqt/sub/on/lxqt/conf/set/panel.conf)」。

或是也可以參考「/usr/share/lxqt/panel.conf」

執行下面指令，就可以找到路徑

``` sh
$ dpkg -L lxqt-panel | grep conf
```

顯示

```
/usr/share/lxqt/panel.conf
```


## 相關 manpage

* man [lxqt-panel](http://manpages.ubuntu.com/manpages/bionic/en/man1/lxqt-panel.1.html)


## 相關套件

* [lxqt-panel](https://packages.ubuntu.com/bionic/lxqt-panel)
