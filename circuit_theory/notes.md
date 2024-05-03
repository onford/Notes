<style>
    h1,h2{
        border-bottom : none;
        font-family: "Times New Roman","宋体";
    }
    p,div{
        font-family: "Times New Roman","宋体";
        font-size:17px;
    }
    bw{
        font-family: "Times New Roman","仿宋";
        font-size:17px;
    }
    st{
        font-family:"Times New Roman","宋体";
        color: red;
    }
    blockquote{
        font-family:"Times New Roman","仿宋";
        font-size:17px;
        border-left: 5px solid #ccc;
    }
    table,th,td{
        font-size:17px;
        font-family:"Times New Roman","宋体";
        border: 1px solid;
        text-align:center;
    }
    caption{
        font-family:"Times New Roman","黑体";
        font-size:17px;
    }
    img{
        margin: 0 auto;
        left:50%;
        right:50%;
        width: 30%;
    }
</style>

# 电路理论笔记

<bw>wr按：\
这一部笔记，主要记录学习过程中的一些想法，以便后续查看时能回忆起当时的理解，并加深印象。实际上并不全面，只是自己想到的一些东西。当然也有可能是错误的，仅供参考。</bw>

## $Chapter1$&emsp;电路模型与基本定律
**一、电路变量与元件**\
&emsp;&emsp;对包括电源在内的各种电路器件而言，当$u,i$选择**关联**的参考方向时，$p=ui$就是**吸收功率**。对于非直流电路，严格来说是**瞬时**吸收功率。\
&emsp;&emsp;课本上的四种受控电源都是**有源元件**，能够提供功率。这个功率来自受控源本身，课本上也没有详细说明受控源提供的能量来自哪里。是像电池一样储存在受控源内部的能量吗？事实上课本上的受控源是高度抽象的电路模型，不需要过多地纠结。\
**二、基尔霍夫定律**\
&emsp;&emsp;电路的基本定律就是基尔霍夫定律，其中包含基尔霍夫电流定律（KCL）和基尔霍夫电压定律（KVL）。\
&emsp;&emsp;**基尔霍夫电流定律**：集中参数电路中，任何时刻流入一个结点（或者一个闭合面）的支路电流的代数和为$0$.也即：
$$\sum _{k=1}^b i _k=0\tag{1.1}$$

&emsp;&emsp;这个实际上就是<st>电流连续性方程</st>。这里没有位移电流项，因为在电路里不能把类似电容这样的元器件拆开来看作两个极板，要整体地看成一个器件。\
&emsp;&emsp;**基尔霍夫电压定律**：集中参数电路中，任何时刻，任意一个回路中所有支路电压代数和为$0$.即：
$$\sum _{k=1}^b u _k=0\tag{1.2}$$
## $Chapter2$&emsp;电阻电路等效变换
&emsp;&emsp;等效变换的意义是在**不改变端口$u-i$关系**的前提下，简化电路的结构。对于电源支路，电流源串联其它元件，与串联元件被短路后等效；电压源并联其它元件，与并联元件被断路后等效。\
**一、星形电路和三角形电路**\
&emsp;&emsp;如果是对称电路的话，问题就很好解决。假设端口$ab$为上下方向，有下表。
<table align="center">
<caption align="top">表 对称电路的电压与电流</caption>
    <tr>
        <th>对称方式</th>
        <td>对称面过端口</td>
        <td>对称面垂直端口</td>
    </tr>
    <tr>
        <th>电流关系</th>
        <td>对称的支路电流相等<br>$$i _L=i _R$$</td>
        <td>所有经过对称面的支路，电流为$0$</td>
    </tr>
    <tr>
        <th>电压关系</th>
        <td>关于对称面对称的点，电势相同</td>
        <td>对称面上所有点的电势都为<br>$$\varphi=\cfrac{\varphi _a+\varphi _b}{2}$$</td>
    </tr>
</table>

&emsp;&emsp;如果不是对称电路，一般就需要用到星-三角互换。\
&emsp;&emsp;**$\Delta\rightarrow \mathrm Y$**：
$$\begin{cases}R _1=\cfrac{R _{12}R _{31}}{R _{12}+R _{23}+R _{31}}\\\\
R _2=\cfrac{R _{23}R _{12}}{R _{12}+R _{23}+R _{31}}\\\\
R _3=\cfrac{R _{23}R _{31}}{R _{12}+R _{23}+R _{31}}\end{cases}\tag{2.1}$$ 

&emsp;&emsp;规律是$R _k=\cfrac{连于k结点的两个电阻之积}{\Delta\text{内三个电阻之和}\qquad\qquad }$.\
&emsp;&emsp;**$\mathrm Y\rightarrow \Delta$**：
$$\begin{cases}G _{12}=\cfrac{G _1G _2}{G _1+G _2+G _3}\\\\
G _{23}=\cfrac{G _2G _3}{G _1+G _2+G _3}\\\\
G _{31}=\cfrac{G _3G _1}{G _1+G _2+G _3}\end{cases}\tag{2.2}$$

&emsp;&emsp;规律是$G _{kj}=\cfrac{\text{连于}k\text{、连于}j\text{结点的两个电导之积}}{\text{Y内三个电导之和}}$.\
**二、电源变换**\
&emsp;&emsp;主要就是诺顿支路与戴维南支路相互变换。\
&emsp;&emsp;**诺顿$\rightarrow$戴维南**：$(I _s)\parallel (R)\rightarrow (U _s=I _s\cdot R)+R$\
&emsp;&emsp;**戴维南$\rightarrow$诺顿**：$(U _s)+(R)\rightarrow(I _s=U _s/R)\parallel(R)$\
&emsp;&emsp;变换之后还需要注意，变换前后电压源、电流源的方向相反（类似于非关联）。如果是控制源，也可以按照这样的规则变换。但是要达到最简等效电路的话，必须要把控制源变换成电阻。
<blockquote>
&emsp;&emsp;当受控源的$u-i$关系（关联参考方向）满足$u/i=R _c$（其中$R _c$时常量）时，就可以用一个大小为$R _c$的电阻等效替换这个受控源。$R _c$与一般的电阻不同，极有可能是负值，也有可能是$0$.
</blockquote>

## $Chapter3$&emsp;电路分析方程
&emsp;&emsp;用基尔霍夫定律，方程多，变量也多。所以考虑使用**结点方程**或**网孔方程**。\
**一、结点方程**\
&emsp;&emsp;结点方程，其实是在KCL方程组中，用<strong>结点电势$u _\mathrm n$消去支路电流$i$</strong>得到的。先标记结点$u _{\mathrm n0}$的电势为$0$，其他结点分别记为$u _{\mathrm n1\cdots\mathrm na}$.快速列写为方程$(3.1)$所示：
$$\begin{bmatrix}G _{11}&\cdots& G _{1a}\\\\
\vdots&\ddots&\vdots\\\\
G _{a1}&\cdots&G _{aa}\end{bmatrix}\begin{bmatrix}u _{\mathrm n1}\\\\
\vdots\\\\u _{\mathrm na}
\end{bmatrix}=\begin{bmatrix}i _{\mathrm{Sn}1}\\\\
\vdots\\\\ i _{\mathrm{Sn}a}\end{bmatrix}\tag{3.1}$$

