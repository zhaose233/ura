+++
date = '2025-07-28T03:42:49+08:00'
draft = true
title = '标量场传播子的重整化'
+++

---

考虑一个有质量的复标量场 $ \phi $ 和一个无质量的实标量场 $ \chi $ 耦合，总拉氏量可以写作
$$
\mathcal{L} = \partial_\mu \phi^* \, \partial^\mu \phi - m^2\phi^* \phi + {1 \over 2} \partial_\mu \chi \, \partial^\mu \chi - \lambda \phi^* \phi \chi
$$
相应地有费曼规则：
- 顶角： $ - i \lambda $
- $ \phi $ 传播子： $ i\over{p^2 -m^2 + i \epsilon } $
- $ \chi $ 传播子： $ i\over{p^2 + i \epsilon } $

于是我们可以考虑一个简单的 $ \phi - \phi $ 散射过程，

它的树图振幅可以简单地得到：
$$
\mathcal{M}^{(0)} = -i {\lambda^2 \over q^2} 
$$
还有另外一个交换出射粒子的图，但对于我们研究的主题不重要。

考虑下面的高阶图，$ \chi $ 在传播过程中产生一对虚 $ \phi $ 粒子，

可以写出这个图的振幅为
$$
\mathcal{M}^{(1)} = {\lambda^4 \over q^4} \int {\mathrm{d}^4 k \over (2\pi)^4} {1 \over {k^2 - m^2 +i \epsilon}} {1 \over {(k-q)^2 - m^2 +i \epsilon}}
$$
立刻会发现这个积分是发散的。积分测度中含有 $ |k|^3 $，使得总的结果以 $ \ln{|k|} $ 的形式发散，这样就没法得到有意义的振幅修正。为了得到有物理意义的结果，需要“把无穷大扫进地毯下面”。

先改写一下这个积分，纯粹为了方便后面的处理。使用如下的等式：
$$
{1 \over {A B}} = \int_0^1 \mathrm{d}x {1 \over {[x A + (1-x) B]^2}} = \int_0^1 \mathrm{d}x \int_0^1 \mathrm{d}y \: \delta(x+y-1) \, {1 \over {[x A + y B]^2}} 
$$