---
layout: page
title: 探索 pcmanfm-qt
date: 2018-07-03 14:43:26 +0800
description: >
  探索 pcmanfm-qt
parent:
  title: lxqt
  url: '/read/subject/lxqt'
source_url: '/read/subject/lxqt/pcmanfm-qt/explore.md'
---


## 探索原始碼紀錄


## 下載 「Source Package: [pcmanfm-qt](https://packages.ubuntu.com/source/bionic/pcmanfm-qt)」

執行下面指令，下載「Source Package: [pcmanfm-qt](https://packages.ubuntu.com/source/bionic/pcmanfm-qt)」。

[quote]
$ apt-get source pcmanfm-qt

[/quote]

會下載下面三個檔案

* pcmanfm-qt_0.12.0-5.debian.tar.xz
* pcmanfm-qt_0.12.0-5.dsc
* pcmanfm-qt_0.12.0.orig.tar.xz

並且解開到「pcmanfm-qt-0.12.0」這個資料夾。


## --show-pref

執行

``` sh
$ grep 'advanced' pcmanfm-qt-0.12.0/* -R
```

顯示

```
pcmanfm-qt-0.12.0/pcmanfm/mainwindow.cpp:            app->preferences("advanced");
pcmanfm-qt-0.12.0/pcmanfm/preferencesdialog.h:    // activePage is the name of page to select (general, display, advanced...)
pcmanfm-qt-0.12.0/pcmanfm/desktop-preferences.ui:     <widget class="QWidget" name="advancedPage">
pcmanfm-qt-0.12.0/pcmanfm/desktop-preferences.ui:      <layout class="QVBoxLayout" name="advancedPageLayout">
pcmanfm-qt-0.12.0/pcmanfm/desktoppreferencesdialog.cpp:  ui.advancedPageLayout->insertWidget(1, desktopFolderWidget);
pcmanfm-qt-0.12.0/pcmanfm/application.cpp:        preferences("advanced");
pcmanfm-qt-0.12.0/pcmanfm/preferences.ui:       <widget class="QWidget" name="advancedPage">
```

執行

``` sh
$ grep 'QWidget' pcmanfm-qt-0.12.0/pcmanfm/preferences.ui -n
```

顯示

```
76:       <widget class="QWidget" name="behaviorPage">
215:       <widget class="QWidget" name="displayPage">
451:       <widget class="QWidget" name="uiPage">
638:       <widget class="QWidget" name="thumbnailPage">
698:       <widget class="QWidget" name="volumePage">
768:       <widget class="QWidget" name="advancedPage">
```

從上面的模式，推論有如下的方式可以執行。

``` sh
$ pcmanfm-qt --show-pref=behavior
$ pcmanfm-qt --show-pref=display
$ pcmanfm-qt --show-pref=ui
$ pcmanfm-qt --show-pref=thumbnail
$ pcmanfm-qt --show-pref=volume
$ pcmanfm-qt --show-pref=advanced
```

執行

``` sh
$ grep 'selectPage' pcmanfm-qt-0.12.0/pcmanfm/preferencesdialog.cpp -n
```

顯示

```
45:    selectPage(activePage);
376:void PreferencesDialog::selectPage(QString name) {
```

執行

``` sh
$ grep 'selectPage' pcmanfm-qt-0.12.0/pcmanfm/preferencesdialog.cpp -n -A 9
```

顯示

```
45:    selectPage(activePage);
46-    adjustSize();
47-}
48-
49-PreferencesDialog::~PreferencesDialog() {
50-
51-}
52-
53-static void findIconThemesInDir(QHash<QString, QString>& iconThemes, QString dirName) {
54-    QDir dir(dirName);
--
376:void PreferencesDialog::selectPage(QString name) {
377-    if(!name.isEmpty()) {
378-        QWidget* page = findChild<QWidget*>(name + "Page");
379-        if(page) {
380-            int index = ui.stackedWidget->indexOf(page);
381-            ui.listWidget->setCurrentRow(index);
382-        }
383-    }
384-}
385-
```
