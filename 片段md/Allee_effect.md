## Allee 效应



你就有时候会发现很多概念都是相关的，比如在看Grenfell, B., Bjørnstad, O. & Kappey, J. Travelling waves and spatial hierarchies in measles epidemics. *Nature* **414,** 716–723 (2001). https://doi.org/10.1038/414716a 这一篇的时候就偶然间发现了这样一个概念 critical community size，很像最近想做的Allee效应的主题。这个概念引子更古老的一篇文献：Bartlett, M. (1960). The Critical Community Size for Measles in the United States. *Journal of the Royal Statistical Society. Series A (General),* *123*(1), 37-44. doi:10.2307/2343186 [PDF](https://www.jstor.org/stable/pdf/2343186.pdf?refreqid=excelsior%3A8b718b75a5e4633091a524237af85adf). 



考虑两个相关的城镇，都有着双年的麻疹周期。进一步假设一个城市够大，超过CCS（大约是300,000），另一个城市规模比CCS小。我们有：

- 在一次大型流行病之后，S的密度构成了一个确定性的阈值，在阈值之上的话，另一场大流行就会到来。
- 在大城镇中，麻疹依然会地区性地不时出现，所以只要有效$R_0$在某一瞬间超过$1$时，疫情就会马上爆发。这个阈值与适龄儿童的积累有关系，并且用季节性传染率来修正。
- 小城市：在epidemic后$I$在局部消失，所以，另一个大流行只会在接收到infective spark的时候出现，通常来自于更大的城镇。

作者给出了下面三个假设：

- 大小城镇的空间镶嵌（spatial mosaic）对疾病的时滞有影响，如果有一组小城镇在大城市周围，那就会生成层次性的流行病行波。
- 作为推论，大城市的组合（都在CCS之上），就会生成高度同步的流行病。因为非线性相会锁住季节性增强的震荡子。
- 最后，弱耦合的/距离较远的中心应该有更强的倾向来进入相反的双年吸引子。

### TSIR框架

对偶映射格子，在时刻$n+1$, 流行病的强度$\lambda_{n+1}$又下式给定
$$
\lambda_{n+1} = \beta_n S_n (I_n + \theta_n)^\alpha,
$$
其中，$\beta_n$是季节传染率，$\alpha$是混合率，$\theta_n$是（随机）接触率，假设是泊松分布$\text{Poi}(m\bar{I}_n).$的，$m$是空间耦合率，$\bar{I_n}$是上一个时刻邻居们染病的数量。这样的话，疾病生灭过程就由下面的负二项分布刻画：
$$
I_{n+1} \sim NegBin(\lambda_{n+1},I_n).
$$
健康人的平衡方程就是$S_{n+1} = S_n +B-I_{n+1}$. 

