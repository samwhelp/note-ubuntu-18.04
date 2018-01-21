---
layout: page
title: Ubuntu 18.04 LTS (Bionic Beaver) Daily Build
description: >
  Ubuntu 18.04 LTS (Bionic Beaver) Daily Build。
parent:
  title: Ubuntu Release Cdimage
  url: '/read/subject/release-cdimage/'
source_url: '/read/subject/release-cdimage/daily-build.md'
---


## 下載頁面

* [http://cdimage.ubuntu.com/cdimage/daily-live/current/](http://cdimage.ubuntu.com/cdimage/daily-live/current/)
* [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)


## 下載ISO檔

執行下面指令，下載「[http://cdimage.ubuntu.com/cdimage/daily-live/current/bionic-desktop-amd64.iso](http://cdimage.ubuntu.com/cdimage/daily-live/current/bionic-desktop-amd64.iso)」。

``` sh
$ wget -c http://cdimage.ubuntu.com/cdimage/daily-live/current/bionic-desktop-amd64.iso
```


## 下載MD5SUMS

執行下面指令，下載「[http://cdimage.ubuntu.com/cdimage/daily-live/current/MD5SUMS](http://cdimage.ubuntu.com/cdimage/daily-live/current/MD5SUMS)」。

``` sh
$ wget -c http://cdimage.ubuntu.com/cdimage/daily-live/current/MD5SUMS
```


## 校驗方式

執行

``` sh
$ md5sum -c MD5SUMS
```

顯示

```
bionic-desktop-amd64.iso: OK
```


## 相關討論

* Ubuntu Community Help Wiki / [HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
* Ubuntu Community Help Wiki / [BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
* [Ubuntu Release Cdimage 16.04 (Xenial Xerus)](http://samwhelp.github.io/book-ubuntu-qna/read/case/release-cdimage/1604.html)


## Ubuntu Flavours Daily Build

* [xubuntu](http://cdimage.ubuntu.com/xubuntu/daily-live/current/)
* [lubuntu](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)
* [kubuntu](http://cdimage.ubuntu.com/kubuntu/daily-live/current/)
* [ubuntu-budgie](http://cdimage.ubuntu.com/ubuntu-budgie/daily-live/current/)
* [ubuntu-mate](http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/)
* [ubuntu-server](http://cdimage.ubuntu.com/ubuntu-server/daily-live/current/)
