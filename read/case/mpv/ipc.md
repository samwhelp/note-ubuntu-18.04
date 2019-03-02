---
layout: page
title: mpv ipc
date: 2019-02-23 13:19:17 +0800
description: >
  mpv ipc。
parent:
  title: 討論案例
  url: '/read/case'
source_url: '/read/case/mpv/ipc.md'
---




以下內容本來要回覆這篇「[mpv播放影片控制時間問題請教](https://www.ubuntu-tw.org/modules/newbb/viewtopic.php?post_id=360634#forumpost360634)」，

不過因為我目前登入前可以看到文章列表，登入後無法看到文章列表，

所以也就無法回覆，也無法回文，只剩登出的功能。

因此先紀錄在這，以防時間久了，我又忘記回文這件事了。

:-)

================================================================================

剛剛在觀看「smplayer」的[原始碼](https://packages.ubuntu.com/source/bionic/smplayer)，

然後執行下面指令，來對照著看

================================================================================

先開啟一個「Terminal」，執行下面指令，使用「[smplayer](http://manpages.ubuntu.com/manpages/bionic/en/man1/smplayer.1.html)」來播放「~/Videos/test.mp4」。

```
$ smplayer ~/Videos/test.mp4
```

接著在另一個「Terminal」執行下面指令

```
$ ps aux | grep mpv
```

顯示

```
user      13273 63.0  1.4 1885268 121832 pts/2  Sl+  09:30   0:13 /usr/bin/mpv --no-config --no-quiet --terminal --no-msg-color <span style="color:red;">--input-file</span>=<span style="color:blue;">/dev/stdin</span> --no-fs --hwdec=no --sub-auto=fuzzy --no-input-default-bindings --input-vo-keyboard=no --no-input-cursor --cursor-autohide=no --no-keepaspect --wid=65011731 --monitorpixelaspect=1 --osd-level=1 --osd-scale=1 --osd-bar-align-y=0.6 --sub-ass --embeddedfonts --sub-ass-line-spacing=0 --sub-scale=1 --sub-font=Arial --sub-color=#ffffffff --sub-shadow-color=#ff000000 --sub-border-color=#ff000000 --sub-border-size=0.75 --sub-shadow-offset=2.5 --sub-font-size=50 --sub-bold=no --sub-italic=no --sub-codepage=ISO-8859-1 --vid=1 --sub-pos=100 --volume=57 --cache=auto --start=82 --screenshot-template=cap_%F_%p_%02n --screenshot-format=jpg --screenshot-directory=/home/user/Pictures/smplayer_screenshots --audio-pitch-correction=yes --volume-max=110 --term-playing-msg=MPV_VERSION=${=mpv-version:} INFO_VIDEO_WIDTH=${=width} INFO_VIDEO_HEIGHT=${=height} INFO_VIDEO_ASPECT=${=video-aspect} INFO_VIDEO_FPS=${=container-fps:${=fps}} INFO_VIDEO_FORMAT=${=video-format} INFO_VIDEO_CODEC=${=video-codec} INFO_AUDIO_FORMAT=${=audio-codec-name} INFO_AUDIO_CODEC=${=audio-codec} INFO_AUDIO_RATE=${=audio-params/samplerate} INFO_AUDIO_NCH=${=audio-params/channel-count} INFO_LENGTH=${=duration:${=length}} INFO_DEMUXER=${=current-demuxer:${=demuxer}} INFO_SEEKABLE=${=seekable} INFO_TITLES=${=disc-titles} INFO_CHAPTERS=${=chapters} INFO_TRACKS_COUNT=${=track-list/count} METADATA_TITLE=${metadata/by-key/title:} METADATA_ARTIST=${metadata/by-key/artist:} METADATA_ALBUM=${metadata/by-key/album:} METADATA_GENRE=${metadata/by-key/genre:} METADATA_DATE=${metadata/by-key/date:} METADATA_TRACK=${metadata/by-key/track:} METADATA_COPYRIGHT=${metadata/by-key/copyright:} INFO_MEDIA_TITLE=${=media-title:} INFO_STREAM_PATH=${stream-path}  --audio-client-name=SMPlayer --term-status-msg=STATUS: ${=time-pos} / ${=duration:${=length:0}} P: ${=pause} B: ${=paused-for-cache} I: ${=core-idle} VB: ${=video-bitrate:0} AB: ${=audio-bitrate:0} /home/user/Videos/test.mp4

```

上面這段，我之前有在「[#1 關於「m3u」和「mpv」和「smplayer」的操作使用](https://www.ubuntu-tw.org/modules/newbb/viewtopic.php?post_id=357582#forumpost357582)」有提到過。

================================================================================

接著在上面發現一個參數「--input-file=/dev/stdin」，引起我的注意

一開始先執行「$ man [mpv](http://manpages.ubuntu.com/manpages/bionic/en/man1/mpv.1.html#options)」，使用「[--input-file](https://mpv.io/manual/stable/#options-input-file)」當關鍵字，找到下面的敘述。

```

--input-file=<filename>
	   Read commands from the given file. Mostly useful with a FIFO. Since mpv 0.7.0  also
	   understands  JSON commands (see JSON IPC), but you can't get replies or events. Use
	   --input-ipc-server for something bi-directional. On MS Windows, JSON  commands  are
	   not available.

	   This  can  also  specify a direct file descriptor with fd://N (UNIX only).  In this
	   case, JSON replies will be written if the FD is writable.

	   NOTE:
		  When the given file is a FIFO mpv opens both ends, so you can  do  several  echo
		  "seek 10" > mp_pipe and the pipe will stay valid.

```

================================================================================

接著在網路上找相關文章，使用「[mpv --input-file](https://www.google.com.tw/search?q=mpv+--input-file)」當關鍵字查詢，找到一篇「[參考文章](https://brontosaurusrex.github.io/2017/10/11/running-mpv-as-biatch/)」。

================================================================================

## 方式一

先開啟一個「Terminal」，執行下面指令

```
mkfifo /tmp/mpv-fifo

mpv --input-file=/tmp/mpv-fifo --idle
```

接著開啟另一個「Terminal」，執行下面指令

```
echo 'loadfile https://www.youtube.com/watch?v=Lqe3MuCyh9o' > /tmp/mpv-fifo
```

稍等一下，就會看到「mpv」播放「[影片](https://www.youtube.com/watch?v=Lqe3MuCyh9o)」。

接著回到樓主原本提的需求，執行下面指令

```
echo 'seek 00:01:00 absolute' > /tmp/mpv-fifo
```

就可以下指令，控制「mpv」從「00:01:00」開始播放影片。

## 相關參考連結

* $ man [mkfifo](http://manpages.ubuntu.com/manpages/bionic/en/man1/mkfifo.1.html)
* [https://mpv.io/manual/stable/#options-input-file](https://mpv.io/manual/stable/#options-input-file)
* <a href="https://mpv.io/manual/stable/#command-interface-[relative|absolute|absolute-percent|relative-percent|exact|keyframes]">https://mpv.io/manual/stable/#command-interface-[relative|absolute|absolute-percent|relative-percent|exact|keyframes]</a>
* [https://github.com/mpv-player/mpv/blob/master/DOCS/man/options.rst](https://github.com/mpv-player/mpv/blob/master/DOCS/man/options.rst)
* [https://github.com/mpv-player/mpv/blob/master/DOCS/man/input.rst](https://github.com/mpv-player/mpv/blob/master/DOCS/man/input.rst)

================================================================================

## 方式二

先執行下面指令，安裝「[socat](https://packages.ubuntu.com/bionic/socat)」

```
$ sudo apt-get install socat
```

先開啟一個「Terminal」，執行下面指令

```
mpv --input-ipc-server=/tmp/mpv-pipe --idle
```

接著開啟另一個「Terminal」，執行下面指令

```
echo '{"command": ["loadfile", "https://www.youtube.com/watch?v=Lqe3MuCyh9o"]}' | socat - /tmp/mpv-pipe
```

會收到

```
{"data":null,"error":"success"}
```

稍等一下，就會看到「mpv」播放「[影片](https://www.youtube.com/watch?v=Lqe3MuCyh9o)」。

接著回到樓主原本提的需求，執行下面指令

```
echo '{"command": ["seek", "00:01:00", "absolute"]}' | socat - /tmp/mpv-pipe
```

就可以下指令，控制「mpv」從「00:01:00」開始播放影片。


## 相關參考連結

* [https://mpv.io/manual/master/#options-input-ipc-server](https://mpv.io/manual/master/#options-input-ipc-server)
* <a href="https://mpv.io/manual/stable/#command-interface-[relative|absolute|absolute-percent|relative-percent|exact|keyframes]">https://mpv.io/manual/stable/#command-interface-[relative|absolute|absolute-percent|relative-percent|exact|keyframes]</a>
* [https://github.com/mpv-player/mpv/blob/master/DOCS/man/options.rst](https://github.com/mpv-player/mpv/blob/master/DOCS/man/options.rst)
* [https://github.com/mpv-player/mpv/blob/master/DOCS/man/input.rst](https://github.com/mpv-player/mpv/blob/master/DOCS/man/input.rst)
* [https://github.com/mpv-player/mpv/blob/master/DOCS/man/ipc.rst](https://github.com/mpv-player/mpv/blob/master/DOCS/man/ipc.rst)

================================================================================

執行

```
mpv --input-cmdlist
```

顯示

```

ignore
seek                 Time [Flags] [Choice]
revert-seek          [Flags]
quit                 [Integer]
quit-watch-later     [Integer]
stop
frame-step
frame-back-step
playlist-next        [Choice]
playlist-prev        [Choice]
playlist-shuffle
sub-step             Integer
sub-seek             Integer
print-text           String
show-text            String [Integer] [Integer]
expand-text          String
show-progress
sub-add              String [Choice] [String] [String]
sub-remove           [Integer]
sub-reload           [Integer]
tv-last-channel
screenshot           [Flags] [Choice]
screenshot-to-file   String [Choice]
screenshot-raw       [Choice]
loadfile             String [Choice] Key/value list
loadlist             String [Choice]
playlist-clear
playlist-remove      Choice
playlist-move        Integer Integer
run                  String String
set                  String String
add                  String [Double]
cycle                String [up|down]
multiply             String Double
cycle-values         String String String
enable-section       String [Flags]
disable-section      String
define-section       String String [Choice]
ab-loop
drop-buffers
af                   String String
af-command           String String String
ao-reload
vf                   String String
vf-command           String String String
script-binding       String
script-message       String
script-message-to    String String
overlay-add          Integer Integer Integer String Integer String Integer Integer Integer
overlay-remove       Integer
write-watch-later-co
hook-add             String Integer Integer
hook-ack             String
mouse                Integer Integer [Integer] [Choice]
keypress             String
keydown              String
keyup                [String]
audio-add            String [Choice] [String] [String]
audio-remove         [Integer]
audio-reload         [Integer]
rescan-external-file [Choice]
apply-profile        String
load-script          String


```

================================================================================

執行

```
mpv -h
```

或是

```
mpv --help
```

顯示

```
Usage:   mpv [options] [url|path/]filename

Basic options:
 --start=<time>    seek to given (percent, seconds, or hh:mm:ss) position
 --no-audio        do not play sound
 --no-video        do not play video
 --fs              fullscreen playback
 --sub-file=<file> specify subtitle file to use
 --playlist=<file> specify playlist file

 --list-options    list all mpv options
 --h=<string>      print options which contain the given string in their name

```

================================================================================

其他範例如下

執行

```
mpv --list-options
```

執行

```
mpv --h=input-file
```

執行

```
mpv --h=input-ipc-server
```

執行

```
mpv --h=idle
```

執行

```
mpv --h=list
```

執行

```
mpv --list-properties
```

執行

```
mpv --list-protocols
```

執行

```
mpv --list-protocols
```

執行

```
mpv --input-cmdlist
```

執行

```
mpv --input-keylist
```

執行

```
mpv --h=cache
```

執行

```
$ mpv --cache-secs=600 'https://www.youtube.com/watch?v=Lqe3MuCyh9o'
```

================================================================================

上面「方式一」，可以簡化成下面步驟

先開啟一個「Terminal」，執行下面指令

```
mkfifo /tmp/mpv-fifo

mpv --input-file=/tmp/mpv-fifo --cache-secs=600 'https://www.youtube.com/watch?v=Lqe3MuCyh9o'
```

接著執行下面指令

```
echo 'seek 00:01:00 absolute' > /tmp/mpv-fifo
```

就可以下指令，控制「mpv」從「00:01:00」開始播放影片。

================================================================================

以上提供參考，

報告完畢

:-)
