---
title: 在Linux系统上开直播
date: 2020-11-26 19:53:09


---

# 把你的屏幕分享给大家！

大家总是会有想要向别人展示东西的时候。也许是向几个同学，或者几个朋友展示自己的电脑展幕。在种时候用QQ或者Skype等等总是体验不太好，犹其在LINUX上的时候。

<!--more-->

这种时候就把自己的展幕直播出去咯。用到的有一个LINUX系统（笔者用的是ARCH，比较方便，大部分发行版进行改动后都可行），一个带有RTMP模块编译的NGINX服务端，一个内网穿透服务（笔者用的是Sakura FRPC），和OBS录播系统。

先安装NGINX-RTMP，笔者直接使用AUR安装了：
```bash
yay -S nginx-rtmp
```
然后是obs,直接pacman安装
```bash
sudo pacman -S obs-studio
```
启动nginx服务，开启obs进行串流，地址为rtmp://127.0.0.1/live
接着去frpc弄一个账号，进行内网穿透，内网端口就填127.0.0.1:1935，然后把你得到的外网端口改成RTMP格式的连接发给你的小伙伴，他就可以看见你的屏幕了！（RTMP通常使用VLC播放即可，POTPLAYER也可以）

开直播吧

*by 从晴朗的朝色泛起之际开始
