---
layout: page
title: 設定「gedit」辨識「Big5」編碼
date: 2018-03-20 15:50:12 +0800
description: >
  設定「gedit」辨識「Big5」編碼。
parent:
  title: 工具的安裝與設定
  url: '/read/howto/install-tool'
source_url: '/read/howto/install-tool/gedit/index.md'
---


## 範例 Script

* [play-ubuntu-18.04-plan/prototype/tool-basic/gedit](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/prototype/tool-basic/gedit)


## 操作步驟

執行

``` sh
$ gsettings set org.gnome.gedit.preferences.encodings candidate-encodings "['UTF-8', 'BIG5', 'BIG5-HKSCS', 'EUC-TW', 'GB18030', 'GB2312', 'GBK', 'CURRENT', 'ISO-8859-15', 'UTF-16']"
```


## 相關討論

* [#3 回覆: GEDIT復製WIN7的TXT檔案打開後變亂碼](https://www.ubuntu-tw.org/modules/newbb/viewtopic.php?post_id=354332#forumpost354332)


## 相關工具

* [play-tool](https://github.com/samwhelp/play-ubuntu-18.04-plan/tree/master/plan/tool-full/play-tool)
