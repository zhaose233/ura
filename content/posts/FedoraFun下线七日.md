---
title: FedoraFun下线七日
date: 2022-02-03 03:56:52


---

# 国内知名 Fedora 社区 FedoraFun 官网今已下线七日

2022年02月03日，正月初三，本应是喜汽洋洋过年的日子，我们却不得不告知一件令人忧伤的事实：**FedoraFun 官网已经下线七天了**

![FedoraFun 官网现状](/images/22-02-03/521.png)

FedoraFun 做为国内较知名的 Fedora 社区之一，致力于填补Fedora于日常易用性上的空白。自创始起就充满活力，在短时间内建成了官网，撰写了教程，搭建了软件仓库。幸运的是，目前软件仓库还能访问。不过上一次更新也已经有段时间了。

![FedoraFun 的软件仓库 repo.fedora.fun 目前仍可访问](/images/22-02-03/new.png)

此次网站的失联问题，外界看来似乎来源于 FedoraFun 创始人兼管理者疏于关心。毕竟创始人本身并未失联，也就是说创始人在明知 FedoraFun 下线的情况下没有恢复网站。但是我们相信这背后是有原因的，于是我们进行了深入的调查。

首先是从创始人本人的方面，现在正值新春佳节，创始人虽是社交能手，但对于新年的各种事项也必定忙于应对。所以才将重建官网一事后延。

![FedoraFun 是一个非常注重私生活的组织，做到了基本保证法定节假日休息](/images/22-02-03/q.jpg)

其实，用于构建 FedoraFun 官网的技术也并非易于理解。FedoraFun 创始人于1月28日晚欲对官网进行改良，但是由于 Nginx 十分不易于配置和使用，最后使得官网无法工作。Nginx是来源于国外的httpc服务器与反代软件，在使用过程中需要编写复杂的配置文件，并且可能含有不稳定的魔法因素。其实用于生成页面的 Hugo 也是如此。然而用于搭建软件仓库的 Onemanager则由国内程序员编写，软件仓库目前运行良好。故创始人此次失败也并非不可理解。

以下是 FedoraFun 从前官网的部分代码：
```HTML
<footer class="site-footer">
    <section class="copyright">
        &copy; 
        
            2021 - 
        
        2022 Fedora生存指难
    </section>
    
    <section class="powerby">
        Built with <a href="https://gohugo.io/" target="_blank" rel="noopener">Hugo</a> <br />
        Theme <b><a href="https://github.com/CaiJimmy/hugo-theme-stack" target="_blank" rel="noopener" data-version="2.5.0">Stack</a></b> designed by <a href="https://jimmycai.com" target="_blank" rel="noopener">Jimmy</a>
    </section>
</footer>
```
可见其中只有几个汉字能够辨认，非常繁杂

所以业内人士认为，综和以上来看，尊重人员的私生活以及法定节假日是值得肯定的行为，那么应当在技术的易用性上下功夫。这也在一定程度上反映了国外技术的不可信，违反直觉，难以使用；更加证明了国产化势在必行。FedoraFun 亦是将国外技术引进的组织之一，也应当更加注重这一点。

于此新春之际，祝愿大家新春快乐，同时，祝愿 FedoraFun 也能从此次变故中涅磐重生，继续作为国内知名技术社区发光发热。

2022-02-03 **刊号2** *——朝色报*
