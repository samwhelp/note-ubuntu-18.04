---
layout: page
title: play-im
date: 2018-04-01 22:03:11 +0800
description: >
  play-im
parent:
  title: play-ubuntu-18.04-plan
  url: '/read/project/play-ubuntu-18.04-plan'
source_url: '/read/project/play-ubuntu-18.04-plan/play-im/index.md'
---


## 專案

* [play-im](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/plan/im-full/play-im)

## Prototype

* [play-ubuntu-18.04-plan/prototype/env-basic/im](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/prototype/env-basic/im)


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
$ cd play-ubuntu-18.04-plan/plan/im-full/play-im
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


### mod-im help

執行下面指令，觀看使用說明

``` sh
$ mod-im
```

或是執行

``` sh
$ mod-im help
```

顯示

```

Usage:

$ mod-im [command]

Ex:

$ mod-im
$ mod-im help

$ mod-im install
$ mod-im remove

$ mod-im pkg-install
$ mod-im pkg-remove

$ mod-im conf-set
$ mod-im conf-reset

Manpage:

$ man mod-im

Debug:

$ export DEBUG_PLAY_IM=true

Sub:

$ mod-im sub:gcin/install
$ mod-im sub:gcin/remove
$ mod-im sub:gcin/pkg-install
$ mod-im sub:gcin/pkg-remove
$ mod-im sub:gcin/conf-set
$ mod-im sub:gcin/conf-reset

$ mod-im sub:hime/install
$ mod-im sub:hime/remove
$ mod-im sub:hime/pkg-install
$ mod-im sub:hime/pkg-remove
$ mod-im sub:hime/conf-set
$ mod-im sub:hime/conf-reset

$ mod-im sub:fcitx_chewing/install
$ mod-im sub:fcitx_chewing/remove
$ mod-im sub:fcitx_chewing/pkg-install
$ mod-im sub:fcitx_chewing/pkg-remove
$ mod-im sub:fcitx_chewing/conf-set
$ mod-im sub:fcitx_chewing/conf-reset

$ mod-im sub:ibus_chewing/install
$ mod-im sub:ibus_chewing/remove
$ mod-im sub:ibus_chewing/pkg-install
$ mod-im sub:ibus_chewing/pkg-remove
$ mod-im sub:ibus_chewing/conf-set
$ mod-im sub:ibus_chewing/conf-reset

```


### mod-im install

執行下面指令，執行所有安裝

``` sh
$ mod-im install
```


## 個別操作


### sub:gcin/install

執行

``` sh
$ mod-im sub:gcin/install
```


### sub:hime/install

執行

``` sh
$ mod-im sub:hime/install
```

### sub:fcitx_chewing/install

執行

``` sh
$ mod-im sub:fcitx_chewing/install
```

### sub:ibus_chewing/install

執行

``` sh
$ mod-im sub:ibus_chewing/install
```
