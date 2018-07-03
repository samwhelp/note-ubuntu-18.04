---
layout: page
title: pcmanfm-qt 基本操作
date: 2018-07-03 19:03:17 +0800
description: >
  pcmanfm-qt 基本操作
parent:
  title: lxqt
  url: '/read/subject/lxqt'
source_url: '/read/subject/lxqt/pcmanfm-qt/usage.md'
---


## Manpage

執行下面指令，閱讀關於「[pcmanfm-qt](http://manpages.ubuntu.com/manpages/bionic/en/man1/pcmanfm-qt.1.html)」這個指令的說明。

``` sh
$ man pcmanfm-qt
```


## Help

或是執行下面指令，了解到有那些相關的參數。


``` sh
$ pcmanfm-qt -h
```

或是執行

``` sh
$ pcmanfm-qt -help
```

顯示

```
Usage: pcmanfm-qt [options] [FILE1, FILE2,...]

Options:
  -h, --help                  Displays this help.
  -v, --version               Displays version information.
  -p, --profile <PROFILE>     Name of configuration profile
  -d, --daemon-mode           Run PCManFM as a daemon
  -q, --quit                  Quit PCManFM
  --desktop                   Launch desktop manager
  --desktop-off               Turn off desktop manager if it's running
  --desktop-pref <NAME>       Open desktop preference dialog on the page with
                              the specified name
  -n, --new-window            Open new window
  -f, --find-files            Open Find Files utility
  -w, --set-wallpaper <FILE>  Set desktop wallpaper from image FILE
  --wallpaper-mode <MODE>     Set mode of desktop wallpaper.
                              MODE=(color|stretch|fit|center|tile|zoom)
  --show-pref <NAME>          Open Preferences dialog on the page with the
                              specified name

Arguments:
  files                       Files or directories to open
```


## Version

執行

``` sh
$ pcmanfm-qt -v
```

或是執行

``` sh
$ pcmanfm-qt --version
```

顯示

```
pcmanfm-qt 0.12.0
```


## --show-pref

執行下面指令，就會啟動一個設定視窗，標題是「Preferences」，並且切換到第一個頁簽「Behavior」。

``` sh
$ pcmanfm-qt --show-pref=behavior
```

執行下面指令，就會啟動一個設定視窗，標題是「Preferences」，並且切換到第二個頁簽「Display」。

``` sh
$ pcmanfm-qt --show-pref=display
```

執行下面指令，就會啟動一個設定視窗，標題是「Preferences」，並且切換到第三個頁簽「User Interface」。

``` sh
$ pcmanfm-qt --show-pref=ui
```

執行下面指令，就會啟動一個設定視窗，標題是「Preferences」，並且切換到第四個頁簽「Thumbnail」。

``` sh
$ pcmanfm-qt --show-pref=thumbnail
```

執行下面指令，就會啟動一個設定視窗，標題是「Preferences」，並且切換到第五個頁簽「Volume」。

``` sh
$ pcmanfm-qt --show-pref=volume
```

執行下面指令，就會啟動一個設定視窗，標題是「Preferences」，並且切換到第六個頁簽「Advanced」。

``` sh
$ pcmanfm-qt --show-pref=advanced
```


## 開啟目前資料夾

執行

``` sh
$ pcmanfm-qt
```

或是執行

``` sh
$ pcmanfm-qt .
```


## -n

執行

``` sh
$ pcmanfm-qt -n ~/Desktop/ ~/Music/ ~/Downloads
```

執行上面指令，開新視窗，因為上面後面參數有接「~/Desktop/ ~/Music/ ~/Downloads」。

所以會出現三個頁簽，各個頁簽分別切換到「~/Desktop/」，「~/Music/」，「~/Downloads」這三個資料夾。


## -f

執行

``` sh
$ pcmanfm-qt -f ~/Desktop/ ~/Music/ ~/Downloads
```

執行上面指令，就會啟動一個視窗，標題是「Search Files」，

並且在「Places to Search」那，列入上面三個搜尋路徑。


## Open File

執行

``` sh
$ pcmanfm-qt ~/Documents/demo.txt
```

執行上面的指令，就會用預設的應用程式開啟「~/Documents/demo.txt」這個檔案。


## --quit

執行

``` sh
$ pcmanfm-qt --quit
```

執行上面指令，會將所有的「pcmanfm-qt」關閉，包含「desktop」。
