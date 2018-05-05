---
layout: page
title: 如何安裝 lxqt
date: 2018-05-05 13:31:55 +0800
description: >
  如何安裝 lxqt
parent:
  title: lxqt
  url: '/read/subject/lxqt'
source_url: '/read/subject/lxqt/install-lxqt.md'
---


## 相關腳本

* play-ubuntu-18.04-plan/prototype/de-basic/[play-lxqt](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/prototype/de-basic/play-lxqt)
* play-ubuntu-18.04-plan/plan/de-basic/[play-lxqt](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/plan/de-basic/play-lxqt)


## 安裝操作步驟

執行下面指令，安裝「[lxqt](https://packages.ubuntu.com/bionic/lxqt)」這個「[Metapackage](https://help.ubuntu.com/community/MetaPackages)」。

``` sh
$ sudo apt-get install lxqt
```


然後我採用的是「[xfwm4](http://manpages.ubuntu.com/manpages/bionic/en/man1/xfwm4.1.html)」，當做「Window Manager」，這是在「17.10」學到的經驗。

所以執行下面的指令安裝「[xfwm4](https://packages.ubuntu.com/bionic/xfwm4)」這個套件。


``` sh
$ sudo apt-get install xfwm4
```

然後重新登入，登入的「Session」要選擇「LXQt-Desktop」。

然後一開始使用「lxqt」，會讓您選擇要採用的「[Window Manager](https://en.wikipedia.org/wiki/Window_manager)」，這時候就可以選擇「[xfwm4](http://manpages.ubuntu.com/manpages/bionic/en/man1/xfwm4.1.html)」。

或是事先也可以先寫好設定檔，

設定檔的路徑是「~/.config/lxqt/session.conf」，可以參考「[這裡](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/de-basic/play-lxqt/config/lxqt/session.conf#L4)」和「[這裡](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/plan/de-basic/play-lxqt/prj/play-lxqt/app/usr/share/play-lxqt/sub/on/lxqt/conf/set/session.conf#L4)」

主要其中有一行如下

```
window_manager=xfwm4
```

未來登入桌面環境後，也可以透過圖形界面工具來設定，

也就是可以透過「[lxqt-config-session](http://manpages.ubuntu.com/manpages/bionic/en/man1/lxqt-config-session.1.html)」，可以直接在「[Terminal](https://help.ubuntu.com/community/UsingTheTerminal)」打指令來啟動這個工具，

也可以在開始選單的「Preferences / LXQt settings」找到「Session Settions」，點選這個選項，就可以啟動這個工具。

這個啟動圖示，可以參考「/usr/share/applications/lxqt-config-session.desktop」。

執行下面指令，就可以找到相關的路徑

``` sh
$ dpkg -L lxqt-session | grep lxqt-config-session
```

顯示

```
/usr/bin/lxqt-config-session
/usr/share/applications/lxqt-config-session.desktop
/usr/share/man/man1/lxqt-config-session.1.gz
```
