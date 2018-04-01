---
layout: page
title: play-font
date: 2018-04-01 22:03:11 +0800
description: >
  play-font
parent:
  title: play-ubuntu-18.04-plan
  url: '/read/project/play-ubuntu-18.04-plan'
source_url: '/read/project/play-ubuntu-18.04-plan/play-font/index.md'
---


## 專案

* [play-ubuntu-18.04-plan/plan/font-full/play-font](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/plan/font-full/play-font)


## Prototype

* [play-ubuntu-18.04-plan/prototype/font-wget/cns11643](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/prototype/font-wget/cns11643)
* [play-ubuntu-18.04-plan/prototype/font-wget/noto](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/prototype/font-wget/noto)
* [play-ubuntu-18.04-plan/prototype/font-basic/typeface-serif-sans-serif-monospace](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/prototype/font-basic/typeface-serif-sans-serif-monospace)


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
$ cd play-ubuntu-18.04-plan/plan/font-full/play-font
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


### mod-font help

執行下面指令，觀看使用說明

``` sh
$ mod-font
```

或是執行

``` sh
$ mod-font help
```

顯示

```

Usage:

$ mod-font [command]

Ex:

$ mod-font
$ mod-font help

$ mod-font install
$ mod-font remove

$ mod-font pkg-install
$ mod-font pkg-remove

$ mod-font conf-set
$ mod-font conf-reset

Manpage:

$ man mod-font

Debug:

$ export DEBUG_PLAY_FONT=true

Sub:

$ mod-font sub:fontfamily/conf-set
$ mod-font sub:fontfamily/conf-reset

$ mod-font sub:noto/install
$ mod-font sub:noto/remove

$ mod-font sub:cns11643/install
$ mod-font sub:cns11643/remove

```


### mod-font install

執行下面指令，執行所有安裝

``` sh
$ mod-font install
```


## 個別操作


### sub:fontfamily/conf-set

執行

``` sh
$ mod-font sub:fontfamily/conf-set
```


### sub:fontfamily/conf-reset

執行

``` sh
$ mod-font sub:fontfamily/conf-reset
```


### sub:cns11643/install

執行

``` sh
$ mod-font sub:cns11643/install
```