&emsp;&emsp;$G _{kk}$是与结点$k$相连所有支路的电导之和，称为结点$k$的自电导。$G _{kj}(k\neq j)$是结点$k,j$之间支路电导的<st>相反数</st>，称为$k,j$结点的互电导。$i _{\mathrm{Sn}k}$是由电流源<st>流入</st>结点$k$的电流代数和。\
&emsp;&emsp;由此就可以解出结点$k$的电势$u _{\mathrm nk}$.\
&emsp;&emsp;使用节点方程前，要注意以下两种情况：\
&emsp;&emsp;1.先简化电源支路，以免干扰电导矩阵的列写。\
&emsp;&emsp;2.戴维南支路应全部转化为诺顿支路。
<blockquote>&emsp;&emsp;所谓简化电源支路，指的是以下两种情况：电流源串联了一个电阻，或者电压源并联了一个电阻。根据电源支路的等效变换，我们应直接把电阻给删了，以免后面出现不必要的麻烦。<br>
&emsp;&emsp;但是，如果要求电路中相应电源的功率的话，在解完结点方程后，还应把电路还原。
</blockquote>


&emsp;&emsp;使用节点方程的时候，对于电源支路的处理：\
&emsp;&emsp;1.支路上只有电流源，不参与电导矩阵的列写。\
&emsp;&emsp;2.支路上只有电压源。\
&emsp;&emsp;&emsp;&emsp;a.如果支路连接到结点$\mathrm n _0$，直接得出支路另一个结点的电势，其它结点正常列写方程，合计方程个数仍为$a$个。\
&emsp;&emsp;&emsp;&emsp;b.支路不连接到$\mathrm n _0$，应该把电压源支路的两个端头结点合并成一个广义结点，再弥补一个电压方程：比如电压源$u _s$的升压方向为结点$j\rightarrow k$，把$j,k$看作广义节点，再弥补一个方程$u _{\mathrm nk}-u _{\mathrm nj}=u _s$，合计方程个数仍为$a$个。\
**二、网孔方程**\
&emsp;&emsp;网孔方程，其实是在KVL方程组中，用<strong>网孔电流$i _m$消去各元件的电压$u$</strong>得到的。假设网孔电流设为$i _{\mathrm m1\cdots\mathrm mb}$.快速列写为方程$(3.2)$所示：
$$\begin{bmatrix}R _{11}&\cdots&R _{1b}\\\\
\vdots&\ddots&\vdots\\\\
R _{b1}&\cdots&R _{bb}\end{bmatrix}\begin{bmatrix}i _{\mathrm m1}\\\\
\vdots\\\\
i _{\mathrm mb}
\end{bmatrix}=\begin{bmatrix}
u _{\mathrm{Sm}1}\\\\
\vdots\\\\
u _{\mathrm{Sm}b}
\end{bmatrix}\tag{3.2}$$

&emsp;&emsp;$R _{kk}$是网孔$k$内所有支路的电阻之和，称为网孔$k$的自电阻。$R _{kj}(k\neq j)$是网孔$k,j$的公共支路电阻的<st>相反数</st>，称为网孔$k,j$的互电阻。$u _{\mathrm{Sn}k}$是沿着网孔$k$的电流方向电压源<st>升压</st>代数和。\
&emsp;&emsp;由此就可以解出网孔$k$的电流$i _{\mathrm mk}$.
<blockquote>
    &emsp;&emsp;教材上，默认了所有网孔电流的参考方向都是顺时针方向。其实每个网孔电流的方向都可以随意规定，只要列写方程时满足$u _\mathrm{Sn}$的书写规则（沿网孔电流方向<strong>升压</strong>），解出来的$i _\mathrm m$就是当前参考方向的网孔电流值。
</blockquote>

&emsp;&emsp;使用网孔方程前，要注意一下两种情况：\
&emsp;&emsp;1.先简化电路，同结点方程列写时的处理。\
&emsp;&emsp;2.诺顿支路应全部转化为戴维南支路。\
&emsp;&emsp;使用节点方程的时候，对于电源支路的处理：\
&emsp;&emsp;1.支路上只有电压源，不参与电阻矩阵的列写。\
&emsp;&emsp;2.支路上只有电流源。\
&emsp;&emsp;&emsp;&emsp;a.如果支路在电路边缘（只有一个网孔电流经过它），直接得出该网孔的电流，其它网孔正常列写方程，合计方程个数仍为$b$个。\
&emsp;&emsp;&emsp;&emsp;b.支路不在网孔边缘，应该把电流源支路两边的网孔合并成一个广义网孔，再弥补一个电流方程：比如电流源$i _s$支路被网孔$j,k$的电流经过，网孔$j$的电流与电流源是关联方向，网孔$k$的电流与电流源是非关联方向，把$j,k$看作广义网孔，再弥补一个方程$i _{\mathrm mj}-i _{\mathrm mk}=i _s$，合计方程个数仍为$b$个。\
&emsp;&emsp;网孔法无法应用于**非平面电路**。

## $Chapter4$&emsp;电路定理
**一、叠加定理与替代定理**\
&emsp;&emsp;**叠加定理**：线性电阻电路中，多个独立电源共同激励下的响应，等于独立电源单独激励下相应的代数和。\
&emsp;&emsp;线性电阻电路的相应和激励又是**齐次线性关系**，所以叠加定理可以表述为下式：
$$i(\mathrm{or\ } u)=\sum _{j=1}^n k _ju _{\mathrm sj}+\sum _{j=1}^mk'_ji _{\mathrm sj}\tag{3.3}$$

&emsp;&emsp;“齐次”表现在式$(3.3)$等号右边没有加上什么常数。只要确定所有系数$k$，响应就能够由各个电源的参数表示。
<blockquote>
&emsp;&emsp;如果要求$k _t$，可以把除电压源$u _{\mathrm st}$之外的电源全部置零，在置零后的电路中，就有$i(\mathrm{or\ }u)=k _tu _{\mathrm st}$，从而求出系数$k _t$.每一个系数都可以这样求。<br>
&emsp;&emsp;电压源置零相当于将其短路，电流源置零相当于将其断路。
</blockquote>

&emsp;&emsp;**替代定理**：在任何电路中，如果某条支路$k$的电压为$u _k$，则支路可以用电压源$ u _k$替代；如果支路$k$的电流为 $i _k$，则支路可用电流源$i _k$替代。在原电路和替换后电路<st>均具有唯一解</st>的条件下，两个电路的工作状态相同。\
**二、戴维南定理和诺顿定理**\
&emsp;&emsp;这两个定理都是对一端口**含电源**线性电阻网络的等效变化。戴维南定理将网络等效变换为戴维南电路，诺顿定理将网络等效变换为诺顿电路。\
&emsp;&emsp;**戴维南定理**：含有独立电源的一端口线性电阻网络，对端口以外的电路 而言，等效为<st>由电压源$u _{\mathrm{OC}}$和电阻$R _\mathrm{eq}$串联</st>的戴维南支路，称为戴维南等效电路。其中$u _\mathrm{OC}$是网络的<st>端口开路电压</st>，$R _\mathrm{eq}$是网络内部全部置零后的<st>端口等效电阻</st>。\
&emsp;&emsp;**诺顿定理**：含有独立电源的一端口线性电阻网络，对端口以外的电路而言，等效为<st>由电流源$i _\mathrm{SC}$和电阻$R _\mathrm{eq}$并联</st>的诺顿支路，称为诺顿等效电路。其中$i _\mathrm{SC}$是<st>端口短路电流</st>，$R _\mathrm{eq}$是网络内部独立电源全部置零后的端口等效电阻。
<blockquote>
&emsp;&emsp;一般碰到的电路都是由独立电压（电流）源、受控源、电阻组成的，这样的电路都是线性电阻网络，都可以使用上面两个定理。<br>
&emsp;&emsp;在用戴维南定理求$u _\mathrm{OC}$时，如果网络内部只有一个独立电源，可以运用基尔霍夫定律或者电路方程求解。当网络中出现<strong>多个独立电源</strong>的时，运用叠加定理，分别对单个独立电源激励的情况求解。在用诺顿定理求$i _\mathrm{SC}$时也是如此。<br>
&emsp;&emsp;上面两个定理求$R _\mathrm{eq}$时，都是在松弛网络里求解的。所谓松弛网络，就是网络中所有电源置零后得到的网络。松弛网络可能是纯电阻网络，这种情况挺好求解的,使用$Chapter2$中的方法。当松弛网络中<strong>含有受控源</strong>的时候，要通过写出端口的$u-i$关系求$R _\mathrm{eq}$.
</blockquote>

