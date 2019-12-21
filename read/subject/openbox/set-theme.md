---
layout: page
title: set openbox theme
date: 2019-12-21 13:21:16 +0800
description: >
  set openbox theme
parent:
  title: openbox
  url: '/read/subject/openbox'
source_url: 'read/subject/openbox/set-theme.md'
---


## Config Tool

* [obconf](http://manpages.ubuntu.com/manpages/bionic/en/man1/obconf.1.html) (Package: [obconf](https://packages.ubuntu.com/bionic/obconf))
* obconf-qt (Package: obconf-qt)


## Config File Path

* [~/.config/openbox/rc.xml](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/de-box/play-openbox/config/openbox/rc.xml#L45) ([manual](* http://openbox.org/wiki/Help:Configuration#Theme))

For example:

``` xml
<theme>
  <name>NumixBlue</name>
</theme>
```

## Theme Dir Path

* /usr/share/themes/
* ~/.themes/
* ~/.local/share/themes/


## Manual

* http://openbox.org/wiki/Help:Contents#rc.xml
* http://openbox.org/wiki/Help:Configuration#Theme
* http://openbox.org/wiki/Help:Themes


## How to Find Openbox Theme

執行

``` sh
$ find /usr/share/themes/ -name openbox-3 | sort -u
```

顯示

```
/usr/share/themes/Artwiz-boxed/openbox-3
/usr/share/themes/Bear2/openbox-3
/usr/share/themes/Breeze-ob/openbox-3
/usr/share/themes/Clearlooks-3.4/openbox-3
/usr/share/themes/Clearlooks-Olive/openbox-3
/usr/share/themes/Clearlooks/openbox-3
/usr/share/themes/Mikachu/openbox-3
/usr/share/themes/Natura/openbox-3
/usr/share/themes/Nightmare-01/openbox-3
/usr/share/themes/Nightmare-02/openbox-3
/usr/share/themes/Nightmare-03/openbox-3
/usr/share/themes/Nightmare/openbox-3
/usr/share/themes/NumixBlue/openbox-3
/usr/share/themes/Numix/openbox-3
/usr/share/themes/Onyx-Citrus/openbox-3
/usr/share/themes/Onyx/openbox-3
/usr/share/themes/Orang/openbox-3
/usr/share/themes/Syscrash/openbox-3
```

執行

``` sh
$ find /usr/share/themes/ -name openbox-3 | cut -d '/' -f 5 | sort -u
```

顯示

```
Artwiz-boxed
Bear2
Breeze-ob
Clearlooks
Clearlooks-3.4
Clearlooks-Olive
Mikachu
Natura
Nightmare
Nightmare-01
Nightmare-02
Nightmare-03
Numix
NumixBlue
Onyx
Onyx-Citrus
Orang
Syscrash
```

## How to Find Openbox Theme Package


### installed

執行

``` sh
$ dpkg -S $(find /usr/share/themes/ -name openbox-3 | sort -u) | sort -u
```

顯示

```
numix-blue-gtk-theme: /usr/share/themes/NumixBlue/openbox-3
numix-gtk-theme: /usr/share/themes/Numix/openbox-3
openbox: /usr/share/themes/Artwiz-boxed/openbox-3
openbox: /usr/share/themes/Bear2/openbox-3
openbox: /usr/share/themes/Breeze-ob/openbox-3
openbox: /usr/share/themes/Clearlooks-3.4/openbox-3
openbox: /usr/share/themes/Clearlooks-Olive/openbox-3
openbox: /usr/share/themes/Clearlooks/openbox-3
openbox: /usr/share/themes/Mikachu/openbox-3
openbox: /usr/share/themes/Natura/openbox-3
openbox: /usr/share/themes/Nightmare-01/openbox-3
openbox: /usr/share/themes/Nightmare-02/openbox-3
openbox: /usr/share/themes/Nightmare-03/openbox-3
openbox: /usr/share/themes/Nightmare/openbox-3
openbox: /usr/share/themes/Onyx-Citrus/openbox-3
openbox: /usr/share/themes/Onyx/openbox-3
openbox: /usr/share/themes/Orang/openbox-3
openbox: /usr/share/themes/Syscrash/openbox-3
```

### apt-file search

執行

``` sh
$ apt-file search openbox-3 | less
```

執行

``` sh
$ apt-file search openbox-3 | awk -F ': ' '{print $1}' | sort -u
```

顯示

```
clearlooks-phenix-theme
lubuntu-artwork
lubuntu-artwork-10-10
lubuntu-artwork-11-04
lubuntu-artwork-11-10
lubuntu-artwork-12-04
lubuntu-artwork-12-10
lubuntu-artwork-13-04
lubuntu-artwork-13-10
lubuntu-artwork-14-04
lubuntu-artwork-14-10
lubuntu-artwork-15-04
lubuntu-artwork-15-10
lubuntu-artwork-16-04
lubuntu-artwork-16-10
lubuntu-artwork-17-04
lubuntu-artwork-17-10
mate-themes
murrine-themes
numix-blue-gtk-theme
numix-gtk-theme
openbox
```

### Create Theme Package List

``` sh
$ apt-file search openbox-3 | awk -F ': ' '{print $1}' | sort -u | awk '{print "* ["$1"](https://packages.ubuntu.com/bionic/"$1")"}'
```

* [clearlooks-phenix-theme](https://packages.ubuntu.com/bionic/clearlooks-phenix-theme)
* [lubuntu-artwork](https://packages.ubuntu.com/bionic/lubuntu-artwork)
* [lubuntu-artwork-10-10](https://packages.ubuntu.com/bionic/lubuntu-artwork-10-10)
* [lubuntu-artwork-11-04](https://packages.ubuntu.com/bionic/lubuntu-artwork-11-04)
* [lubuntu-artwork-11-10](https://packages.ubuntu.com/bionic/lubuntu-artwork-11-10)
* [lubuntu-artwork-12-04](https://packages.ubuntu.com/bionic/lubuntu-artwork-12-04)
* [lubuntu-artwork-12-10](https://packages.ubuntu.com/bionic/lubuntu-artwork-12-10)
* [lubuntu-artwork-13-04](https://packages.ubuntu.com/bionic/lubuntu-artwork-13-04)
* [lubuntu-artwork-13-10](https://packages.ubuntu.com/bionic/lubuntu-artwork-13-10)
* [lubuntu-artwork-14-04](https://packages.ubuntu.com/bionic/lubuntu-artwork-14-04)
* [lubuntu-artwork-14-10](https://packages.ubuntu.com/bionic/lubuntu-artwork-14-10)
* [lubuntu-artwork-15-04](https://packages.ubuntu.com/bionic/lubuntu-artwork-15-04)
* [lubuntu-artwork-15-10](https://packages.ubuntu.com/bionic/lubuntu-artwork-15-10)
* [lubuntu-artwork-16-04](https://packages.ubuntu.com/bionic/lubuntu-artwork-16-04)
* [lubuntu-artwork-16-10](https://packages.ubuntu.com/bionic/lubuntu-artwork-16-10)
* [lubuntu-artwork-17-04](https://packages.ubuntu.com/bionic/lubuntu-artwork-17-04)
* [lubuntu-artwork-17-10](https://packages.ubuntu.com/bionic/lubuntu-artwork-17-10)
* [mate-themes](https://packages.ubuntu.com/bionic/mate-themes)
* [murrine-themes](https://packages.ubuntu.com/bionic/murrine-themes)
* [numix-blue-gtk-theme](https://packages.ubuntu.com/bionic/numix-blue-gtk-theme)
* [numix-gtk-theme](https://packages.ubuntu.com/bionic/numix-gtk-theme)
* [openbox](https://packages.ubuntu.com/bionic/openbox)


### Find Theme Name From Packages By apt-cache

執行

``` sh
$ apt-file search openbox-3 | awk -F ': ' '{print $2}' | cut -d '/' -f 5 | sort -u
```

顯示

```
Artwiz-boxed
Bear2
Box1
Box10
Box11
Box2
Box3
Box4
Box5
Box6
Box7
Box8
Box9
Breeze-ob
Clearlooks
Clearlooks-3.4
Clearlooks-Olive
Clearlooks-Phenix
Lubuntu Arc
Lubuntu-dark-panel
Lubuntu-default
Lubuntu-small
LxDesign
Mikachu
Natura
Nightmare
Nightmare-01
Nightmare-02
Nightmare-03
Numix
NumixBlue
Onyx
Onyx-Citrus
Orang
Orangine
Ozone1
Ozone2
Ozone3
Syscrash
TraditionalOk
```


## How to find other theme

* [http://openbox.org/download-themes.php](http://openbox.org/download-themes.php)
* [https://www.box-look.org/](https://www.box-look.org/)
* [https://www.box-look.org/browse/cat/140/order/latest/](https://www.box-look.org/browse/cat/140/order/latest/)
* [https://www.box-look.org/browse/cat/140/ord/rating/](https://www.box-look.org/browse/cat/140/ord/rating/)
