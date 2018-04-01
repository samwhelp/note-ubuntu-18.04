---
layout: page
title: play-apt
date: 2018-04-01 22:03:11 +0800
description: >
  play-apt
parent:
  title: play-ubuntu-18.04-plan
  url: '/read/project/play-ubuntu-18.04-plan'
source_url: '/read/project/play-ubuntu-18.04-plan/play-apt/index.md'
---


## 專案

* [play-ubuntu-18.04-plan/plan/env-full/play-apt](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/plan/env-full/play-apt)


## Prototype

* [play-ubuntu-18.04-plan/prototype/env-basic/apt-sources-list](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/prototype/env-basic/apt-sources-list)


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
$ cd play-ubuntu-18.04-plan/plan/env-full/play-apt
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


### mod-apt help

執行下面指令，觀看使用說明

``` sh
$ mod-apt
```

或是執行

``` sh
$ mod-apt help
```

顯示

```

Usage:

$ mod-apt [command]

Ex:

$ mod-apt
$ mod-apt help

$ mod-apt install
$ mod-apt remove

$ mod-apt pkg-install
$ mod-apt pkg-remove

$ mod-apt conf-set
$ mod-apt conf-reset

Manpage:

$ man mod-apt

Debug:

$ export DEBUG_PLAY_APT=true

Sub:

$ mod-apt sub:apt/src-tw
$ mod-apt sub:apt/src-us

```


### mod-apt install

執行下面指令，執行所有安裝

``` sh
$ mod-apt install
```


## 個別操作


### sub:apt/src-tw

執行

``` sh
$ mod-apt sub:apt/src-tw
```


### sub:apt/src-us

執行

``` sh
$ mod-apt sub:apt/src-us
```