**三、最大功率传输定理**\
&emsp;&emsp;求某线性电阻网络中可变电阻$R$的最大传输功率，一般将电路中$R$外的一端口网络等效为戴维南支路，当$R$等于$R _\mathrm{eq}$时，获得最大功率$P _\mathrm{max}=\cfrac{U _\mathrm{OC}^2}{4R _\mathrm{eq}}$.

## $Chapter7$&emsp;电容、电感及动态电路
**一、广义函数**\
**1.单位阶跃函数**\
&emsp;&emsp;为了动态电路表示的需要，定义了一些特殊的函数。首先是单位阶跃函数：
$$\varepsilon(t)=\begin{cases}1& t > 0,\\\\0&t < 0.\end{cases}\tag{7.1}$$

&emsp;&emsp;函数在$t=0$处无定义，并且函数值在这里从$0$跳到$1$.阶跃函数有一些性质，比如$\varepsilon(t)+\varepsilon(-t)=1$.可以拓展为对$t$的任意函数$f(t)$，有：
$$\varepsilon(f(t))+\varepsilon(-f(t))=1\tag{7.2}$$

&emsp;&emsp;式$(7.2)$在这一章后面的计算、化简中经常会用到。\
**2.闸门函数**\
&emsp;&emsp;闸门函数的定义：
$$G(t _1,t _2)=\begin{cases}1&t _1< t < t _2,\\\\0& t < t _1\mathrm{\ or\ }t > t _2.\end{cases}\tag{7.3}$$
<blockquote>
&emsp;&emsp;$G(t _1,t _2)$其实是一种极致的简写，这样的写法甚至省略了自变量，只保留函数参数。一般闸门函数$G$的自变量就是$t$，也许写成$G(t,t _1,t _2)$更严谨一些。
</blockquote>

&emsp;&emsp;在$t _1\leq t _2$的情况下（一般不会跑出这种情况），$G(t _1,t _2)$满足：
$$G(t _1,t _2)=\varepsilon(t-t _1)-\varepsilon(t-t _2)=\varepsilon(t-t _1)\times\varepsilon(t _2-t)\tag{7.4}$$

&emsp;&emsp;为了避免高次项的出现，我们一般采用前一个等号。
<blockquote>
&emsp;&emsp;我们可以定义这样的式子：$\varepsilon(t+\infty)=\varepsilon(+\infty)=1,\varepsilon(t-\infty)=\varepsilon(-\infty)=0$.这样可以获得闸门函数的两种特殊情况：
$$\begin{aligned}G(-\infty,t _2)&=\varepsilon(t+\infty)-\varepsilon(t-t _2)=1-\varepsilon(t -t _2)=\varepsilon(t _2-t)\\
G(t _1,+\infty)&=\varepsilon(t-t _1)-\varepsilon(t _2-\infty)=\varepsilon(t-t _1)\end{aligned}\tag{7.5}$$
&emsp;&emsp;定义这两个式子可以方便一些解题。比如将$u=\begin{cases}2&t < 0\\
-5&0 < t <1\\
0& t > 1\end{cases}$写成广义函数，就可以这样：
$$\begin{aligned}u&=2G(-\infty,0)-5G(0,1)+0G(1,+\infty)\\
&=2\varepsilon(-t)-5[\varepsilon(t)-\varepsilon(t-1)]+0\\
&=2\varepsilon(-t)-5\varepsilon(t)+5\varepsilon(t-1)\end{aligned}\tag{7.6}$$
</blockquote>

**3.单位冲激函数**\
&emsp;&emsp;单位冲激函数$\delta(t)$定义如下：
$$\begin{cases}\begin{aligned}&\delta(t)=0,t\neq 0\\\\
&\int_{-\infty}^{+\infty}\delta(t)\mathrm dt=1\end{aligned}\end{cases}\tag{7.7}$$

&emsp;&emsp;可以理解为函数在$x=0$处取到了一个无穷大的值，$\delta(t)$超出了普通函数的范畴。它和$\varepsilon(t)$之间的关系为：
$$\begin{aligned}&\delta(t)=\cfrac{\mathrm d\varepsilon(t)}{\mathrm dt}&\varepsilon(t)=\int _{-\infty}^t\delta(t)\mathrm dt\\\\
&\delta(t-t _0)=\cfrac{\mathrm d\varepsilon(t-t _0)}{\mathrm dt}&\varepsilon(t-t _0)=\int _{-\infty}^t\delta(t-t _0)\mathrm dt\end{aligned}\tag{7.8}$$

**4.广义函数的运算**\
&emsp;&emsp;根据式$(7.8)$，可以比较容易地对具有$\varphi(t)\varepsilon(t-t _0)$形式的函数进行微分。一般不涉及到冲激函数$\delta(t)$的微分。\
&emsp;&emsp;冲激函数的<st>筛分性</st>比较重要：
$$f(t)\delta(t-t _0)=f(t _0)\delta(t-t _0)\tag{7.9}$$

&emsp;&emsp;依据式$(7.9)$可以进行具有$\varphi(t)\delta(t-t _0)$形式的函数进行积分：
$$\int _a^bf(t)\delta(t-t _0)\mathrm dt=\int _a^bf(t _0)\delta(t-t _0)\mathrm dt=f(t _0)\int _a^b\delta(t-t _0)\mathrm dt\tag{7.10}$$

&emsp;&emsp;对具有$\varphi(t)\varepsilon(t-t _0)$形式的函数进行的积分：
$$\int _{-\infty}^t\varphi(t)\varepsilon(t-t _0)\mathrm dt=\varepsilon(t-t _0)\int _{t _0}^t\varphi(t)\mathrm dt\tag{7.11}$$

**二、电容**\
&emsp;&emsp;储存电场能量的元件，$q=Cu$.其$u-i$关系：
$$\begin{aligned}& i=\cfrac{\mathrm dq}{\mathrm dt}=\cfrac{\mathrm d(Cu)}{\mathrm dt}=C\cfrac{\mathrm du}{\mathrm dt}\\\\
& u(t)=u(0 _-)+\cfrac{1}{C}\int _{0 _-}^ti\mathrm dt\end{aligned}\tag{7.12}$$

