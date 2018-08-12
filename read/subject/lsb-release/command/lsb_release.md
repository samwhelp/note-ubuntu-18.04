---
layout: page
title: lsb_release
date: 2018-08-12 14:25:09 +0800
description: >
  lsb_release
parent:
  title: lsb-release
  url: '/read/subject/lsb-release'
source_url: '/read/subject/lsb-release/command/lsb_release.md'
---


## Manpage

執行下面指令，閱讀「[lsb_release](http://manpages.ubuntu.com/manpages/bionic/en/man1/lsb_release.1.html)」的相關使用說明。

``` sh
$ man lsb_release
```


## Help

執行

``` sh
$ lsb_release -h
```

或是執行

``` sh
$ lsb_release --help
```

顯示

```
Usage: lsb_release [options]

Options:
  -h, --help         show this help message and exit
  -v, --version      show LSB modules this system supports
  -i, --id           show distributor ID
  -d, --description  show description of this distribution
  -r, --release      show release number of this distribution
  -c, --codename     show code name of this distribution
  -a, --all          show all of the above information
  -s, --short        show requested information in short format
```

## All

執行

``` sh
$ lsb_release -a
```

或是執行

``` sh
$ lsb_release --all
```

顯示

```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 18.04.1 LTS
Release:	18.04
Codename:	bionic
```

## /etc/lsb-release

可以對照「/etc/lsb-release」這個檔案來探索。

執行

``` sh
$ cat /etc/lsb-release
```

顯示

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.1 LTS"
```

## ID

執行

``` sh
$ lsb_release -i
```

或是執行

``` sh
$ lsb_release --id
```

顯示

```
Distributor ID:	Ubuntu
```

加上「short參數」

執行

``` sh
$ lsb_release -i -s
```

或是執行

``` sh
$ lsb_release --id --short
```

顯示

```
Ubuntu
```

## RELEASE

執行

``` sh
$ lsb_release -r
```

或是執行

``` sh
$ lsb_release --release
```

顯示

```
Release:	18.04
```

加上「short參數」

執行

``` sh
$ lsb_release -r -s
```

或是執行

``` sh
$ lsb_release --release --short
```

顯示

```
18.04
```

## CODENAME

執行

``` sh
$ lsb_release -c
```

或是執行

``` sh
$ lsb_release --codename
```

顯示

```
Codename:	bionic
```

加上「short參數」

執行

``` sh
$ lsb_release -c -s
```

或是執行

``` sh
$ lsb_release --codename --short
```

顯示

```
bionic
```

## DESCRIPTION

執行

``` sh
$ lsb_release -d
```

或是執行

``` sh
$ lsb_release --description
```

顯示

```
Description:	Ubuntu 18.04.1 LTS
```

加上「short參數」

執行

``` sh
$ lsb_release -d -s
```

或是執行

``` sh
$ lsb_release --description --short
```

顯示

```
Ubuntu 18.04.1 LTS
```


## 相關套件

* [lsb-release](https://packages.ubuntu.com/bionic/lsb-release)
* [distro-info-data](https://packages.ubuntu.com/bionic/distro-info-data)
* [base-files](https://packages.ubuntu.com/bionic/base-files)


## 應用案例

執行

``` sh
$ grep 'lsb_release' /usr/sbin/dkms -n
```

顯示

```
392:    elif type lsb_release >/dev/null 2>&1; then
393:        DISTRIB_ID=$(lsb_release -i -s)
394:        DISTRIB_RELEASE=$(lsb_release -r -s)
408:            if [[ $(lsb_release -d -s) =~ Enterprise ]]; then
```

執行

``` sh
$ grep 'distro_version(' /usr/sbin/dkms -n -A 39
```

顯示

```
384:distro_version()
385-{
386-    # What distribution are we running?
387-    local LSB_DESCRIPTION DISTRIB_ID DISTRIB_RELEASE ver
388-
389-    # Try the LSB-provided strings first
390-    if [ -r /etc/lsb-release ]; then
391-        . /etc/lsb-release
392-    elif type lsb_release >/dev/null 2>&1; then
393-        DISTRIB_ID=$(lsb_release -i -s)
394-        DISTRIB_RELEASE=$(lsb_release -r -s)
395-    fi
396-
397-    case ${DISTRIB_ID} in
398-        Fedora)
399-            echo fc${DISTRIB_RELEASE}
400-            ;;
401-        RedHatEnterprise*|CentOS|ScientificSL)
402-            # OEL also reports as such; format is 4.7, 5.3
403-            ver=$(echo "${DISTRIB_RELEASE}" | \
404-            sed -e 's/^\([[:digit:]]*\).*/\1/g')
405-            echo el${ver}
406-            ;;
407-        SUSE*)
408-            if [[ $(lsb_release -d -s) =~ Enterprise ]]; then
409-                echo sles${DISTRIB_RELEASE}
410-            else
411-                echo suse${DISTRIB_RELEASE}
412-            fi
413-            ;;
414-        *)
415-            if [[ ${DISTRIB_ID} && ${DISTRIB_RELEASE} ]]; then
416-                echo "${DISTRIB_ID}${DISTRIB_RELEASE}"
417-            else
418-                distro_version_rpm
419-            fi
420-            ;;
421-    esac
422-}
423-
```
