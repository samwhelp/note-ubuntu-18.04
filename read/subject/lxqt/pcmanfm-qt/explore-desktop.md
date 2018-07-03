---
layout: page
title: 探索 pcmanfm-qt (Desktop)
date: 2018-07-03 14:43:26 +0800
description: >
  探索 pcmanfm-qt (Desktop)
parent:
  title: lxqt
  url: '/read/subject/lxqt'
source_url: '/read/subject/lxqt/pcmanfm-qt/explore-desktop.md'
---


## 探索跟 Desktop 功能相關的原始碼紀錄

執行

``` sh
$ dpkg -L pcmanfm-qt
```

顯示

```
/.
/etc
/etc/xdg
/etc/xdg/autostart
/etc/xdg/autostart/lxqt-desktop.desktop
/usr
/usr/bin
/usr/bin/pcmanfm-qt
/usr/share
/usr/share/applications
/usr/share/applications/pcmanfm-qt-desktop-pref.desktop
/usr/share/applications/pcmanfm-qt.desktop
/usr/share/doc
/usr/share/doc/pcmanfm-qt
/usr/share/doc/pcmanfm-qt/AUTHORS
/usr/share/doc/pcmanfm-qt/README.md
/usr/share/doc/pcmanfm-qt/changelog.Debian.gz
/usr/share/doc/pcmanfm-qt/copyright
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/pcmanfm-qt.1.gz
/usr/share/pcmanfm-qt
/usr/share/pcmanfm-qt/lxqt
/usr/share/pcmanfm-qt/lxqt/settings.conf
```

## Desktop

執行

``` sh
$ dpkg -L pcmanfm-qt | grep desktop
```

顯示

```
/etc/xdg/autostart/lxqt-desktop.desktop
/usr/share/applications/pcmanfm-qt-desktop-pref.desktop
/usr/share/applications/pcmanfm-qt.desktop
```

執行

``` sh
$ grep '^Exec=' /usr/share/applications/pcmanfm-qt-desktop-pref.desktop
```

顯示

```
Exec=pcmanfm-qt --desktop-pref=general
```