**1.电容串联**\
&emsp;&emsp;$n$个电容为$C _k$，初始电压为$u _{k0}(k=1,2,\cdots ,n)$的电容器，按照相同电压方向**串联**，得到一个电容为$C _\mathrm{eq}$，初始电压为$u _0$的等效电容：
$$u _0=\sum _{k=1}^nu _{k0}\qquad \cfrac{1}{C _\mathrm{eq}}=\sum _{k=1}^n\cfrac{1}{C _k}\tag{7.13}$$

&emsp;&emsp;如果等效电容两端的电压变为$u'$，那么电压的变化量$\Delta u=u'-u _0$以电容的倒数为权重，分给这$n$个电容：
$$u _k'=u _{k0}+\Delta u _k=u _{k0}+(u'-u _0)\cfrac{C _k^{-1}}{\sum\limits _{l=1}^nC _l^{-1}}\tag{7.14}$$

**2.电容并联**\
&emsp;&emsp;$n$个电容为$C _k$，初始电压为$u _{k0}(k=1,2,\cdots,n)$的电容器，按照相同电压方向**并联**，得到一个电容为$C _{eq}$，初始电压为$u _0$的等效电容：
$$C _\mathrm{eq}=\sum _{k=1}^nC _k\tag{7.15}$$

&emsp;&emsp;如果各个电容的初始电压相等，那么它们就等于$u _{k0}$.如果不是全部相等，在并联的一瞬间会产生冲击电流，使得电压统一为$u _0$：
$$u _0=\cfrac{\sum\limits _{k=1}^nC _ku _{k0}}{\sum\limits _{k=1}^nC _k}\tag{7.16}$$
<blockquote>
&emsp;&emsp;形式上，$u _0$是$u _{k0}$以$C _k$为权的加权平均值，也即各个电容的初始电压以电容为权的加权平均值。冲击电流带来的是电容极板上电荷量$q$的瞬间重新分配,冲击前后电容极板上电荷守恒$\sum q=\sum Cu=\mathrm{Const}$.
</blockquote>

**三、电感**\
&emsp;&emsp;储存磁场能量的元件，$\varPsi=Li$.其$u-i$关系：
$$\begin{aligned}&u=\cfrac{\mathrm d\varPsi}{\mathrm dt}=\cfrac{\mathrm d(Li)}{\mathrm dt}=L\cfrac{\mathrm di}{\mathrm dt}\\\\
&i(t)=i(0 _-)+\cfrac{1}{L}\int _{0 _-}^tu\mathrm dt\end{aligned}\tag{7.17}$$
<blockquote>
&emsp;&emsp;法拉第电磁感应定律指出，$\mathscr E _i=-\cfrac{\mathrm d\varPsi}{\mathrm dt}$.但是式$(7.17)$中没有负号。这是因为，感应电动势$\mathscr E _i$的方向是从低电势指向高电势；而电路理论中$u$的方向是压降的方向，从高电势指向低电势。
</blockquote>

**1.电感并联**\
&emsp;&emsp;$n$个电感为$L _k$，初始电流为$i _{k0}(k=1,2,\cdots,n)$的电感器，按照相同电流方向**并联**得到一个电感位$L _\mathrm{eq}$，初始电流为$i _0$的等效电感：
$$i _0=\sum _{k=1}^ni _{k0}\qquad \cfrac{1}{L _\mathrm{eq}}=\sum _{k=1}^n\cfrac{1}{L _k}\tag{7.18}$$

&emsp;&emsp;如果通过等效电感的电流变为$i'$，那么电流的变化量$\Delta i=i'-i _0$以电感的倒数为权重，分给这$n$个电感：
$$i _k'=i _{k0}+\Delta i _k=i _{k0}+(i'-i _0)\cfrac{L _k^{-1}}{\sum\limits _{l=1}^nL _l^{-1}}\tag{7.19}$$

**2.电感串联**\
&emsp;&emsp;$n$个电感位$C _k$，初始电压为$i _{k0}(k=1,2,\cdots,n)$的电感器，按照相同电流方向**串联**，得到一个电感为$L _{eq}$，初始电流为$i _0$的等效电感：
$$L _\mathrm{eq}=\sum _{k=1}^nL _k\tag{7.20}$$

&emsp;&emsp;如果各个电感的初始电流相等，那它们就等于$i _0$.如果不是全部相等，在串联的一瞬间会产生冲击电压，使得电流统一为$i _0$：
$$i _0=\cfrac{\sum\limits _{k=1}^nL _ki _{k0}}{\sum\limits _{k=1}^nL _k}\tag{7.21}$$
<blockquote>
&emsp;&emsp;形式上，$i _0$是$i _{k0}$以$L _k$为权的加权平均值，也即各个电感的初始电流以电感为权的加权平均值。冲击电压带来的是电感内磁链$\varPsi$的瞬间重新分配，冲击前后电感中磁链守恒$\sum \varPsi=\sum Li=\mathrm{Const}$.<br>
&emsp;&emsp;相比于电荷守恒，磁链守恒可能没有那么直观，理解起来稍微困难一些。
</blockquote>

**五、动态电路暂态分析**\
&emsp;&emsp;列写微分方程，根据初值条件得到唯一解。微分方程的阶数为电路中**独立储能元件**个数。
<blockquote>
&emsp;&emsp;两个储能元件不独立，一般具备以下条件：<br>
&emsp;&emsp;1.元件类型相同。比如说都是电容，或者都是电感。<br>
&emsp;&emsp;2.两个元件串联或者并联。<br>
&emsp;&emsp;其实也就是两个元件可以“合成”一个等效元件。如果电感$L _1$与一个电阻$R$先串联后，再与$L _2$并联，那也是两个独立储能元件。如果实在判断不了，就直接列微分方程；每个元件的微分方程阶数未必相等，但阶数最高的那个等于电路的阶数。<br>
&emsp;&emsp;两个元件不独立，也有可能是其它因素对它们造成了约束。
</blockquote>

&emsp;&emsp;初值条件是$t=0 _+$时各个量的值。一般情况是连续换路，对于电容有$u(0 _+)=u(0 _-)$，对于电感有$i (0 _+)=i (0 _-)$，根据电路定理求出电路在$t=0 _+$时的各电压、电流值。如果求微分值，一般需要进行转换：\
&emsp;&emsp;1.电容$C$的$\cfrac{\mathrm du _C}{\mathrm dt}$，根据$i=C\cfrac{\mathrm du}{\mathrm dt}$转化为求$i _C$.\
&emsp;&emsp;2.电感$L$的$\cfrac{\mathrm di _L}{\mathrm dt}$，根据$u=L\cfrac{\mathrm di}{\mathrm dt}$转化为求$u _L$.\
&emsp;&emsp;3.电容$C$的$\cfrac{\mathrm di _C}{\mathrm dt}$，用电容本身的电压$u _C$或某个电感的$i _L$表示$i _C$，转化为情况1或2求解。\
&emsp;&emsp;4.电感$L$的$\cfrac{\mathrm du _L}{\mathrm dt}$，用电感本身的$i _L$或某个电容的$u _C$表示$u _L$，转化为情况1或2求解。\
&emsp;&emsp;5.二阶及以上微分，一层层来。

