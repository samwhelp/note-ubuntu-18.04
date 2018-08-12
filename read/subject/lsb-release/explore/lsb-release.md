---
layout: page
title: 探索 lsb-release
date: 2018-08-12 14:25:09 +0800
description: >
  探索 lsb-release
parent:
  title: lsb-release
  url: '/read/subject/lsb-release'
source_url: '/read/subject/lsb-release/explore/lsb-release.md'
---

## 套件檔案列表

執行

``` sh
$ dpkg -L lsb-release
```

或是經過排序，執行下面指令

``` sh
$ dpkg -L lsb-release | sort
```

顯示

```
/.
/usr
/usr/bin
/usr/bin/lsb_release
/usr/lib
/usr/lib/python2.7
/usr/lib/python2.7/dist-packages
/usr/lib/python2.7/dist-packages/lsb_release.py
/usr/lib/python3
/usr/lib/python3/dist-packages
/usr/lib/python3/dist-packages/lsb_release.py
/usr/share
/usr/share/bug
/usr/share/bug/lsb-release
/usr/share/doc
/usr/share/doc/lsb-release
/usr/share/doc/lsb-release/changelog.gz
/usr/share/doc/lsb-release/copyright
/usr/share/doc/lsb-release/README.Debian
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/lsb_release.1.gz
/usr/share/pyshared
/usr/share/pyshared/lsb_release.py
```


## man

執行

``` sh
$ dpkg -L lsb-release | grep '/man/man.*/'
```

顯示

```
/usr/share/man/man1/lsb_release.1.gz
```

所以可以執行「$ man [lsb_release](http://manpages.ubuntu.com/manpages/bionic/en/man1/lsb_release.1.html)」來閱讀相關說明。


## bin

執行

``` sh
$ dpkg -L lsb-release | grep '/bin/'
```

顯示

```
/usr/bin/lsb_release
```

執行

``` sh
$ file /usr/bin/lsb_release
```

顯示

```
/usr/bin/lsb_release: Python script, ASCII text executable
```

執行

``` sh
$ grep 'import' /usr/bin/lsb_release -n
```

顯示

```
20:from optparse import OptionParser
21:import sys
22:import os
23:import re
25:import lsb_release

```

執行

``` sh
$ python3 -c 'import lsb_release; print(lsb_release);'
```

顯示

```
<module 'lsb_release' from '/usr/lib/python3/dist-packages/lsb_release.py'>
```

執行

``` sh
$ python -c 'import lsb_release; print(lsb_release);'
```

顯示

```
<module 'lsb_release' from '/usr/lib/python2.7/dist-packages/lsb_release.pyc'>
```

執行

``` sh
$ file /usr/lib/python3/dist-packages/lsb_release.py
```

顯示

```
/usr/lib/python3/dist-packages/lsb_release.py: symbolic link to ../../../share/pyshared/lsb_release.py
```

執行

``` sh
$ file /usr/lib/python2.7/dist-packages/lsb_release		
```

顯示

```
/usr/lib/python2.7/dist-packages/lsb_release.py: symbolic link to ../../../share/pyshared/lsb_release.py
```

執行

``` sh
$ dpkg -L lsb-release | grep python | sort
```

顯示

```
/usr/lib/python2.7
/usr/lib/python2.7/dist-packages
/usr/lib/python2.7/dist-packages/lsb_release.py
/usr/lib/python3
/usr/lib/python3/dist-packages
/usr/lib/python3/dist-packages/lsb_release.py
```

執行

``` sh
$ dpkg -L lsb-release | grep pyshared | sort
```

顯示

```
/usr/share/pyshared
/usr/share/pyshared/lsb_release.py
```

執行

``` sh
$ grep '/etc/lsb-release' /usr/share/pyshared/lsb_release.py -n
```

顯示

```
358:# Whatever is guessed above can be overridden in /etc/lsb-release
361:    etc_lsb_release = os.environ.get('LSB_ETC_LSB_RELEASE','/etc/lsb-release')
```
