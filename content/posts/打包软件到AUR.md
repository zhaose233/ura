---
title: 打包软件到AUR
date: 2020-11-12T20:37:50+08:00


---

# 打包软件并共享到AUR

对于Arch Linux的用户来说，AUR软件仓库是常常为人所津津乐道的优势。其优点就在于极大的开放性。那么我们也可以打包软件上传到AUR，从白嫖进化到贡献者！

首先到AUR注册一个账户，并且填入在本机生成的ssh密钥。然后克隆一个空仓库：
```bash
git clone ssh://aur@aur.archlinux.org/gwm-git.git
```
<!--more-->
像这样，然后放入pkgbuild和校验文件
```bash
git add PKGBUILD .SRCINFO
```
然后上传
```bash
git push
```
接着在AUR上就可以看到你的软件了，可以用yay安装了！！