## $Chapter8$&emsp;一阶电路暂态分析
**一、分析方法**\
&emsp;&emsp;暂态电路中如果只有一个独立储能元件（一阶电路），其分析会方便很多，也能够总结出一些技巧。\
&emsp;&emsp;零输入响应（自然响应）、零状态响应（阶跃响应）都可以看作是**全响应**的特殊情况，因而可以都使用三要素法。电路中的任何响应（电压或电流）$y$都按照式$(8.1)$变化。
$$y(t)=y(\infty)+[y(0 _+)-y(\infty)]\mathrm e^{-\frac{t}{\tau}}\tag{8.1}$$

&emsp;&emsp;简单来说，也就是响应$y$从初始值$y(0 _+)$按指数规律渐近到$y(\infty)$.其中的$\tau$是电路的**时间常数**。先将储能元件外的电路等效为**戴维南支路**，其等效电阻为$R _\mathrm{eq}$.对于储能元件是电容的电路，$\tau=R _\mathrm{eq}C$；对于储能元件是电感的电路，$\tau=\cfrac{L}{R _\mathrm{eq}}$.

<blockquote>
&emsp;&emsp;初值$y(0 _+)$求法在$Chapter7$，稳态$y(\infty)$在稳态电路图中求。对于所有的一阶电路来说，暂态持续$5\tau$后，认为达到了稳态。
</blockquote>

&emsp;&emsp;全响应还可以看作是<st>零输入响应与零状态响应的叠加</st>。考虑全响应中任意一个响应$y$.如果将电路中所有的独立电源置零，此时对应的响应为$y'$；将电路中储能元件的储能清空，此时对应的响应为$y''$.那么$y=y'+y''$.

**二、一些分量**\
&emsp;&emsp;式$(8.1)$中，$[y(0 _+)-y(\infty)]\mathrm e^{-\frac{t}{\tau}}$是**暂态分量**，因为指数使其随时间衰减为$0$，只能暂时存在。它也是**自由分量**，在电源强制稳住电容（或电感）之前，允许电容（或电感）自由发挥一会。\
&emsp;&emsp;$y(\infty)$是**稳态分量**，因为响应最终会稳定在这个值。它也是**强制分量**，是电源强制响应收敛到这个值的。

**三、线性非时变特性**\
&emsp;&emsp;一般见到的由独立电源、电阻、储能元件构成的电路，都是线性非时变电路。它们的**零状态**响应有两个性质。\
&emsp;&emsp;**线性特性**：若$x _1(t)$激励下的零状态响应为$y _1(t)$，$x _2(t)$激励下的零状态响应为$y _2(t)$，则$k _1x _1(t)+k _2x _2(t)$激励下的零状态响应为$k _1y _1(t)+k _2y _2(t)$.
<blockquote>
&emsp;&emsp;<strong>线性特性</strong>中的响应$y(t)$与$(8.1)$式中的有些许不同，一般只考虑电容、电感的响应。同时，<strong>线性特性</strong>适用于时变独立电源。后面的非时变特性也是这样的。
</blockquote>

&emsp;&emsp;**非时变特性**：若$x(t)$激励下的零状态响应为$y(t)$，则$x(t-t _0)$激励下的零状态响应为$y(t-t _0)$.\
&emsp;&emsp;除此之外，还有一个**重要特性**：若$x(t)$激励下的零状态响应是$y(t)$，则$\cfrac{\mathrm dx(t)}{\mathrm dt}$激励下的零状态响应是$\cfrac{\mathrm dy(t)}{\mathrm dt}$，$\displaystyle\int _{0 _-}^tx(t)\mathrm dt$激励下的零状态响应是$\displaystyle\int _{0 _-}^ty(t)\mathrm dt$.
<blockquote>
&emsp;&emsp;这个性质实用的一点在，我们可以根据阶跃电源（如$u _S\varepsilon(t)$）下的零状态响应，求冲击电源（对应的，$u _S\delta(t)$）下的零状态响应。这个性质是正确的，但课本上说这是“线性非时变电路零状态响应的<strong>线性特性、非时变特性结合</strong>”得出的性质，我目前无法理解。
</blockquote>

## $Chapter10$&emsp;正弦稳态分析
**一、正弦电量**\
&emsp;&emsp;对于周期性电量$y(t)$（电压或电流），定义有效值为一个周期内瞬时值平方的平均值，即**方均根**值：
$$y=\sqrt{\cfrac{1}{T}\int _0 ^Ty^2(t)\mathrm dt}\tag{10.1}$$
<blockquote>
&emsp;&emsp;课本上说这是均方根，但个人认为方均根更合适一点。
</blockquote>

&emsp;&emsp;如果$y(t)$是**正弦电量**，那么$y=\cfrac{y _m}{\sqrt 2}$.\
**二、相量法**\
&emsp;&emsp;正弦电量，例如$u=\sqrt 2U\cos(\omega t+\varphi)$，引入虚部后构成一个复数：
$$\begin{aligned}\sqrt 2U[\cos(\omega t+\varphi)+\color{red}{\mathrm j\sin(\omega t+\varphi)}]&=\sqrt 2U\mathrm e^{\mathrm j(\omega t+\varphi)}\\\\&=\sqrt 2\color{red}{U}\mathrm e^{\mathrm j\omega t}\cdot\color{red}{\mathrm e^{\mathrm j\varphi}}\\\\
&=\sqrt 2\mathrm e^{\mathrm j\omega t}\color{red}{\dot U}\end{aligned}\tag{10.2}$$

&emsp;&emsp;$\dot U$含有正弦电量$u$的**初相位**信息，不含时域$t$的信息，被称为**相量**。
<blockquote>
&emsp;&emsp;电路理论里面用$\mathrm j$表示<strong>虚数单位</strong>，可能是考虑到$i$在电路中表示电流，避免混淆。相量的引入，有些类似大学物理研究简谐振动时<strong>旋转矢量法</strong>的引入。旋转矢量在$y$轴上的投影和振动本身关系不大，只是利用了其在$x$轴上的投影。振动的叠加采用旋转矢量法，所以相量法也非常方便正弦电量的加减。<br>
&emsp;&emsp;相量的引入还优化了正弦电量的微分、积分运算。“相量的微分运算很简单”的说法实际上是错误的，因为我们根本没有对相量微分，相量的表达式中根本不含$t$.我们是将时域量$u(i)$的微分、积分运算，<strong>对应</strong>到相量$\dot U(\dot I)$的乘法、除法运算：
$$\begin{aligned}\cfrac{\mathrm du}{\mathrm dt}&\longleftrightarrow \mathrm j\omega\dot U\\
\int u\mathrm dt&\longleftrightarrow \cfrac{\dot U}{\mathrm j\omega}\end{aligned}\tag{10.3}$$
&emsp;&emsp;相量到底是什么？我认为它是一个抽取了电量初态（即$t=0$时）信息的量，由于正弦电路电量的变化是周期性的、有规律的，这个初态就足以表征电量的所有特征。
</blockquote>

