---
layout: page
title: play-locale
date: 2018-04-01 22:03:11 +0800
description: >
  play-locale
parent:
  title: play-ubuntu-18.04-plan
  url: '/read/project/play-ubuntu-18.04-plan'
source_url: '/read/project/play-ubuntu-18.04-plan/play-locale/index.md'
---


## 專案

* [play-locale](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/plan/env-full/play-locale)


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
$ cd play-ubuntu-18.04-plan/plan/env-full/play-locale
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


### mod-locale help

執行下面指令，觀看使用說明

``` sh
$ mod-locale
```

或是執行

``` sh
$ mod-locale help
```

顯示

```

Usage:

$ mod-locale [command]

Ex:

$ mod-locale
$ mod-locale help

$ mod-locale install
$ mod-locale remove

$ mod-locale pkg-install
$ mod-locale pkg-remove

$ mod-locale conf-set
$ mod-locale conf-reset

Manpage:

$ man mod-locale

Debug:

$ export DEBUG_PLAY_LOCALE=true

Sub:

$ mod-locale sub:locale_gen/all

$ mod-locale sub:locale_switch/en_us
$ mod-locale sub:locale_switch/zh_tw
```


### mod-locale install

執行下面指令，執行所有安裝

``` sh
$ mod-locale install
```


## 個別操作


### sub:locale_gen/all

執行

``` sh
$ mod-locale sub:locale_gen/all
```


### sub:locale_switch/en_us

執行

``` sh
$ mod-locale sub:locale_switch/en_us
```

### sub:locale_switch/zh_tw

執行

``` sh
$ mod-locale sub:locale_switch/en_us
```
