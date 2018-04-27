---
layout: page
title: Ubuntu 18.04 LTS (Bionic Beaver) Release Cdimage
date: 2018-04-27 12:17:17 +0800
description: >
  Ubuntu 18.04 LTS (Bionic Beaver) Release Cdimage。
parent:
  title: Ubuntu Release Cdimage
  url: '/read/subject/release-cdimage/'
source_url: '/read/subject/release-cdimage/daily-build.md'
---


## Release Notes

* [Ubuntu 18.04 LTS (Bionic Beaver) Release Notes](https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes)


## 下載入口連結

* [http://releases.ubuntu.com/](http://releases.ubuntu.com/)
* [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)


## 下載頁面

* [http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/)



## 下載 ISO檔

執行下面指令，下載「[http://releases.ubuntu.com/18.04/ubuntu-18.04-desktop-amd64.iso](http://releases.ubuntu.com/18.04/ubuntu-18.04-desktop-amd64.iso)」。

``` sh
$ wget -c http://releases.ubuntu.com/18.04/ubuntu-18.04-desktop-amd64.iso
```


## 下載 MD5SUMS

執行下面指令，下載「[http://releases.ubuntu.com/18.04/MD5SUMS](http://releases.ubuntu.com/18.04/MD5SUMS)」。

``` sh
$ wget -c http://releases.ubuntu.com/18.04/MD5SUMS
```


## 校驗方式

執行

``` sh
$ md5sum -c MD5SUMS
```

顯示

```
ubuntu-18.04-desktop-amd64.iso: OK
```


## 相關討論

* Ubuntu Community Help Wiki / [HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
* Ubuntu Community Help Wiki / [BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
* [Ubuntu Release Cdimage 16.04 (Xenial Xerus)](http://samwhelp.github.io/book-ubuntu-qna/read/case/release-cdimage/1604.html)


## Ubuntu Flavours Release Cdimage

* [xubuntu](http://cdimage.ubuntu.com/xubuntu/releases/18.04/release/)
* [lubuntu](http://cdimage.ubuntu.com/lubuntu/releases/18.04/release/)
* [kubuntu](http://cdimage.ubuntu.com/kubuntu/releases/18.04/release/)
* [ubuntu-budgie](http://cdimage.ubuntu.com/ubuntu-budgie/releases/18.04/release/)
* [ubuntu-mate](http://cdimage.ubuntu.com/ubuntu-mate/releases/18.04/release/)


## iso link

```
http://releases.ubuntu.com/18.04/ubuntu-18.04-desktop-amd64.iso
http://releases.ubuntu.com/18.04/ubuntu-18.04-live-server-amd64.iso
http://cdimage.ubuntu.com/xubuntu/releases/18.04/release/xubuntu-18.04-desktop-amd64.iso
http://cdimage.ubuntu.com/lubuntu/releases/18.04/release/lubuntu-18.04-desktop-amd64.iso
http://cdimage.ubuntu.com/kubuntu/releases/18.04/release/kubuntu-18.04-desktop-amd64.iso
http://cdimage.ubuntu.com/ubuntu-budgie/releases/18.04/release/ubuntu-budgie-18.04-desktop-amd64.iso
http://cdimage.ubuntu.com/ubuntu-mate/releases/18.04/release/ubuntu-mate-18.04-desktop-amd64.iso
```

上面的列表，可以存成一個檔案「iso.list」。

然後執行

``` sh
$ wget -c -i iso.list
```