**三、阻抗和导纳**\
&emsp;&emsp;对于电感$L$，由相量的微分关系可得$\cfrac{\dot U _L}{\dot I _L}=\mathrm j\omega L$，其中的$\mathrm j$代表电压超前电流$\cfrac{\pi}{2}$.对比电阻$R=\cfrac{U}{I}$，我们记$X _L=\omega L$为**电抗**，它和电阻一样表征阻止、抵抗电流的性质。电阻的倒数是电导，所以定义电抗的倒数**电纳**$B _L=\cfrac{1}{\omega L}$.电容也可以相应地得到$X _C=\cfrac{1}{\omega C}$，$L _C=\omega C$.\
&emsp;&emsp;电阻和电抗一样都能阻止、抵抗电流的性质，并且都具有$U/I$的形式，可以统一成**阻抗**：
$$Z=\cfrac{\dot U}{\dot I}=R+\mathrm jX=|Z|\angle\varphi _Z\tag{10.4}$$

&emsp;&emsp;同理定义导纳：
$$Y=\cfrac{\dot I}{\dot U}=G+\mathrm jB=|Y|\angle\varphi _Y\tag{10.5}$$

&emsp;&emsp;在引入阻抗和导纳后，直流电路的内容也可以搬到这里来使用。电压超前电流为感性，电流超前电压为容性。

## $Chapter11$&emsp;正弦稳态电路的功率
**一、瞬时功率**\
&emsp;&emsp;只有电阻在消耗功率。电阻和电感不会消耗功率，于是功率在储能元件和电源中反复交换。正因如此，电路消耗的瞬时功率$p(t)$会出现负值，这说明储能元件正在释放能量。\
&emsp;&emsp;瞬时功率的表达式为
$$p(t)=UI\cos(\varphi _u-\varphi _i)+UI\cos(2\omega t+\varphi _u+\varphi _i)\tag{11.1}$$

**二、有功功率与无功功率**\
**1.有功功率**\
&emsp;&emsp;有功功率$P$定义为<st>瞬时功率的平均值</st>，也就是瞬时功率在一个周期内的平均值。根据式$(11.1)$得到有功功率：
$$P=UI\cos(\varphi _u-\varphi _i)\tag{11.2}$$

&emsp;&emsp;有功功率（单位瓦，$\mathrm W$），可以理解为电能中真正在做电功的那部分的消耗功率。$P$同时也是网络中电阻消耗的<st>平均功率</st>，也就是电阻瞬时功率的平均值。\
**2.无功功率**\
&emsp;&emsp;无功功率定义为<st>网络与电源往复交换功率的幅值</st>。通过将网络等效为电阻$R$串联电抗$X$的模型，分析电抗$X$的瞬时功率，其最大值就是无功功率：
$$Q=UI\sin(\varphi _u-\varphi _i)\tag{11.3}$$

&emsp;&emsp;无功功率（单位乏，$\mathrm {var}$），本身不包含吸收或发出的功率，但还是人为**约定**电感吸收无功功率，电容发出无功功率。\
&emsp;&emsp;如果已知经过等效电抗$X$的电流有效值为$I$，也可以根据$Q=I^2X$求它吸收的无功功率；已知它两端电压的有效值为$U$，也可以根据$Q=\cfrac{U^2}{X}$求无功功率。这和纯电阻电路的欧姆定律相似。
<blockquote>
&emsp;&emsp;乏（$\mathrm{var}$）和瓦（$\mathrm W$）量纲相同，以及视在功率单位$\mathrm{V\cdot A}$都具有相同的量纲。人为区分它们的单位，是为了仅在给出电路参数的情况下，就能根据单位判断它是哪一种功率。
</blockquote>

**三、视在功率和功率因数**\
**1.视在功率与复功率**\
&emsp;&emsp;视在功率（单位伏安，$\mathrm{V\cdot A}$），定义为<st>负载消耗或电源提供的有功功率的上限</st>，由于$P=UI\cos(\varphi _u-\varphi _i)$，所以，$S=UI$.\
&emsp;&emsp;**复功率**把这些功率综合在一起。
$$\overline S=P+\mathrm jQ\tag{11.4}$$
<blockquote>
&emsp;&emsp;复功率$\overline S$的单位也是$\mathrm{V\cdot A}$，并且$|\overline S|=S$，即视在功率是复功率的模，也难怪都用字母$S$表示。
</blockquote>

&emsp;&emsp;求复功率经常用到<st>$\overline S=\dot U\dot I ^ * $</st>，当然也可以根据已知条件对其进行变形，比如$\overline S=\cfrac{U^2}{\dot Z^ *}$或$\overline S=I^2Z$等。\
**2.功率因数**\
&emsp;&emsp;功率因数定义为<st>有功功率与视在功率的比值</st>：
$$\lambda=\cfrac{P}{S}=\cos(\varphi _u-\varphi _i)=\cos\varphi\tag{11.5}$$

&emsp;&emsp;其中$\varphi=\varphi _u-\varphi _i$被称为**功率因数角**。电力系统由电压源供电，负载并联工作，负载电压基本恒定，因此习惯**以电压为参考相量**，电流滞后于电压（$\cfrac{\pi}{2}\geq\varphi > 0$）时称$\lambda$为<strong>滞后（或感性）</strong>功率因数，电流超前电压（$-\cfrac{\pi}{2}\leq\varphi < 0$）时称$\lambda$为<strong>超前（容性）</strong>功率因数。

&emsp;&emsp;瓦特表测量电路的有功功率。
## $Chapter12$&emsp;三相正弦稳态电路
**一、三相电路基本**\
**1.三相电源**\
&emsp;&emsp;一般有两种连接方法。如果是星形连接，一般引出$\mathrm{A,B,C,N}$三个端；如果是三角形连接，一般引出$\mathrm{A,B,C}$三个端。
<table align="center">
    <caption align="top">表 三相电源不同连接方式的电压关系</caption>
    <tr>
        <th>三相电源连接方式</th>
        <td>三角形连接</td>
        <td>星形连接</td>
    </tr>
    <tr>
        <th>$u _\mathrm A$</th>
        <td>$u _\mathrm {AN}$</td>
        <td>$u _\mathrm{AB}$</td>
    </tr>
    <tr>
        <th>$u _\mathrm B$</th>
        <td>$u _\mathrm{BN}$</td>
        <td>$u _\mathrm{BC}$</td>
    </tr>
    <tr>
        <th>$u _\mathrm C$</th>
        <td>$u _\mathrm{CN}$</td>
        <td>$u _\mathrm{CA}$</td>
    </tr>
</table>

&emsp;&emsp;$\varphi _A-\varphi _B=\varphi _B-\varphi _C=\varphi _C-\varphi _A=120^\circ$称为**正序**，$-120^\circ$称为**负序**，电力系统中要求是正序的三相电源。\
**2.三相负载**\
&emsp;&emsp;同样有三角形负载和星形负载。**对称**三相负载的转换关系为：
$$Z _\Delta=3Z _\mathrm Y\tag{12.1}$$

