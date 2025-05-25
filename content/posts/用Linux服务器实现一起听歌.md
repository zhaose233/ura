---
title: 用Linux服务器实现一起听歌
date: 2020-10-14 18:09:40


---

# 用服务器一起听歌！

近来用了下QQ的一起听歌功能，感觉挺有意思，但是只能听QQ歌单里有的歌，十分受限。所以决定自己用服务器搭一个差不多的听歌方案。

一起听歌最重要的就是同步，所有人都同时听同一首曲子的同一个地方，这一点和直播很像，所以决定用比较常见的流媒体方式搭建，说白了就是开了一个音频直播。

我用的环境是CentOS7，当然这个教程对别的大部分发行版也适用。需要的软件有ffmpeg和make。

<!--more-->
ffmpeg的安装不多说了，Debian系一般可以直接apt安装，其它发行版编译安装既可。

然后搭建流媒体服务器，用的是SRS，先下载源码包，编译安装：
```linuxshell
wget https://github.com/ossrs/srs/archive/v3.0-r0.tar.gz
tar -zxvf srs-3.0-r0.tar.gz
cd srs-3.0-r0/trunk/
./configure
make
make install
```
然后开启服务：
```linuxshell
ln -sf /usr/local/srs/etc/init.d/srs /etc/init.d/srs
cp -f /usr/local/srs/usr/lib/systemd/system/srs.service /usr/lib/systemd/system/srs.service
systemctl daemon-reload
systemctl start srs
```
如果想开机启动的话：
```linuxshell
systemctl enable srs
```

然后我把要放的音乐都放到了/data下
下面要做的就是开始推流了，用ffmpeg推流：
```linuxshell
 ffmpeg -re -i /data/mymusic.mp3 -f flv -y rtmp://49.234.70.34/live/livestream
```
这时候用vlc或者别的流媒体播放器就可以听音乐了，但是放完一首就会停止，可用性不高，于是我写了一个自动循环的脚本：
```linuxshell
#!/bin/bash
while true
do
	for file in $( ls /data )
	do
		output=`ffmpeg -re -i /data/$file -f flv -y rtmp://49.234.70.34/live/livestream`
	done
done
```
这个脚本会自动播放/data目录下的文件，文件名最好全英文，不然可能出问题。要用的话只要改一下我的ip就行了

然后你就可以用这个流媒体服务器和朋友们一起听任何你想听的歌了！！！

我的一起听歌服务器是rtmp://49.234.70.34/live/livestream，如果卡就是人太多了，自觉退出吧～～～（笑哭）

*by 从晴朗的朝色泛起之际开始*
