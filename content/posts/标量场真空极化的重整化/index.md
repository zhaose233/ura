+++
date = '2025-07-28T03:42:49+08:00'
draft = true
title = '标量场真空极化的重整化'
+++

考虑一个有质量的复标量场 $ \phi $ 和一个无质量的实标量场 $ \chi $ 耦合，总拉氏量可以写作
$$
\mathcal{L} = \partial_\mu \phi^* \, \partial^\mu \phi - m^2\phi^* \phi + {1 \over 2} \partial_\mu \chi \, \partial^\mu \chi - \lambda \phi^* \phi \chi
$$
相应地有费曼规则：
- 顶角： $ - i \lambda $
- $ \phi $ 传播子： $ i\over{p^2 -m^2 + i \epsilon } $
- $ \chi $ 传播子： $ i\over{p^2 + i \epsilon } $

于是我们可以考虑一个简单的 $ \phi - \phi $ 散射过程，

![散射树图](images/pic1.svg)

它的树图振幅可以简单地得到：
$$
\mathcal{M}^{(0)} = -i {\lambda^2 \over q^2} 
$$
还有另外一个交换出射粒子的图，但对于我们研究的主题不重要。

考虑下面的高阶图，$ \chi $ 在传播过程中产生一对虚 $ \phi $ 粒子，

![$ \chi $ 传播圈图](images/pic2.svg)

可以写出这个图的振幅为
$$
\mathcal{M}^{(1)} = {\lambda^4 \over q^4} \int {\mathrm{d}^4 k \over (2\pi)^4} {1 \over {k^2 - m^2 +i \epsilon}} {1 \over {(k-q)^2 - m^2 +i \epsilon}}
$$
立刻会发现这个积分是发散的。积分测度中含有 $ |k|^3 $，使得总的结果以 $ \ln{|k|} $ 的形式发散，这样就没法得到有意义的振幅修正。为了得到有物理意义的结果，需要“把无穷大扫进地毯下面”。

先改写一下这个积分，纯粹为了方便后面的处理。使用如下的等式：
$$
{1 \over {A B}} = \int_0^1 \mathrm{d}x {1 \over {[x A + (1-x) B]^2}} = \int_0^1 \mathrm{d}x \int_0^1 \mathrm{d}y \: \delta(x+y-1) \, {1 \over {[x A + y B]^2}} 
$$
重写后的分母为
$$
\begin{aligned}
D &= x(k^2 - m^2 +i \epsilon) + y[(k-q)^2 - m^2 +i \epsilon] \\
  &= k^2 - 2 y q k + y q^2 - m^2 + i \epsilon \\
  &= (k - yq)^2 + xyq^2 - m^2 + i \epsilon \\
  &= l^2 - \Delta + i \epsilon
