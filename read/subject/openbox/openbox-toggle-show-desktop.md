---
layout: page
title: Openbox Toggle Show Desktop
date: 2020-02-06 16:13:45 +0800
description: >
  Openbox Toggle Show Desktop
parent:
  title: openbox
  url: '/read/subject/openbox'
source_url: '/read/subject/openbox/openbox-toggle-show-desktop.md'
---


## 設定顯示桌面

Openbox設定「顯示桌面」，有下面幾種方式

* 滑鼠按鍵綁定
* 鍵盤按鍵綁定
* xdotool
* wmctrl

Openbox內建有提供一個動作「[ToggleShowDesktop](http://openbox.org/wiki/Help:Actions#ToggleShowDesktop)」可以設定，所以可以用來設定在「滑鼠按鍵綁定」和「鍵盤按鍵綁定」。

## 滑鼠按鍵綁定

我綁定，在「桌面」按下「滑鼠左鍵」，就會執行「[ToggleShowDesktop](http://openbox.org/wiki/Help:Actions#ToggleShowDesktop)」這個動作。

設定範例如下

```
<mouse>
	<context name="Root">

		<!-- Mouse Button Left Click //-->
		<mousebind button="Left" action="Press">
			<action name="ToggleShowDesktop"/>
		</mousebind>

	</context>
</mouse>
```

可以參考我的「[設定樣本](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/de-box/play-openbox/config/openbox/openbox-gen-rc/Section/Mousebind/Root.php)」和「[rc.xml](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/de-box/play-openbox/config/openbox/rc.xml)」。

或是參考我的「[文件導引](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/de-box/play-openbox/spec-mousebind.md#on-desktop)」。

做了這樣的設定之後，可以有幾個「配套措施」。

* Openbox設定「[Margins](http://openbox.org/wiki/Help:Configuration#Margins)」。
* Panel設定「寬度」不佔滿，例如可以設定「[85%](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/de-box/play-openbox/config/tint2/tint2rc#L81)」。

這樣在畫面上，就會有「縫隙」，可以在「桌面」按下「滑鼠左鍵」。

Openbox設定「[Margins](http://openbox.org/wiki/Help:Configuration#Margins)」，可以參考我的「[設定樣本](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/de-box/play-openbox/config/openbox/openbox-gen-rc/Section/Margins.php)」。

而Panel，有很多選項可以選擇搭配的，像是「lxqt-panel」，「tint2」等等，

或是也可以搭配「cairo-dock」。

我是搭配「tint2」，除了剛剛講到的「寬度」設定「[85%](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/de-box/play-openbox/config/tint2/tint2rc#L81)」，
「tint2」還有一個特別的設計，

在「圖形界面程式(tint2conf)」有一個選項在「Panel」那個「頁籤」，

有一個「Window manager interaction / Forward mouse events」選項，

這個選項，需要勾選。

只要有勾選，就可以在「[tint2rc](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/de-box/play-openbox/config/tint2/tint2rc#L85)」找到如下的設定

```
wm_menu = 1
```

這樣在「tint2 Panel」一些區域，若是沒有綁定「滑鼠左鍵」，

則會執行「Openbox桌面滑鼠左鍵的功能」，

例如：

在「tint2 Desktop」那個「區域」，

在「tint2 Taskbar」的「非Task區域」，

在「tint2 DateTime」那個「區域」，

在這幾個區域，按下「滑鼠左鍵」，就會執行「Openbox桌面滑鼠左鍵的功能」。


相關的說明可以執行「$ man [tint2](http://manpages.ubuntu.com/manpages/bionic/en/man1/tint2.1.html)」，然後以「wm_menu」當關鍵字找尋，

例如，執行下面指令

``` sh
$ man tint2 | grep 'wm_menu' -A 2
```

可以找到如下的說明

```
              · wm_menu = boolean (0 or 1) : Defines if tint2 forwards unhandled mouse events to your window manager. Useful
                for window managers such as openbox, which display the start menu if you right click on the desktop.

--
              * none : If wm_menu = 1 is set, the mouse event is forwarded to the window manager. Otherwise it  is  ignored.
              * close : close the task * toggle : toggle the task * iconify : iconify (minimize) the task * toggle_iconify :
              toggle or iconify the task * maximize_restore : maximized or minimized the task * shade :  shades  (collapses)

```



## 鍵盤按鍵綁定

除了上面「滑鼠按鍵綁定」的設定，也可以設定「鍵盤按鍵綁定」，

例如，設定「Win + d」，就會執行「[ToggleShowDesktop](http://openbox.org/wiki/Help:Actions#ToggleShowDesktop)」這個動作。

設定範例如下

```
<keyboard>
	<keybind key="W-d">
		<action name="ToggleShowDesktop"/>
	</keybind>
</keyboard>
```

可以參考我的「[設定樣本](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/de-box/play-openbox/config/openbox/openbox-gen-rc/Section/Keybind/ToggleShowDesktop.php)」和「[rc.xml](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/de-box/play-openbox/config/openbox/rc.xml)」。

或是參考我的「[文件導引](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/de-box/play-openbox/spec-keybind.md#toggle-show-desktop)」。


## xdotool

上面設定「Win + d」的「鍵盤按鍵綁定」之後，

可以搭配「[xdotool](http://manpages.ubuntu.com/manpages/bionic/en/man1/xdotool.1.html)」這個指令，來自於「Package: [xdotool](https://packages.ubuntu.com/bionic/xdotool)」。

例如，執行下面指令，

``` sh
xdotool key super+d
```

就會如同您按下「Win + d」這個動作，

所以也就會執行「[ToggleShowDesktop](http://openbox.org/wiki/Help:Actions#ToggleShowDesktop)」這個動作。

接著搭配撰寫「Desktop Entry」放到「~/.local/share/applications/」這個資料夾。

例如，撰寫「[~/.local/share/applications/openbox-toggle-show-desktop.desktop](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/de-box/play-openbox/config/openbox/asset/desktop-entry/openbox-toggle-show-desktop.desktop#L3)」，

只要將剛剛的指令，寫在「Exec=」之後，

例如

```
Exec=xdotool key super+d
```

再接著搭配「tint2」裡「launcher」的功能，在「[tint2rc](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/de-box/play-openbox/config/tint2/tint2rc#L168)」撰寫如下的設定

例如

```
launcher_item_app = openbox-toggle-show-desktop.desktop
```

這樣在「tint2」就會有「切換顯示桌面」的「按鈕」。

這個技巧，是在「Arch Wiki / [Openbox](https://wiki.archlinux.org/index.php/Openbox#Desktop_menu_as_a_panel_menu)」學到的。


## wmctrl

可以搭配「[wmctrl](http://manpages.ubuntu.com/manpages/bionic/en/man1/wmctrl.1.html)」這個指令，來自於「Package: [wmctrl](https://packages.ubuntu.com/bionic/wmctrl)」。


撰寫一個「Shell Script」放到「~/bin」這個資料夾。

例如：撰寫「[~/bin/wmctrl-toggle-desktop.sh](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/xsession-wm-metacity/metacity/xsession-wm-metacity-with-tint2/config/wmctrl/wmctrl-toggle-show-desktop.sh)」，內容如下

``` sh
#!/usr/bin/env bash

if xprop -root _NET_SHOWING_DESKTOP | grep '= 1'; then
	wmctrl -k off
else
	wmctrl -k on
fi
```

上面這段程式碼，是在「[這篇文章下面的回覆](https://www.linuxquestions.org/questions/linux-software-2/how-to-show-desktop-in-xfce4-601161-print/)」看到的。

記得設定可執行

``` sh
$ chmod u+x ~/bin/wmctrl-toggle-desktop.sh
```

或是執行

``` sh
$ chmod 755 ~/bin/wmctrl-toggle-desktop.sh
```

然後一樣可以善用上面提到的技巧，撰寫「[Desktop Entry](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/xsession-wm-metacity/metacity/xsession-wm-metacity-with-tint2/config/wmctrl/wmctrl-toggle-show-desktop.desktop)」，

搭配「tint2」裡「launcher」的功能，

這樣在「tint2」就會有「切換顯示桌面」的「按鈕」。
