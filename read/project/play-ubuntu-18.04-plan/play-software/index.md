---
layout: page
title: play-software
date: 2018-04-01 22:03:11 +0800
description: >
  play-software
parent:
  title: play-ubuntu-18.04-plan
  url: '/read/project/play-ubuntu-18.04-plan'
source_url: '/read/project/play-ubuntu-18.04-plan/play-software/index.md'
---


## 專案

* [play-ubuntu-18.04-plan/plan/tool-full/play-software](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/plan/tool-full/play-software)

## Prototype

* [play-ubuntu-18.04-plan/prototype/tool-basic](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/prototype/tool-basic)


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
$ cd play-ubuntu-18.04-plan/plan/tool-full/play-software
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


### mod-software help

執行下面指令，觀看使用說明

``` sh
$ mod-software
```

或是執行

``` sh
$ mod-software help
```

顯示

```

Usage:

$ mod-software [command]

Ex:

$ mod-software
$ mod-software help

$ mod-software install
$ mod-software remove

$ mod-software pkg-install
$ mod-software pkg-remove

$ mod-software conf-set
$ mod-software conf-reset

Manpage:

$ man mod-software

Debug:

$ export DEBUG_PLAY_SOFTWARE=true

Sub:

$ mod-software sub:atom/install
$ mod-software sub:atom/remove

$ mod-software sub:chrome/install
$ mod-software sub:chrome/remove

$ mod-software sub:composer/install
$ mod-software sub:composer/remove

$ mod-software sub:youtube_dl/install
$ mod-software sub:youtube_dl/remove


```


## 個別操作


### sub:atom/install

執行

``` sh
$ mod-software sub:atom/install
```


### sub:chrome/install

執行

``` sh
$ mod-software sub:chrome/install
```


### sub:composer/install

執行

``` sh
$ mod-software sub:composer/install
```


### sub:youtube_dl/install

執行

``` sh
$ mod-software sub:youtube_dl/install
```
