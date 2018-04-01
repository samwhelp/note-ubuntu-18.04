---
layout: page
title: play-lxqt
date: 2018-04-01 22:03:11 +0800
description: >
  play-lxqt
parent:
  title: play-ubuntu-18.04-plan
  url: '/read/project/play-ubuntu-18.04-plan'
source_url: '/read/project/play-ubuntu-18.04-plan/play-lxqt/index.md'
---


## 專案

* [play-ubuntu-18.04-plan/plan/de-basic/play-lxqt](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/plan/de-basic/play-lxqt)


## Prototype

* [play-ubuntu-18.04-plan/prototype/de-basic/play-lxqt](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/prototype/de-basic/play-lxqt)


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
$ cd play-ubuntu-18.04-plan/plan/de-basic/play-lxqt
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


### mod-lxqt help

執行下面指令，觀看使用說明

``` sh
$ mod-lxqt
```

或是執行

``` sh
$ mod-lxqt help
```

顯示

```

Usage:

$ mod-lxqt [command]

Ex:

$ mod-lxqt
$ mod-lxqt help

$ mod-lxqt install
$ mod-lxqt remove

$ mod-lxqt pkg-install
$ mod-lxqt pkg-remove

$ mod-lxqt conf-set
$ mod-lxqt conf-reset

Manpage:

$ man mod-lxqt

```


### mod-lxqt install

執行下面指令，執行所有安裝

``` sh
$ mod-lxqt install
```
