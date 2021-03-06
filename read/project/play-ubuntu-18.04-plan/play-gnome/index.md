---
layout: page
title: play-gnome
date: 2018-04-01 22:03:11 +0800
description: >
  play-gnome
parent:
  title: play-ubuntu-18.04-plan
  url: '/read/project/play-ubuntu-18.04-plan'
source_url: '/read/project/play-ubuntu-18.04-plan/play-gnome/index.md'
---


## 專案

* [play-ubuntu-18.04-plan/plan/de-basic/play-gnome](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/plan/de-basic/play-gnome)


## Prototype

* [play-ubuntu-18.04-plan/prototype/de-basic/play-gnome](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/prototype/de-basic/play-gnome)


## 操作步驟


### install git

執行下面指令，安裝「[git](https://packages.ubuntu.com/bionic/git)」這個套件。

``` sh
$ sudo apt-get install git
```


### git clone

執行

``` sh
$ git clone https://github.com/samwhelp/play-ubuntu-18.04-plan.git
```


### cd root dir

執行下面指令，切換到專案資料夾

``` sh
$ cd play-ubuntu-18.04-plan/plan/de-basic/play-gnome
```


### make prepare

執行下面指令，安裝產生deb檔，所需要的套件。

``` sh
$ make prepare
```


### make deb-build

執行下面指令，產生deb檔。

``` sh
$ make deb-build
```


### make deb-install

執行下面指令，安裝剛剛產生的deb檔。

``` sh
$ make deb-install
```


### mod-gnome help

執行下面指令，觀看使用說明

``` sh
$ mod-gnome
```

或是執行

``` sh
$ mod-gnome help
```

顯示

```

Usage:

$ mod-gnome [command]

Ex:

$ mod-gnome
$ mod-gnome help

$ mod-gnome install
$ mod-gnome remove

$ mod-gnome pkg-install
$ mod-gnome pkg-remove

$ mod-gnome conf-set
$ mod-gnome conf-reset

Manpage:

$ man mod-gnome

Debug:

$ export DEBUG_PLAY_GNOME=true

```


### mod-gnome install

執行下面指令，執行所有安裝

``` sh
$ mod-gnome install
```
