---
title: 给picom开启高性能模糊透明
date: 2020-12-04 16:44:14


---

# picom混成器模糊透明来了！

使用windows manager的图形界面的话，如果不想忍受单薄的画面，当然少不了一个窗口混成器。现在kwin，mutter这些集成在DE里面的wm都整合了混成器。但是像i3这种wm，就需要一个外置混成器来撑撑排面了。

<!--more-->

现在比较流行的是picom，能够提供不亚于kwin之类的淡入淡出，透明效果，但是模糊背景一直表现不佳。从前的模糊方案只有kernel，能直接通占用10%以上的CPU。然而现在有了新的模糊方案了以后性能有了大幅的提升！

archlinux先填加archlinuxcn源：
```ini
[archlinuxcn]
SigLevel = Optional TrustAll
Server = https://mirrors.ustc.edu.cn/archlinuxcn/$arch
```
其它发行版可以自行从github下载源码安装。

在archlinux下
```bash
sudo pacman -S picom-git
```
然后将以下内容填加到picom.conf里：
```ini
 blur:
{
  method = "dual_kawase";
  size = 10;
  strength = 3;
  deviation = 5.0;
};
```
用picom --experimental-backends开启picom可以享受背景模糊了！

*by 从晴朗的朝色泛起之际开始