執行下面指令，觀看「[pcmanfm-qt](http://manpages.ubuntu.com/manpages/bionic/en/man1/pcmanfm-qt.1.html)」的使用說明。

``` sh
$ man pcmanfm-qt
```

可以執行的有三種

```
$ pcmanfm-qt --desktop-pref=general
$ pcmanfm-qt --desktop-pref=bg
$ pcmanfm-qt --desktop-pref=advanced
```

## 下載 「Source Package: [pcmanfm-qt](https://packages.ubuntu.com/source/bionic/pcmanfm-qt)」

執行下面指令，下載「Source Package: [pcmanfm-qt](https://packages.ubuntu.com/source/bionic/pcmanfm-qt)」。

``` sh
$ apt-get source pcmanfm-qt
```

會下載下面三個檔案

* pcmanfm-qt_0.12.0-5.debian.tar.xz
* pcmanfm-qt_0.12.0-5.dsc
* pcmanfm-qt_0.12.0.orig.tar.xz

並且解開到「pcmanfm-qt-0.12.0」這個資料夾。


## --desktop-pref

執行下面指令，找尋跟「general」相關的檔案。

``` sh
$ grep 'general' pcmanfm-qt-0.12.0/* -R -n
```

顯示

```
pcmanfm-qt-0.12.0/Doxyfile.in:1313:# save some trees in general.
pcmanfm-qt-0.12.0/Doxyfile.in:1406:# save some trees in general.
pcmanfm-qt-0.12.0/LICENSE:256:of promoting the sharing and reuse of software generally.
pcmanfm-qt-0.12.0/pcmanfm/preferencesdialog.h:36:    // activePage is the name of page to select (general, display, advanced...)
pcmanfm-qt-0.12.0/pcmanfm/desktop-preferences.ui:22:     <widget class="QWidget" name="generalPage">
pcmanfm-qt-0.12.0/pcmanfm/pcmanfm-qt-desktop-pref.desktop.in:6:Exec=pcmanfm-qt --desktop-pref=general
```

使用「QWidget」當關鍵字，在「pcmanfm-qt-0.12.0/pcmanfm/desktop-preferences.ui」這個檔案探索。

``` sh
$ grep 'QWidget' pcmanfm-qt-0.12.0/pcmanfm/desktop-preferences.ui -n
```

顯示

```
22:     <widget class="QWidget" name="generalPage">
313:     <widget class="QWidget" name="bgPage">
451:     <widget class="QWidget" name="advancedPage">
```

也就是剛剛提到的，可以執行三種指令。

```
$ pcmanfm-qt --desktop-pref=general
$ pcmanfm-qt --desktop-pref=bg
$ pcmanfm-qt --desktop-pref=advanced
```

執行下面指令，找尋跟「selectPage」相關的檔案。

``` sh
$ grep 'selectPage' pcmanfm-qt-0.12.0/* -R
```

顯示

```
pcmanfm-qt-0.12.0/pcmanfm/desktoppreferencesdialog.h:40:  void selectPage(QString name);
pcmanfm-qt-0.12.0/pcmanfm/preferencesdialog.h:42:    void selectPage(QString name);
pcmanfm-qt-0.12.0/pcmanfm/preferencesdialog.cpp:45:    selectPage(activePage);
pcmanfm-qt-0.12.0/pcmanfm/preferencesdialog.cpp:376:void PreferencesDialog::selectPage(QString name) {
pcmanfm-qt-0.12.0/pcmanfm/desktoppreferencesdialog.cpp:248:void DesktopPreferencesDialog::selectPage(QString name) {
pcmanfm-qt-0.12.0/pcmanfm/application.cpp:447:    desktopPreferencesDialog_.data()->selectPage(page);
pcmanfm-qt-0.12.0/pcmanfm/application.cpp:556:        preferencesDialog_.data()->selectPage(page);
```

使用「selectPage」當關鍵字，在「pcmanfm-qt-0.12.0/pcmanfm/desktoppreferencesdialog.cpp」這個檔案探索。


``` sh
$ grep 'selectPage' pcmanfm-qt-0.12.0/pcmanfm/desktoppreferencesdialog.cpp -n
```

顯示

```
248:void DesktopPreferencesDialog::selectPage(QString name) {
```

執行

```
$ grep 'selectPage' pcmanfm-qt-0.12.0/pcmanfm/desktoppreferencesdialog.cpp -n -A 5
```

顯示

```
248:void DesktopPreferencesDialog::selectPage(QString name) {
249-  QWidget* page = findChild<QWidget*>(name + "Page");
250-  if(page)
251-    ui.tabWidget->setCurrentWidget(page);
252-}
253-
```

執行

``` sh
$ grep 'selectPage' pcmanfm-qt-0.12.0/pcmanfm/application.cpp -n
```

顯示

```
447:    desktopPreferencesDialog_.data()->selectPage(page);
556:        preferencesDialog_.data()->selectPage(page);
```

執行

``` sh
$ grep 'selectPage' pcmanfm-qt-0.12.0/pcmanfm/application.cpp -n -B 8 -A 5
```

顯示

```
439-void Application::desktopPrefrences(QString page) {
440-    // show desktop preference window
441-    if(!desktopPreferencesDialog_) {
442-        desktopPreferencesDialog_ = new DesktopPreferencesDialog();
443-
444-        // Should be used only one time
445-        desktopPreferencesDialog_->setEditDesktopFolder(!lxqtRunning_);
446-    }
447:    desktopPreferencesDialog_.data()->selectPage(page);
448-    desktopPreferencesDialog_.data()->show();
449-    desktopPreferencesDialog_.data()->raise();
450-    desktopPreferencesDialog_.data()->activateWindow();
451-}
452-
--
548-}
549-
550-void Application::preferences(QString page) {
551-    // open preference dialog
552-    if(!preferencesDialog_) {
553-        preferencesDialog_ = new PreferencesDialog(page);
554-    }
555-    else {
556:        preferencesDialog_.data()->selectPage(page);
557-    }
558-    preferencesDialog_.data()->show();
559-    preferencesDialog_.data()->raise();
560-    preferencesDialog_.data()->activateWindow();
561-}
```

執行

``` sh
$ grep 'desktopPrefrences' pcmanfm-qt-0.12.0/pcmanfm/application.cpp -n
```

顯示

```
230:            desktopPrefrences(parser.value(desktopPrefOption));
277:            iface.call("desktopPrefrences", parser.value(desktopPrefOption));
439:void Application::desktopPrefrences(QString page) {
```

執行

``` sh
$ grep 'desktopPrefrences' pcmanfm-qt-0.12.0/pcmanfm/application.cpp -n -A 2 -B 1
```

顯示

```
229-        if(parser.isSet(desktopPrefOption)) { // desktop preference dialog
230:            desktopPrefrences(parser.value(desktopPrefOption));
231-            keepRunning = true;
232-        }
--
276-        if(parser.isSet(desktopPrefOption)) { // desktop preference dialog
277:            iface.call("desktopPrefrences", parser.value(desktopPrefOption));
278-        }
279-        else if(parser.isSet(findFilesOption)) { // file searching utility
--
438-
439:void Application::desktopPrefrences(QString page) {
440-    // show desktop preference window
441-    if(!desktopPreferencesDialog_) {
```

執行

``` sh
$ grep 'desktopPrefOption' pcmanfm-qt-0.12.0/pcmanfm/application.cpp -n
```

顯示

```
185:    QCommandLineOption desktopPrefOption("desktop-pref", tr("Open desktop preference dialog on the page with the specified name"), tr("NAME"));
186:    parser.addOption(desktopPrefOption);
229:        if(parser.isSet(desktopPrefOption)) { // desktop preference dialog
230:            desktopPrefrences(parser.value(desktopPrefOption));
276:        if(parser.isSet(desktopPrefOption)) { // desktop preference dialog
277:            iface.call("desktopPrefrences", parser.value(desktopPrefOption));
```

執行

``` sh
$ grep 'desktopPrefOption' pcmanfm-qt-0.12.0/pcmanfm/application.cpp -n -A 2 -B 1
```

顯示

```
184-
185:    QCommandLineOption desktopPrefOption("desktop-pref", tr("Open desktop preference dialog on the page with the specified name"), tr("NAME"));
186:    parser.addOption(desktopPrefOption);
187-
188-    QCommandLineOption newWindowOption(QStringList() << "n" << "new-window", tr("Open new window"));
--
228-
229:        if(parser.isSet(desktopPrefOption)) { // desktop preference dialog
230:            desktopPrefrences(parser.value(desktopPrefOption));
231-            keepRunning = true;
232-        }
--
275-
276:        if(parser.isSet(desktopPrefOption)) { // desktop preference dialog
277:            iface.call("desktopPrefrences", parser.value(desktopPrefOption));
278-        }
279-        else if(parser.isSet(findFilesOption)) { // file searching utility
```


## DBus

執行

``` sh
$ qdbus | grep lxqt
```

顯示

```
 org.lxqt.global_key_shortcuts
 org.lxqt.lxqt-runner
 org.lxqt.lxqt-powermanagement
 org.lxqt.session
```

執行

``` sh
$ qdbus org.lxqt.session
```

顯示

```
/
/LXQtSession
```

執行

``` sh
$ qdbus org.lxqt.session /LXQtSession
```

顯示

```
method bool org.lxqt.session.canLogout()
method bool org.lxqt.session.canPowerOff()
method bool org.lxqt.session.canReboot()
method QDBusVariant org.lxqt.session.listModules()
method Q_NOREPLY void org.lxqt.session.logout()
signal void org.lxqt.session.moduleStateChanged(QString moduleName, bool state)
method Q_NOREPLY void org.lxqt.session.powerOff()
method Q_NOREPLY void org.lxqt.session.reboot()
method Q_NOREPLY void org.lxqt.session.startModule(QString name)
method Q_NOREPLY void org.lxqt.session.stopModule(QString name)
method QDBusVariant org.freedesktop.DBus.Properties.Get(QString interface_name, QString property_name)
method QVariantMap org.freedesktop.DBus.Properties.GetAll(QString interface_name)
signal void org.freedesktop.DBus.Properties.PropertiesChanged(QString interface_name, QVariantMap changed_properties, QStringList invalidated_properties)
method void org.freedesktop.DBus.Properties.Set(QString interface_name, QString property_name, QDBusVariant value)
method QString org.freedesktop.DBus.Introspectable.Introspect()
method QString org.freedesktop.DBus.Peer.GetMachineId()
method void org.freedesktop.DBus.Peer.Ping()
```

執行

``` sh
$ qdbus org.lxqt.session /LXQtSession org.lxqt.session.listModules
```

顯示

```
:lxqt-confupdate.desktop
lxqt-desktop.desktop
lxqt-globalkeyshortcuts.desktop
lxqt-notifications.desktop
lxqt-panel.desktop
lxqt-policykit-agent.desktop
lxqt-powermanagement.desktop
lxqt-runner.desktop
```

執行

``` sh
$ qdbus org.lxqt.session /LXQtSession org.lxqt.session.stopModule 'lxqt-desktop.desktop'
```

執行

``` sh
$ qdbus org.lxqt.session /LXQtSession org.lxqt.session.startModule 'lxqt-desktop.desktop'
```

執行

``` sh
$ dpkg -S lxqt-desktop.desktop
```

```
pcmanfm-qt: /etc/xdg/autostart/lxqt-desktop.desktop
```

執行

```
$ ls /etc/xdg/autostart/lxqt* -1
```

顯示

```
/etc/xdg/autostart/lxqt-desktop.desktop
/etc/xdg/autostart/lxqt-globalkeyshortcuts.desktop
/etc/xdg/autostart/lxqt-notifications.desktop
/etc/xdg/autostart/lxqt-panel.desktop
/etc/xdg/autostart/lxqt-policykit-agent.desktop
/etc/xdg/autostart/lxqt-powermanagement.desktop
/etc/xdg/autostart/lxqt-qlipper-autostart.desktop
/etc/xdg/autostart/lxqt-runner.desktop
/etc/xdg/autostart/lxqt-xscreensaver-autostart.desktop
```

執行

``` sh
$ grep 'X-LXQt-Module' /etc/xdg/autostart/* -R -n
```

顯示

```
/etc/xdg/autostart/lxqt-desktop.desktop:7:X-LXQt-Module=true
/etc/xdg/autostart/lxqt-globalkeyshortcuts.desktop:7:X-LXQt-Module=true
/etc/xdg/autostart/lxqt-notifications.desktop:7:X-LXQt-Module=true
/etc/xdg/autostart/lxqt-panel.desktop:7:X-LXQt-Module=true
/etc/xdg/autostart/lxqt-policykit-agent.desktop:7:X-LXQt-Module=true
/etc/xdg/autostart/lxqt-powermanagement.desktop:9:X-LXQt-Module=true
/etc/xdg/autostart/lxqt-runner.desktop:7:X-LXQt-Module=true
```


## 下載 「Source Package: [lxqt-session](https://packages.ubuntu.com/source/bionic/lxqt-session)」

執行下面指令，下載「Source Package: [lxqt-session](https://packages.ubuntu.com/source/bionic/lxqt-session)」。

``` sh
$ apt-get source lxqt-session
```

會下載下面三個檔案

* lxqt-session_0.12.0-5.debian.tar.xz
* lxqt-session_0.12.0-5.dsc
* lxqt-session_0.12.0.orig.tar.xz

並且解開到「lxqt-session-0.12.0」這個資料夾。

執行

```
$ grep 'listModules' lxqt-session-0.12.0/* -R -n
```

顯示

```
lxqt-session-0.12.0/lxqt-config-session/modulemodel.cpp:59:    QDBusReply<QVariant> reply = mInterface->call("listModules");
lxqt-session-0.12.0/lxqt-session/src/lxqtmodman.cpp:271:QStringList LXQtModuleManager::listModules() const
lxqt-session-0.12.0/lxqt-session/src/sessiondbusadaptor.h:97:    QDBusVariant listModules()
lxqt-session-0.12.0/lxqt-session/src/sessiondbusadaptor.h:99:        return QDBusVariant(m_manager->listModules());
lxqt-session-0.12.0/lxqt-session/src/lxqtmodman.h:88:    QStringList listModules() const;
```

執行

``` sh
$ grep 'listModules' lxqt-session-0.12.0/lxqt-session/src/lxqtmodman.cpp -n -A 4
```

顯示
```
271:QStringList LXQtModuleManager::listModules() const
272-{
273-    return QStringList(mNameMap.keys());
274-}
275-
```

執行

``` sh
$ grep 'mNameMap' lxqt-session-0.12.0/lxqt-session/src/lxqtmodman.cpp -n
```

顯示

```
244:    mNameMap[name] = proc;
252:    if (!mNameMap.contains(name))
267:    if (mNameMap.contains(name))
268:        mNameMap[name]->terminate();
273:    return QStringList(mNameMap.keys());
321:    mNameMap.remove(proc->fileName);
336:    ModulesMapIterator i(mNameMap);
345:        mNameMap[i.key()] = nullptr;
357:    ModulesMapIterator i(mNameMap);
```
