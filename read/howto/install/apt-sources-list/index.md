---
layout: page
title: Apt sources.list
date: 2018-03-20 15:31:18 +0800
description: >
  Apt sources.list。
parent:
  title: 如何設定
  url: '/read/howto/install'
source_url: '/read/howto/install/apt-sources-list/index.md'
---


## 範例 Script

*  [play-ubuntu-18.04-plan/prototype/env-basic/apt-sources-list](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/prototype/env-basic/apt-sources-list)


## 更多參考

* The Debian Administrator's Handbook / [6.1. Filling in the sources.list File](https://debian-handbook.info/browse/stable/apt.html#sect.apt-sources.list)
* Debian Wiki / [SourcesList](https://wiki.debian.org/SourcesList)
* Ubuntu Community Help Wiki / [Repositories / CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
* Ubuntu Server Guide / Package Management / [Configuration](https://help.ubuntu.com/lts/serverguide/configuration.html)

## 修改說明


我是選擇英文來安裝，時區選「Asia/Taipei」，[安裝程式](https://packages.ubuntu.com/bionic/ubiquity)會將「/etc/apt/sources.list」設定[如下](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/env-basic/apt-sources-list/config/original/sources.list)

```
#deb cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Alpha amd64 (20180308)]/ bionic main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://tw.archive.ubuntu.com/ubuntu/ bionic main restricted
# deb-src http://tw.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://tw.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
# deb-src http://tw.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://tw.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://tw.archive.ubuntu.com/ubuntu/ bionic universe
deb http://tw.archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://tw.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://tw.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://tw.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://tw.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
# deb-src http://tw.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://tw.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
# deb-src http://tw.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
```

因為我會執行「apt-get source」這樣的指令，所以我會安裝「[dpkg-dev](https://packages.ubuntu.com/xenial/dpkg-dev)」這個套件，

並且將上面「/etc/apt/sources.list」的「deb-src」那幾行反註解，可以參考[這篇](https://www.ubuntu-tw.org/modules/newbb/viewtopic.php?post_id=358818#forumpost358818)的說明。

也就是設定[如下](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/env-basic/apt-sources-list/config/tw/sources.list)

```
#deb cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Alpha amd64 (20180308)]/ bionic main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://tw.archive.ubuntu.com/ubuntu/ bionic main restricted
deb-src http://tw.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://tw.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
deb-src http://tw.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://tw.archive.ubuntu.com/ubuntu/ bionic universe
deb-src http://tw.archive.ubuntu.com/ubuntu/ bionic universe
deb http://tw.archive.ubuntu.com/ubuntu/ bionic-updates universe
deb-src http://tw.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://tw.archive.ubuntu.com/ubuntu/ bionic multiverse
deb-src http://tw.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://tw.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
deb-src http://tw.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://tw.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://tw.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
```

若有時候「tw」的「mirror site」連不上，就會改成「us」的，改成[如下](https://github.com/samwhelp/play-ubuntu-18.04-plan/blob/master/prototype/env-basic/apt-sources-list/config/us/sources.list)

```
#deb cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Alpha amd64 (20180308)]/ bionic main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu bionic partner
# deb-src http://archive.canonical.com/ubuntu bionic partner

deb http://security.ubuntu.com/ubuntu bionic-security main restricted
deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
deb http://security.ubuntu.com/ubuntu bionic-security universe
deb-src http://security.ubuntu.com/ubuntu bionic-security universe
deb http://security.ubuntu.com/ubuntu bionic-security multiverse
deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
```


## 相關討論

* [[索引] 套件操作實務](https://www.ubuntu-tw.org/modules/newbb/viewtopic.php?post_id=333562#forumpost333562)
* [#24 回覆: Ubuntu 17.10 推出](https://www.ubuntu-tw.org/modules/newbb/viewtopic.php?post_id=358818#forumpost358818)
* [#2 回覆: Ubuntu17.10升級時出現了問題](https://www.ubuntu-tw.org/modules/newbb/viewtopic.php?post_id=359082#forumpost359082)
* [#4 回覆: Ubuntu 17.10 Desktop 64bit 沒有 fcitx 輸入法](https://www.ubuntu-tw.org/modules/newbb/viewtopic.php?post_id=359532#forumpost359532)
* [#4 回覆: 關於WIFI 無線網路 RTL8192CU 驅動安裝 softAP](https://www.ubuntu-tw.org/modules/newbb/viewtopic.php?post_id=357248#forumpost357248)


## 相關工具

* [play-apt](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/plan/env-full/play-apt)
