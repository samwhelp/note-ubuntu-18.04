---
layout: page
title: pcmanfm-qt 當作 Desktop 的操作
date: 2018-07-03 13:55:42 +0800
description: >
  pcmanfm-qt 當作 Desktop 的操作
parent:
  title: lxqt
  url: '/read/subject/lxqt'
source_url: '/read/subject/lxqt/pcmanfm-qt/desktop.md'
---


## Manpage

執行下面指令，閱讀關於「[pcmanfm-qt](http://manpages.ubuntu.com/manpages/bionic/en/man1/pcmanfm-qt.1.html)」這個指令的說明。

``` sh
$ man pcmanfm-qt
```


## Help

或是執行下面指令，了解到有那些相關的參數。


``` sh
$ pcmanfm-qt -h
```

或是執行

``` sh
$ pcmanfm-qt -help
```

顯示

```
Usage: pcmanfm-qt [options] [FILE1, FILE2,...]

Options:
  -h, --help                  Displays this help.
  -v, --version               Displays version information.
  -p, --profile <PROFILE>     Name of configuration profile
  -d, --daemon-mode           Run PCManFM as a daemon
  -q, --quit                  Quit PCManFM
  --desktop                   Launch desktop manager
  --desktop-off               Turn off desktop manager if it's running
  --desktop-pref <NAME>       Open desktop preference dialog on the page with
                              the specified name
  -n, --new-window            Open new window
  -f, --find-files            Open Find Files utility
  -w, --set-wallpaper <FILE>  Set desktop wallpaper from image FILE
  --wallpaper-mode <MODE>     Set mode of desktop wallpaper.
                              MODE=(color|stretch|fit|center|tile|zoom)
  --show-pref <NAME>          Open Preferences dialog on the page with the
                              specified name

Arguments:
  files                       Files or directories to open
```


## Version

執行

``` sh
$ pcmanfm-qt -v
```

或是執行

``` sh
$ pcmanfm-qt --version
```

顯示

```
pcmanfm-qt 0.12.0
```


## Process

執行

``` sh
$ ps aux | grep pcmanfm-qt
```

顯示

```
user       1336  1.1  1.3 1081160 107428 tty1   Sl+  01:49   7:55 pcmanfm-qt --desktop --profile=lxqt
user      26889  0.0  0.0  13072  2572 pts/12   S+   13:29   0:00 grep --color=auto pcmanfm-qt
```

關於「pcmanfm-qt --desktop --profile=lxqt」這個指令。

是定義在「/etc/xdg/autostart/lxqt-desktop.desktop」這個檔案。

可以透過下面步驟找到。

執行

``` sh
$ dpkg -L pcmanfm-qt | grep desktop
```

顯示

```
/etc/xdg/autostart/lxqt-desktop.desktop
/usr/share/applications/pcmanfm-qt-desktop-pref.desktop
/usr/share/applications/pcmanfm-qt.desktop
```

執行

``` sh
$ grep '^Exec=' /etc/xdg/autostart/lxqt-desktop.desktop
```

顯示

```
Exec=pcmanfm-qt --desktop --profile=lxqt
```

而「/etc/xdg/autostart/lxqt-desktop.desktop」這個檔案，

是在要進入桌面環境時，透過「[lxqt-session](http://manpages.ubuntu.com/manpages/bionic/en/man1/lxqt-session.1.html)」，來啟動的。

進入桌面後，也可以透過「[lxqt-config-session](http://manpages.ubuntu.com/manpages/bionic/en/man1/lxqt-config-session.1.html)」這個「圖形界面程式」來啟動和停止，也可以啟用和停用這個「Module(模組)」。

在第一個頁簽「Basic Settings」，有一個列表「LXQt Modules」，以及兩個按鈕「Start」和「Stop」。


## X-LXQt-Module

執行

``` sh
$ grep 'X-LXQt-Module' /etc/xdg/autostart/* -R -n
```

顯示

```
/etc/xdg/autostart/lxqt-desktop.desktop:7:X-LXQt-Module=true
/etc/xdg/autostart/lxqt-globalkeyshortcuts.desktop:7:X-LXQt-Module=true
/etc/xdg/autostart/lxqt-notifications.desktop:7:X-LXQt-Module=true
/etc/xdg/autostart/lxqt-panel.desktop:7:X-LXQt-Module=true
/etc/xdg/autostart/lxqt-policykit-agent.desktop:7:X-LXQt-Module=true
/etc/xdg/autostart/lxqt-powermanagement.desktop:9:X-LXQt-Module=true
/etc/xdg/autostart/lxqt-runner.desktop:7:X-LXQt-Module=true
```

上面有「X-LXQt-Module=true」就會顯示在剛剛提到的「LXQt Modules」那個列表。


## DBus

除了透過「[lxqt-config-session](http://manpages.ubuntu.com/manpages/bionic/en/man1/lxqt-config-session.1.html)」這個「圖形界面程式」來啟動和停止，也可以透過「Dbus」來操作。

執行

``` sh
$ qdbus | grep lxqt
```

顯示

```
 org.lxqt.global_key_shortcuts
 org.lxqt.lxqt-runner
 org.lxqt.lxqt-powermanagement
 org.lxqt.session
```

執行

``` sh
$ qdbus org.lxqt.session
```

顯示

```
/
/LXQtSession
```

執行

``` sh
$ qdbus org.lxqt.session /LXQtSession
```

顯示

```
method bool org.lxqt.session.canLogout()
method bool org.lxqt.session.canPowerOff()
method bool org.lxqt.session.canReboot()
method QDBusVariant org.lxqt.session.listModules()
method Q_NOREPLY void org.lxqt.session.logout()
signal void org.lxqt.session.moduleStateChanged(QString moduleName, bool state)
method Q_NOREPLY void org.lxqt.session.powerOff()
method Q_NOREPLY void org.lxqt.session.reboot()
method Q_NOREPLY void org.lxqt.session.startModule(QString name)
method Q_NOREPLY void org.lxqt.session.stopModule(QString name)
method QDBusVariant org.freedesktop.DBus.Properties.Get(QString interface_name, QString property_name)
method QVariantMap org.freedesktop.DBus.Properties.GetAll(QString interface_name)
signal void org.freedesktop.DBus.Properties.PropertiesChanged(QString interface_name, QVariantMap changed_properties, QStringList invalidated_properties)
method void org.freedesktop.DBus.Properties.Set(QString interface_name, QString property_name, QDBusVariant value)
method QString org.freedesktop.DBus.Introspectable.Introspect()
method QString org.freedesktop.DBus.Peer.GetMachineId()
method void org.freedesktop.DBus.Peer.Ping()
```


### org.lxqt.session.listModules

執行

``` sh
$ qdbus org.lxqt.session /LXQtSession org.lxqt.session.listModules
```

顯示

```
:lxqt-confupdate.desktop
lxqt-desktop.desktop
lxqt-globalkeyshortcuts.desktop
lxqt-notifications.desktop
lxqt-panel.desktop
lxqt-policykit-agent.desktop
lxqt-powermanagement.desktop
lxqt-runner.desktop
```


### org.lxqt.session.stopModule

執行下面指令

``` sh
$ qdbus org.lxqt.session /LXQtSession org.lxqt.session.stopModule 'lxqt-desktop.desktop'
```

執行上面指令，您就會發現，桌面的背景和圖示消失了。

也可以執行「ps aux | grep pcmanfm-qt」，只有顯示

```
user      27725  0.0  0.0  13072  1032 pts/12   R+   13:52   0:00 grep --color=auto pcmanfm-qt
```


### org.lxqt.session.stopModule

執行下面指令

``` sh
$ qdbus org.lxqt.session /LXQtSession org.lxqt.session.startModule 'lxqt-desktop.desktop'
```

執行上面指令，您就會發現，桌面的背景和圖示又恢復了。


## pcmanfm-qt --desktop-off

另外也可以透過指令「[pcmanfm-qt](http://manpages.ubuntu.com/manpages/bionic/en/man1/pcmanfm-qt.1.html)」來操作。

執行

``` sh
$ pcmanfm-qt --desktop-off
```

執行上面指令，您就會發現，桌面的背景和圖示消失了。


## pcmanfm-qt --desktop

執行

``` sh
$ pcmanfm-qt --desktop --profile=lxqt
```

執行上面指令，您就會發現，桌面的背景和圖示又恢復了。


## pcmanfm-qt --profile=lxqt

關於「--profile=lxqt」，這個可以對應到「~/.config/pcmanfm-qt/lxqt/settings.conf」。

若是「--profile=default」，則是可以對應到「~/.config/pcmanfm-qt/default/settings.conf」。

若是「--profile=misc」，則是可以對應到「~/.config/pcmanfm-qt/misc/settings.conf」。


## pcmanfm-qt --desktop-pref=general

執行下面指令，就會啟動一個設定視窗，標題是「Desktop Preferences」，並且顯示第一個頁簽「General」。

``` sh
$ pcmanfm-qt --desktop-pref=general
```

關於「pcmanfm-qt --desktop-pref=general」這個指令。

是定義在「/usr/share/applications/pcmanfm-qt-desktop-pref.desktop」這個檔案。

可以透過下面步驟找到。

執行

``` sh
$ dpkg -L pcmanfm-qt | grep desktop
```

顯示

```
/etc/xdg/autostart/lxqt-desktop.desktop
/usr/share/applications/pcmanfm-qt-desktop-pref.desktop
/usr/share/applications/pcmanfm-qt.desktop
```

執行

``` sh
$ grep '^Exec=' /usr/share/applications/pcmanfm-qt-desktop-pref.desktop
```

顯示

```
Exec=pcmanfm-qt --desktop-pref=general
```

其他還可以執行的如下

執行下面指令，就會啟動一個設定視窗，標題是「Desktop Preferences」，並且顯示第二個頁簽「Slide Show」。

``` sh
$ pcmanfm-qt --desktop-pref=bg
```

執行下面指令，就會啟動一個設定視窗，標題是「Desktop Preferences」，並且顯示第三個頁簽「Advanced」。

``` sh
$ pcmanfm-qt --desktop-pref=advanced
```


## pcmanfm-qt --set-wallpaper

執行

``` sh
$ ls /usr/share/backgrounds/ -1
```

顯示

```
Beaver_Wallpaper_Grey_4096x2304.png
Cathédrale_Marie-Rheine-du-Monde_by_Thierry_Pon.jpg
contest
Crocus_Wallpaper_by_Roy_Tanck.jpg
Definitive_Light_Zen_Orange_by_Pierre_Cante.jpg
El_Haouaria_by_Nusi_Nusi.jpg
greybird.svg
Halifax_Sunset_by_Vlad_Drobinin.jpg
Manhattan_Sunset_by_Giacomo_Ferroni.jpg
On_top_of_the_Rubihorn_by_Matthias_Niess.jpg
Raindrops_On_The_Table_by_Alex_Fazit.jpg
'Ross_Jones_Rockpool_(Sydney)_by_Chris_Carignan.jpg'
Spices_in_Athens_by_Makis_Chourdakis.jpg
This_Is_Bionic_Beaver_by_Pierre_Cante.jpg
ubuntu-default-greyscale-wallpaper.png
Wall_with_door_on_Gozo_by_Matthias_Niess.jpg
warty-final-ubuntu.png
xfce
```

舉例執行

``` sh
$ pcmanfm-qt -w '/usr/share/backgrounds/Spices_in_Athens_by_Makis_Chourdakis.jpg'
```

執行上面指令，就會發現「桌面背景」更改成「/usr/share/backgrounds/Spices_in_Athens_by_Makis_Chourdakis.jpg」這個圖片。


舉例執行

``` sh
$ pcmanfm-qt --set-wallpaper=/usr/share/backgrounds/Manhattan_Sunset_by_Giacomo_Ferroni.jpg
```

執行上面指令，就會發現「桌面背景」更改成「/usr/share/backgrounds/Manhattan_Sunset_by_Giacomo_Ferroni.jpg」這個圖片

這個動作，也可以透過「圖形界面程式」來操作，

也就是透過「pcmanfm-qt --desktop-pref=general」，

會啟動一個設定視窗，標題是「Desktop Preferences」，

在第一個頁簽「General」那，可以設定「Wallpaper image file」。

這個設定將會儲存在「~/.config/pcmanfm-qt/lxqt/settings.conf」這個檔案。

```
[Desktop]
Wallpaper=/usr/share/backgrounds/Manhattan_Sunset_by_Giacomo_Ferroni.jpg
```


## pcmanfm-qt --wallpaper-mode=stretch

上面桌面要正常顯示背景圖片，必須設定下面幾個模式「stretch」，「fit」，「center」，「tile」。

執行下面指令，將顯示模式設為「stretch」。

``` sh
$ pcmanfm-qt --wallpaper-mode=stretch
```

執行下面指令，將顯示模式設為「fit」。

``` sh
$ pcmanfm-qt --wallpaper-mode=fit
```

執行下面指令，將顯示模式設為「center」。

``` sh
$ pcmanfm-qt --wallpaper-mode=center
```

執行下面指令，將顯示模式設為「tile」。

``` sh
$ pcmanfm-qt --wallpaper-mode=tile
```

這個設定將會儲存在「~/.config/pcmanfm-qt/lxqt/settings.conf」這個檔案。

```
[Desktop]
WallpaperMode=stretch
```

## pcmanfm-qt --wallpaper-mode=color

若是設定成「color」這個模式，則桌面不會顯示背景圖片，只會顯示顏色。

執行下面指令，將顯示模式設為「color」。

``` sh
$ pcmanfm-qt --wallpaper-mode=color
```

而顯示的「color」會根據「~/.config/pcmanfm-qt/lxqt/settings.conf」這個檔案裡面的設定。

```
[Desktop]
WallpaperMode=color
BgColor=#00557f
```

上面這些動作，也可以透過「圖形界面程式」來操作，

也就是透過「pcmanfm-qt --desktop-pref=general」，

會啟動一個設定視窗，標題是「Desktop Preferences」，

在第一個頁簽「General」那，

可以設定「Wallpaper mode」和「Select background color」。
