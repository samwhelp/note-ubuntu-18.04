---
layout: page
title: play-i3
date: 2018-04-01 22:03:11 +0800
description: >
  play-i3
parent:
  title: play-ubuntu-18.04-plan
  url: '/read/project/play-ubuntu-18.04-plan'
source_url: '/read/project/play-ubuntu-18.04-plan/play-i3/index.md'
---


## 專案

* [play-ubuntu-18.04-plan/plan/de-basic/play-i3](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/plan/de-basic/play-i3)


## Prototype

* [play-ubuntu-18.04-plan/prototype/de-basic/play-i3](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/prototype/de-basic/play-i3)


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
$ cd play-ubuntu-18.04-plan/plan/de-basic/play-i3
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


### mod-i3 help

執行下面指令，觀看使用說明

``` sh
$ mod-i3
```

或是執行

``` sh
$ mod-i3 help
```

顯示

```

Usage:

$ mod-i3 [command]

Ex:

$ mod-i3
$ mod-i3 help

$ mod-i3 install
$ mod-i3 remove

$ mod-i3 pkg-install
$ mod-i3 pkg-remove

$ mod-i3 conf-set
$ mod-i3 conf-reset

Manpage:

$ man mod-i3

Debug:

$ export DEBUG_PLAY_I3=true

```


### mod-i3 install

執行下面指令，執行所有安裝

``` sh
$ mod-i3 install
```
