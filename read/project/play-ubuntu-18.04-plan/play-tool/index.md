---
layout: page
title: play-tool
date: 2018-04-01 22:03:11 +0800
description: >
  play-tool
parent:
  title: play-ubuntu-18.04-plan
  url: '/read/project/play-ubuntu-18.04-plan'
source_url: '/read/project/play-ubuntu-18.04-plan/play-tool/index.md'
---


## 專案

* [play-ubuntu-18.04-plan/plan/tool-full/play-tool](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/plan/tool-full/play-tool)

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
$ cd play-ubuntu-18.04-plan/plan/tool-full/play-tool
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


### mod-tool help

執行下面指令，觀看使用說明

``` sh
$ mod-tool
```

或是執行

``` sh
$ mod-tool help
```

顯示

```

Usage:

$ mod-tool [command]

Ex:

$ mod-tool
$ mod-tool help

$ mod-tool install
$ mod-tool remove

$ mod-tool pkg-install
$ mod-tool pkg-remove

$ mod-tool conf-set
$ mod-tool conf-reset

Manpage:

$ man mod-tool

```


### mod-tool install

執行下面指令，執行所有安裝

``` sh
$ mod-tool install
```
