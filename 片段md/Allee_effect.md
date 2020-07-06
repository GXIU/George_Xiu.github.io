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





## 有Allee效应的疾病的入侵动力学

在捕猎-被捕猎系统中，两类物种都可以受Allee效应的支配。首先，Allee效应会提升猎物的固有死亡率或者降低猎物的固有出生率，使得个体的自然增长率在人口密度比较低的时候降低。其次，很多捕食者也有可能遇到Allee效应，因为很多猎人会遭遇捕食过程中的非效率。

所以作者设计了一个同质二维环境中的有Allee效应的空间捕获-被捕获系统：
$$
\begin{equation}
\begin{aligned}
&\frac{\partial N(X, Y, T)}{\partial T}=D_{1}\left(\frac{\partial^{2} N}{\partial X^{2}}+\frac{\partial^{2} N}{\partial Y^{2}}\right)+r N\left(1-\frac{N}{K}\right) \frac{N}{N+\alpha_{1}}-a_{N P} N P\\
&\frac{\partial P(X, Y, T)}{\partial T}=D_{2}\left(\frac{\partial^{2} P}{\partial X^{2}}+\frac{\partial^{2} P}{\partial Y^{2}}\right)+\delta a_{N P} N P \frac{P}{P+\alpha_{2}}-E_{P} P
\end{aligned}
\end{equation}
$$
其中第一个方程是猎物的丰富度方程，第二个是捕猎者的丰富度方程；$K$是环境容纳量，$r$是自然增长率，$E_p$是捕猎者的死亡率，$a_{NP}$是攻击率，$\delta$是有效转化率。**重点**：$\frac{N}{N+\alpha_1}$和$\frac{P}{P+\alpha_2}$是猎物和捕猎者的弱Allee效率。

猎物中的疾病传播：SI模型，所以上式的第一个方程被如下方程取代：
$$
\begin{equation}
\begin{array}{c}
\frac{\partial S(X, Y, T)}{\partial T}=D_{1}\left(\frac{\partial^{2} S}{\partial X^{2}}+\frac{\partial^{2} S}{\partial Y^{2}}\right)+r N\left(1-\frac{S}{K}\right) \frac{S}{S+\alpha_{1}} \\
-\frac{\Theta S I}{N+H}-a_{S P} S P \\
\frac{\partial I(X, Y, T)}{\partial T}=D_{1}\left(\frac{\partial^{2} I}{\partial X^{2}}+\frac{\partial^{2} I}{\partial Y^{2}}\right)+\frac{\Theta S I}{N+H}-E_{I} I-a_{I P} I P .
\end{array}
\end{equation}
$$
其中$\Theta$是有效接触率，$H$是搜寻时间，$E_I$是死亡率，$a_{SP}$和$a_{IP}$是攻击率。（一个合理的假设是患病个体不能逃脱，所以假设只有捕食者需要捕猎健康个体的时候才会出现Allee效应）捕猎其实是两个部分：
$$
a_{S P} S P\left(P /\left(P+a_{2}\right)\right)+a_{I P} I P=a_{N P} N P\left(P /\left(P+a_{2}\right)\right)
$$
标准化处理之后，方程可以写成这样：
$$
\begin{array}{l}
\frac{\partial S}{\partial t}=\frac{\partial^{2} S}{\partial x^{2}}+\frac{\partial^{2} S}{\partial y^{2}}+S(1-S) \frac{S}{S+a_{1}}-\frac{\theta S I}{S+I+h}-\alpha S P \\
\frac{\partial I}{\partial t}=\frac{\partial^{2} I}{\partial x^{2}}+\frac{\partial^{2} I}{\partial y^{2}}+\frac{\theta S I}{S+I+h}-e_{i} I-\beta I P \\
\frac{\partial P}{\partial t}=\varepsilon\left(\frac{\partial^{2} P}{\partial x^{2}}+\frac{\partial^{2} P}{\partial y^{2}}\right)+\alpha S P \frac{P}{P+a_{2}}+\beta I P-e_{p} P
\end{array}
$$

#### 两个主题

- 只有健康的猎物有Allee效应($a_1>0$, $a_2=0$)
- 只有捕猎者有Allee效应($a_1=0$, $a_2>0$)