\end{aligned}
$$
在第三个等号中使用了 $ x + y = 1 $，最后对 $ k $ 做一个 Shift，做变量替换 $ l = k - yq $ 和 $ \Delta = - xyq^2 + m^2 $，就可以把原积分改写为
$$
\int {\mathrm{d}^4 k \over (2\pi)^4} {1 \over {k^2 - m^2 +i \epsilon}} {1 \over {(k-q)^2 - m^2 +i \epsilon}} = \int_0^1 \mathrm{d}x \int_0^1 \mathrm{d}y \: \delta(x+y-1) \, {1 \over (2\pi)^4} \int {\mathrm{d}^4 l} {1 \over {(l^2 - \Delta + i\epsilon)^2}}
$$
观察这一个积分，其是在闵科夫斯基空间下的四维积分，为了方便地对其应用截断并且方便计算，可以使用 Wick 旋转。
考虑对 $ l^0 $ 的积分：
$$
\int_{-\infty}^{+\infty}\mathrm{d}l^0 {1 \over {[(l^0)^2-|\vec{l}|^2 - \Delta + i \epsilon]^2}}
$$
是一个实积分，然而计算这个积分其实可以看作一个围绕复平面上半平面的围道积分，因为积分函数很显然地在 $ \infty $ 变为 0。于是积分值仅跟极点的留数有关，而上半平面的极点仅有 $ l^0 = -\sqrt{|\vec{l}|^2+\Delta} + i \epsilon $，所以可以把围道改为沿复平面左半平面，也就是说可以改写成沿虚轴的积分：
$$
\int_{-i\infty}^{+i\infty}\mathrm{d}l^0 {1 \over {[(l^0)^2-|\vec{l}|^2 - \Delta + i \epsilon]^2}}
$$
再作一个变量替换 $ i l^4 = l^0 $，就可以得到
$$
\int_{-\infty}^{+\infty}\mathrm{d}l^0 {1 \over {[(l^0)^2-|\vec{l}|^2 - \Delta + i \epsilon]^2}} = -i \int_{-\infty}^{+\infty}\mathrm{d}l^4 {1 \over {[- (l^4)^2 - |\vec{l}|^2 - \Delta + i \epsilon]^2}}
$$
闵科夫斯基空间下的积分也就可以改写欧几里德空间下的积分，这时候扔掉 $ i \epsilon $ 也没关系了，因为极点不在虚轴上：
$$
\int {\mathrm{d}^4 l} {1 \over {(l^2 - \Delta + i\epsilon)^2}} = -i \int {\mathrm{d}^4 \bm{l_E}} {1 \over {(\bm{l_E}^2 + \Delta )^2}}
$$
下面考察四维欧几里德空间的积分，应用四维球坐标，并且对 $ l_E $ 应用一个截断 $ \Lambda $（这个截断是洛伦兹不变的，变换回闵氏空间之后可以看出来，然而如果在上面的闵氏空间中先对 $ l^0 $ 做围道积分再对三维动量作截断的话，那截断就不是洛伦兹不变的）：
$$
\int {\mathrm{d}^4 \bm{l_E}} {1 \over {(\bm{l_E}^2 + \Delta)^2}} =\lim_{\Lambda \to + \infty} \int \mathrm{d}\Omega_4 \int_{0}^{\Lambda}\mathrm{d}l_E {{l_E}^3 \over {({l_E}^2 + \Delta)^2}}
$$
对这个积分可以作换元然后直接求解
$$
\begin{aligned}
\int_{0}^{\Lambda}\mathrm{d}l_E {{l_E}^3 \over {({l_E}^2 + \Delta)^2}} &= {1 \over 2} \int_{0}^{\Lambda}\mathrm{d}{l_E}^2 {{l_E}^2 \over {({l_E}^2 + \Delta)^2}} \\ 
&= {1 \over 2} \int_{0}^{\Lambda}\mathrm{d}{l_E}^2 \left[{1 \over {{l_E}^2 + \Delta}} - {\Delta \over {({l_E}^2 + \Delta)^2}}\right] \\
&= {1 \over 2} \left( \ln{{\Lambda^2 + \Delta} \over \Delta} + {\Lambda^2 \over \Lambda^2  + \Delta} \right)
\end{aligned}
$$
下面到了关键的一步。上式结果的两项中，第一项是对数发散的，我们没法对它做什么，但是第二项在 $ \Lambda \to +\infty $ 时就是 1！把上面的所有结果都代入到一开始的积分里，我们可以得到这个图的振幅为（四维球坐标的方向部分积分为 $ 2 \pi^2 $）：
$$
\mathcal{M}^{(1)} = -i{\lambda^4 \over q^4} {1 \over 16 \pi^2} \left(1+\int_0^1 \mathrm{d}x \int_0^1 \mathrm{d}y \: \delta(x+y-1) \, \ln{{\Lambda^2 + \Delta} \over \Delta}\right) = -i{\lambda^4 \over q^4} {1 \over 16 \pi^2} \left(1+Z\right)
$$
我们把无穷大的常数计为 $ Z $，然后把这个图与一阶的树图相加来得到一个总振幅：
$$
\mathcal{M}=-i{\lambda^2 \over q^2}\left[1+{Z \over {16 \pi^2}} + {\lambda^2 \over 16 \pi^2 q^2}\right]
$$