**二、对称三相电路计算**\
**1.三相电量**\
&emsp;&emsp;**正序对称**电路中线电量与相电量的关系为：\
&emsp;&emsp;$\mathrm Y$型连接，线电压$\dot U _l$与对应相电压$\dot U _p$的关系是$\dot U _l=\sqrt 3\dot U _p\angle 30^\circ$，线电流与相电流是同一个电流。\
&emsp;&emsp;$\Delta$型连接，线电压与相电压是同一个电压，线电流$\dot I _l$与对应相电流$\dot I _p$的关系是$\dot I _l=\sqrt 3\dot I _p\angle -30^\circ$.
<blockquote>
&emsp;&emsp;线电压可以与相电流对应，因为对称三相电路中的电量有很好的轮换对称性质。约定<strong>正序</strong>对称电路的线量与相量对应关系：$\dot U _\mathrm {ab}\leftrightarrow \dot U _\mathrm {an},\dot U _\mathrm {bc}\leftrightarrow \dot U _\mathrm {bn},\dot U _\mathrm{ca}\leftrightarrow \dot U _\mathrm{cn}$.<br>
&emsp;&emsp;将$\dot U$换成$\dot I$，或是将$\mathrm{a,b,c}$换成$\mathrm{A,B,C}$（负载侧换成电源侧），对应关系也成立。<br>
&emsp;&emsp;对于电源侧，因为一般情况都是$\mathrm Y$型三相电源，所以电源侧的线电流和相电流就是同一个电流，一般只考虑电源侧的电压关系。对于负载侧，由于常见的接法两种都有，所以要按照负载侧的接法讨论线量和相量。
</blockquote>

&emsp;&emsp;对称三相电路中，点$\mathrm N$与点$\mathrm n$的电势总是相等的。因此可以将$\mathrm{N,n}$短接，这是利用分相法计算对称三相电路的理论基础；也可以将$\mathrm{N-n}$断路，从而降低输电成本。\
**2.三相功率**\
&emsp;&emsp;设负载侧的相电压有效值$U _p$，相电流有效值$I _p$，那么<st>三相电路负载的瞬时功率是恒定值</st>。考虑到星形、三角形负载均有$U _lI _l=\sqrt 3U _pI _p$，所以：
$$p=3U _pI _p\cos\varphi=\sqrt 3U _lI _l\cos\varphi\tag{12.2}$$

&emsp;&emsp;其中的$\varphi$是负载阻抗$Z$的阻抗角。由有功功率的定义，式$(12.2)$所表示的也是三相电路负载的有功功率：
$$P=3U _pI _p\cos\varphi=\sqrt 3U _lI _l\cos\varphi\tag{12.3}$$

&emsp;&emsp;实际上也能得到三相电路负载的无功功率：
$$Q=3U _pI _p\sin\varphi=\sqrt 3U _lI _l\sin\varphi\tag{12.4}$$
<blockquote>
&emsp;&emsp;把三相分开来，分别算每一相的无功功率，每一相都是$U _pI _p\sin\varphi$.
</blockquote>

&emsp;&emsp;同理得到三相负载电路的复功率和视在功率：
$$\overline S=P+\mathrm jQ=3U _pI _p(\cos\varphi +\mathrm j\sin\varphi)=\sqrt 3U _lI _l(\cos\varphi +\mathrm j\sin\varphi)\tag{12.5}$$

$$S=|\overline S|=\sqrt{P^2+Q^2}=3U _pI _p=\sqrt 3U _lI _l\tag{12.6}$$

<blockquote>
&emsp;&emsp;由于我们是直接对负载的电压、电流分析得到一系列的功率，所以三相电路的复功率仍然可以用相电量表示为：
$$\overline S=3\dot U _p\dot I _p^ * \tag{12.7}$$
&emsp;&emsp;但是
$$\overline S\neq \sqrt 3\dot U _l\dot I _l^ * \tag{12.8}$$
&emsp;&emsp;这是因为相量与对应的线量相比，除了模上有差距，相位也是有差距的。对于三角形负载，$\dot U _l=\dot U _p$，$\dot I _l=\sqrt 3\dot I _p\angle -30^\circ$，所以：
$$\overline S _\Delta=3\dot U _p\dot I _p^ * =3\dot U _l(\cfrac{\dot I _l}{\sqrt 3}\angle 30^\circ)^ * =\sqrt 3\dot U _l\dot I _l^ * \color{red}{\angle -30^\circ}\tag{12.9}$$
&emsp;&emsp;对于星形负载，$\dot U _l=\sqrt 3\dot U _p\angle 30^\circ$，$\dot I _l=\dot I _p$，所以
$$\overline S _\mathrm Y=3\dot U _p\dot I _p^ * =3\cfrac{U _l}{\sqrt 3\angle 30^\circ}\dot I _l^ * =\sqrt 3\dot U _l\dot I _l^ * \color{red}{\angle -30^\circ}\tag{12.10}$$
&emsp;&emsp;所以三相电路的复功率用线量应表示为：
$$\overline S=\sqrt 3\dot U _l\dot I _l^ * \color{red}{\angle -30^\circ}\tag{12.11}$$
</blockquote>

**四、三相电路有功功率的测量**<br>
&emsp;&emsp;可以用三个瓦特表分别测三相有功功率，适合对称和不对称的三相电路（所有电路）。\
&emsp;&emsp;如果只用两个瓦特表，仅不适用于中线电流$I _\mathrm n$非零的四线制电路。两个瓦特表的示数没有物理意义，可能出现负值，但是和$P _1+P _2$为三相电路的总有功功率。在对称三相电路中，$P _1,P _2$还与电路的无功功率$Q$有联系。如果正序三相电路中$\mathrm W _1$所在相的相位领先$\mathrm W _2$所在相$120^\circ$的话，就有：
$$Q=\sqrt 3(P _1-P _2)\tag{12.12}$$

## $Chapter13$&emsp;含磁耦合的电路
**一、耦合电感**\
&emsp;&emsp;为了在电路图中表示电感的耦合关系，引入了**同名端**：当电流同时流入（或流出）同名端时，耦合电感为**加强型耦合**。
<blockquote>
&emsp;&emsp;一般在计算的时候，电感的电压、电流都是取关联方向的。可以认为从一个同名端流入的电流，与另一端的电压是关联方向。即电感$L _2$的同名端流入$i _2$，在另一端产生$u _1=M\cfrac{\mathrm di _2}{\mathrm dt}$，而非$u _1=-M\cfrac{\mathrm di _2}{\mathrm dt}$.
</blockquote>

&emsp;&emsp;耦合电感中，由于耦合的存在，所以会额外储存一个**互感储能**。选定电感$L _1,L _2$的电流$i _1,i _2$的方向后，互感储能就是$\pm Mi _1i _2$.正号对应加强型耦合，负号对应削弱型耦合。\
**二、含耦合电感电路的分析**\
&emsp;&emsp;分析方法总的来说有三种。\
**1.普通方法**\
&emsp;&emsp;用网孔分析法，使用网孔电流$\dot I _\mathrm m$表示各个电感上的压降，然后对每个网孔列写网孔方程。其实也就是列写KVL方程。可以分析所有的耦合电感电路，但是略显麻烦。\
**2.去耦合等效电路**\
&emsp;&emsp;适合于耦合电感<st>有公共端</st>的情况。有些时候没有公共端，可以通过电路等效变换去创造公共端。实在创造不了，就不能用这种方法。\
&emsp;&emsp;如果公共端是同名端，可以从两个电感$L _1,L _2$中提出互感$M$.如果是非同名端，可以提出$-M$.\
**3.映射阻抗**\
&emsp;&emsp;负载回路（电感$L _2$和负载$Z _2$）映射到电源回路，映射阻抗：
$$Z _\mathrm r=\cfrac{(\omega M)^2}{Z _2+\mathrm j\omega L _2}\tag{13.1}$$

