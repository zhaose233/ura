---
title: 使用开源的软件0成本成为vtuber
date: 2021-09-12 15:14:45

---

vtuber是现今新兴的网络直播/出道方式，能够很方便地塑造一个人设，避免自己露脸的尴尬（

不过很多的vtuber使用的软件都有授权限制，包括live2d也是商业项目

所以！在这里你能够看到0成本的出道方式（硬件还是要成本的，最好有英伟达显卡），不过只能3D出道

项目网址：
 - OpenSeeFace-gd：<https://github.com/you-win/openseeface-gd>
 - OpenSeeFace：<https://github.com/emilianavt/OpenSeeFace>

正文开始～始めるよ～

vtuber软件可以分为两个部分
 - 一个是你看到的跟随实体主播变化的虚拟形像（前端）
 - 用来追踪你的五官或者身体的算法程序（后端）
 
很多商业软件是将这两个部分整合起来的。因为这样更方便使用。

**OpenSeeface-GD的windows发布版本也是整合好的，直接就可以用**
 
朝色使用OpenSeeFace-gd作为前端：
![frontend](/images/front-end.png)
下面的那个godot debug就是正在运行的程序

朝色使用的后端是OpenSeeFace脚本：
![backend](/images/back-end.png)

如果你使用的是Windows系统，直接下截它提供的release即可，当然如果你的网络有点小问题不太方便，这是一个镜像站点的下截链接（写本文时最新）：
 - <https://hub.fastgit.org/you-win/openseeface-gd/releases/download/0.6.0/OpenSeeFace-GD.zip>
 
下截好后解压运行exe即可，如果是linux自行按照readme来吧，挺顺利就弄好了（朝色我用的就是linux呢）
 
之后你只需要点击“run face tracker”开始追踪面部，如果姿势很奇怪的话点setoffset，然后按空格键就可以恢复到正面对着屏幕的姿势。
![error](/images/error.png)
奇奇怪怪的bug

当然如果你现在的人物还是那只小黄鸭的话。。。你自然需要一个其它的模型啦。这个项目支持glb与vrm格式的人物模型。vrm的话有个网站上面有很多，有的甚至可以商用和二次发布。
 - <https://3d.nicovideo.jp>
不知道访问情况如何，当然你也可以制做自己的vrm，steam上有pixiv的制做工具，上手还可以吧，不过linux下的兼容不行，比较麻烦。
 - [VRoid Studio](https://store.steampowered.com/app/1486350/VRoid_Studio_v0140/)
再用Load Model找到你的vrm就行了
![loadmodel](/images/load-model.png)

加截之后如果要调整肢体姿势，在Pose里选上要调的关节，apply一下，用鼠标滚轮就能调啦

至于直播或者录屏的软件，这里推荐一个跨平台开源的软件OBS Studio
![OBS Studio](/images/obs.png)
 - <https://obsproject.com>
或者你也可以从我的云盘下载：
 - [OBS 27.0.1 windows](https://pan.zhaose.cyou/home/Tools/Windows/OBS-Studio-27.0.1-Full-Installer-x64.exe)

如果你还没看过我发在bilibili上的视频可以去看一下噢～

*by 晴朗的朝色泛起之际开始*
 