&emsp;&emsp;显然映射阻抗的大小与$L _1,L _2$之间的耦合类型无关。\
**三、变压器**\
&emsp;&emsp;理想变压器模型的假设条件：线圈**没有电阻**，磁心没有损耗，自感<st>$L _1\rightarrow \infty,L _2\rightarrow \infty$</st>，电感**全耦合**。它是从铁芯变压器抽象出来的理想模型。
<blockquote>
&emsp;&emsp;因为理想变压器的两个电感$L _1,L _2\rightarrow\infty$，所以不能像之前遇到的耦合电感那样，用$u=L\cfrac{\mathrm di}{\mathrm dt}$分析电感两端的电压。实际分析采用的是完全不同的思路。
</blockquote>

**1.线圈电压与电流关系**\
&emsp;&emsp;取$i _1,i _2$均流入（流出）同名端，且$u _1,u _2$分别于$i _1,i _2$是关联方向，那么：
$$\begin{aligned}\cfrac{u _1}{u _2}&=\cfrac{N _1}{N _2}=n\\\\
\cfrac{i _1}{i _2}&=-\cfrac{N _2}{N _1}=-\cfrac{1}{n}\end{aligned}\tag{13.2}$$

<blockquote>
&emsp;&emsp;理想变压器仅完成功率传输的作用，不消耗有功功率，也不消耗无功功率。
</blockquote>

**2.阻抗变换**\
&emsp;&emsp;理想变压器的阻抗变换公式是：
$$Z _\mathrm{in}=n^2Z _\mathrm L\tag{13.3}$$

<blockquote>
&emsp;&emsp;理想变压器的阻抗变换不同于阻抗映射。阻抗映射后仍保留电源回路的电感$L _1$，阻抗变换不保留，也不能保留（因为$L _1\rightarrow\infty$）。实际上它们也就是名字比较像，但完全不是一个东西，所以阻抗变换也不能套用式$(13.1)$.式$(13.3)$的变换，通过可以变形成下式：
$$\cfrac{Z _\mathrm{in}}{N _1^2}=\cfrac{Z _\mathrm L}{N _2^2}\tag{13.4}$$
&emsp;&emsp;$Z _\mathrm{in}$和$N _1$是原方回路的变换阻抗和原方线圈的匝数，$Z _\mathrm L$和$N _2$是次方回路的阻抗和次方线圈的匝数。<br>
&emsp;&emsp;由式$(13.3)$可以看出，原方回路的阻抗也可以映射到次方回路。
</blockquote>

## $Chapter14$&emsp;正弦稳态电路的频率响应
**一、传递函数与频率响应**\
&emsp;&emsp;随着输入信号频率$\omega$的变化，电路的工作状态也会变化。传递函数定义为正弦稳态电路中某个响应相量和激励相量之比：
$$H(\omega)=\cfrac{\dot Y(\omega)}{\dot X(\omega)}\tag{14.1}$$

&emsp;&emsp;根据$|H(\omega)|$在高频、低频区的大小，可以将电路分为：\
&emsp;&emsp;**高通**滤波器：对低频信号有抑制作用，即$\omega$小时$|H(\omega)|$小。\
&emsp;&emsp;**低通**滤波器：对高频信号有抑制作用，即$\omega$大时$|H(\omega)|$小。\
&emsp;&emsp;**带通**滤波器：在某一个角频率区间内$|H(\omega)|$比较大。\
**二、谐振电路**\
**1.RLC串联电路**\
&emsp;&emsp;RLC串联电路的谐振（角）频率$\omega _0=\cfrac{1}{\sqrt{LC}}$，品质因数是：
$$Q=\cfrac{\omega _0L}{R}=\cfrac{1}{\omega _0CR}=\cfrac{1}{R}\sqrt{\cfrac{L}{C}}\tag{14.2}$$

&emsp;&emsp;以$\dot U _R$为响应，能够构造一个带通滤波器，其通带宽度为：
$$B=\omega _{c2}-\omega _{c _1}=\cfrac{\omega _0}{Q}\tag{14.3}$$

<blockquote>
&emsp;&emsp;课本用$Q=\cfrac{U _{L0}}{U _S}=\cfrac{U _{C0}}{U _S}$引入品质因数$Q$.但我认为式$(14.3)$才是品质因数的最好体现，品质因数越大，带宽越小，滤波能力越强。
</blockquote> 

**2.RLC并联谐振电路**\
&emsp;&emsp;RLC并联电路的谐振（角）频率和串联一样，品质因数：
$$Q=\cfrac{\omega _0C}{G}=\cfrac{1}{\omega _0LG}\tag{14.4}$$

&emsp;&emsp;通带宽度同式$(14.3)$.\
**3.其他谐振电路**\
&emsp;&emsp;谐振，其实就是电流和电压一起振动，它们的相位相同。据此可以分析各种混联电路的谐振情况，也就是混联后阻抗$Z$（或者等价地，导纳$G$）<st>只有实部</st>。电流和电压有着相同的相位，这说明电路的功率因数角$\varphi=0$，<st>无功功率为$0$</st>，电感吸收的无功功率与电容发出的无功功率恰好抵消。根据这些都可以找到谐振频率。\
&emsp;&emsp;由式$(14.2)$和$(14.4)$看出，品质因数$Q$在不同电路里的定义是不同的，我摸索出了一个统一的定义：$Q$是谐振电路中所有电感吸收的无功功率（或所有电容发出的无功功率）$Q _L$与电路消耗的有功功率$P _R$之比。即：
$$Q=\cfrac{Q _L}{P _R}\tag{14.5}$$
<blockquote>
&emsp;&emsp;式$(14.5)$是本人做了一些题后想到的经验公式，它能够解释RLC串联、并联电路的品质因数。以RLC串联电路为例：
$$Q=\cfrac{\omega _0L}{R}=\cfrac{I^2X _L(\omega _0)}{I^2 R}=\cfrac{IU _L}{P _R}=\cfrac{Q _L}{P _R}\tag{14.6}$$
</blockquote>

## $Chapter15$&emsp;周期性非正弦稳态电路
&emsp;&emsp;使用傅里叶变换，转换成直流加不同频率的正弦波。\
**1.电量的有效值**\
&emsp;&emsp;如果有一个电压以傅里叶级数形式展开：
$$u=U _0+\sum _{k=1}^{\infty}\sqrt 2U _k\cos(k\omega _0t+\varphi _k)\tag{15.1}$$

&emsp;&emsp;那么这个电压的有效值是：
$$U =\sqrt{U _0^2+\sum _{k=1}^\infty U _k^2}\tag{15.2}$$

&emsp;&emsp;也就是**直流分量与各谐波分量有效值平方和的平均根**，或者**各分量有效值的平方和的平均根**。\
**2.平均功率（有功功率）**\
&emsp;&emsp;平均功率符合叠加定理，可以考虑各个分量分别作用。如果电压与电流为关联方向：
$$\begin{aligned}u(t)&=U _0+\sum _{k=1}^\infty\sqrt 2U _k\cos(k\omega t+\varphi _{uk})\\\\
i(t)&=I _0+\sum _{k=1}^\infty\sqrt 2I _k\cos(k\omega t+\varphi _{ik})\end{aligned}\tag{15.3}$$

&emsp;&emsp;那么平均功率为：
$$P=U _0I _0+\sum _{k=1}^\infty U _kI _k\cos(\varphi _{uk}-\varphi _{ik})\tag{15.6}$$

$\boxed{\mathbb{The\ End}}$