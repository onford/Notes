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

# 大学物理（下）笔记
## 部分常用物理常量的计算值

<table align="center">
    <tr>
        <th>物理量</th>
        <th>计算用值</th>
        <th>物理量</th>
        <th>计算用值</th>
    </tr>
     <tr>
        <td>真空中的光速</td>
        <td>$c=3.0\times 10^8\mathrm{\ m\cdot s^{-1}}$</td>
        <td>引力常量</td>
        <td>$G=6.67\times10^{-11}\mathrm{\ m^3\cdot kg^{-1}\cdot s^{-2}}$</td>
    </tr>
    <tr>
        <td>重力加速度</td>
        <td>$g=9.8\mathrm{\ m\cdot s^{-2}}$</td>
        <td>元电荷</td>
        <td>$e=1.6\times10^{-19}\mathrm{\ C}$</td>
    </tr>
    <tr>
        <td>电子静质量</td>
        <td>$m_\mathrm{e}=9.91\times 10^{-31}\mathrm{\ kg}$</td>
        <td>电子荷质比</td>
        <td>$-e/m_\mathrm{e}=-1.76\times10^{11}\mathrm{\ C\cdot kg^{-1}}$</td>
    </tr>
    <tr>
        <td>电子经典半径</td>
        <td>$r_\mathrm{e}=2.82\times 10^{-15}\mathrm{\ m}$</td>
        <td>质子静质量</td>
        <td>$m_\mathrm{p}=1.673\times10^{-27}\mathrm{\ kg}$</td>
    </tr>
    <tr>
        <td>中子静质量</td>
        <td>$m_\mathrm{n}=1.675\times 10^{-27}\mathrm{\ kg}$</td>
        <td>真空介电常数</td>
        <td>$\varepsilon_0=8.85\times10^{-12}\mathrm{\ F\cdot m^{-1}}$</td>
    </tr>
    <tr>
        <td>真空磁导率</td>
        <td>$\mu_0=4\pi\times 10^{-7}\mathrm{\ N\cdot A^{-2}}$</td>
        <td>阿伏伽德罗常数</td>
        <td>$N_\mathrm{A}=6.02\times10^{23}\mathrm{\ mol^{-1}}$</td>
    </tr>
    <tr>
        <td>摩尔气体常量</td>
        <td>$R=8.31\mathrm{\ J\cdot mol^{-1}\cdot K^{-1}}$</td>
        <td>玻尔兹曼常量</td>
        <td>$k=1.38\times10^{-23}\mathrm{\ J\cdot K^{-1}}$</td>
    </tr>
    <tr>
        <td>理想气体摩尔体积（标准状况）</td>
        <td>$V_\mathrm{m}=22.4\times 10^{-3}\mathrm{\ m^3\cdot mol^{-1}}$</td>
        <td>标准大气压</td>
        <td>$1\mathrm{\ atm}=1.01\times10^5\mathrm{\ Pa}$</td>
    </tr>
    <tr>
        <td>普朗克常量</td>
        <td>$h=6.63\times 10^{-34}\mathrm{\ J\cdot s}$</td>
        <td>康普顿波长</td>
        <td>$\lambda _ c=2.43\times10^{-12}\mathrm{\ m}$</td>
    </tr>
</table>

<bw>wr按：\
这一部笔记，主要记录学习过程中的一些想法，以便后续查看时能回忆起当时的理解，并加深印象。实际上并不全面，只是自己想到的一些东西。其中的光学篇，由于在高中时期没有接触过，因此难免在理解上出现一些问题。</bw>

## $Chapter9$&emsp;恒定磁场
**一、毕奥-萨伐尔定律**\
&emsp;&emsp;磁场和电场在很多性质上是有共性的，很多时候可以拿它们两个相互对比。\
&emsp;&emsp;恒定磁场最基础的公式是毕奥-萨伐尔定律：
$$\textrm{d}\boldsymbol B=\cfrac{\mu_0}{4\pi}\cfrac{I\textrm{d}\boldsymbol l\times\boldsymbol e_r}{r^2}\tag{9.1}$$

&emsp;&emsp;<st>$\mu_0=4\pi\times10^{-7}\mathrm{T\cdot m/A}$</st>，这个常数可以记忆一下。基于此，我们能够计算到电流为$I$的长直载流导线在距离其为$r$处激发的磁场为
$$B=\cfrac{\mu_0I}{4\pi r}(\cos \varphi_1-\cos\varphi_2)\tag{9.2}$$

&emsp;&emsp;其中$\varphi_1,\varphi_2$是该点与导线两端的连线和导线所成的夹角。无限长直载流导线激发的磁场，其实就是$(9.1)$式在$\varphi_1=0,\varphi_2=\pi$时的情况：
$$B=\cfrac{\mu_0I}{2\pi r}\tag{9.3}$$

&emsp;&emsp;通过毕奥-萨伐尔定律，还能够算得半径为$R$的圆环电流$I$在其轴线上坐标为$x$的点处产生的磁场大小
$$B=\cfrac{\mu_0I}{2(R^2+x^2)^{3/2}}\tag{9.4}$$

&emsp;&emsp;这个能够自行推导，感觉就足够了，倒也不是特别好记。\
**二、磁偶极子**\
&emsp;&emsp;磁偶极子可以认为是一个平面环形电流，只有当这个环的线度在问题中可以忽略时，才能把它作为磁偶极子处理。\
&emsp;&emsp;这很容易让我们联想到电偶极子。两者之间的对比如下：
<table align="center">
    <caption align="top">表 电偶极子与磁偶极子对比</caption>
    <tr>
        <th></th>
        <th>电偶极子</th>
        <th>磁偶极子</th>
    </tr>
    <tr>
        <th>定义式</th>
        <td>$$\boldsymbol{p}=q\boldsymbol{l}=ql\boldsymbol{e}_\mathrm{r}$$</td>
        <td>$$\boldsymbol{m}=I\boldsymbol{S}=IS\boldsymbol{e}_\mathrm{n}$$</td>
    </tr>
    <tr>
        <th>激发的电磁场</th>
        <td>中垂面上的电场<br>$$\boldsymbol{E}=-\cfrac{\boldsymbol{p}}{4\pi\varepsilon_0r^3}$$</td>
        <td>中垂线上的磁场<br>$$\boldsymbol{B}=\cfrac{\mu_0\boldsymbol{m}}{2\pi r^3}$$</td>
    </tr>
    <tr>
        <th>在电磁场中受到力矩</th>
        <td>在电场$\boldsymbol{E}$中<br>$$\boldsymbol{M}=\boldsymbol{p}\times\boldsymbol{E}$$</td>
        <td>在磁场$\boldsymbol{B}$中<br>$$\boldsymbol{M}=\boldsymbol{m}\times\boldsymbol{B}$$</td>
    </tr>
</table>

&emsp;&emsp;电偶极子在电场中受到力矩作用，达到稳定平衡状态时电矩与电场方向相同，能够解释有极分子的取向极化；磁偶极子在磁场中受到力矩作用，达到稳定平衡状态时磁矩与磁场方向相同，能够解释顺磁质的磁化。

**三、磁场的高斯定理与安培环路定理**\
&emsp;&emsp;磁场的高斯定理
$$\oint_S \boldsymbol{B\ \cdot}\mathrm{d}\boldsymbol{S}=0\tag{9.5}$$

&emsp;&emsp;说明磁场是<st>无源场</st>，这在本质上是因为不存在所谓“磁单极子”或者叫做“磁荷”的东西。而静电场是由“电荷”所激发的，所以静电场是有源场：
$$\oint_S \boldsymbol{E\ \cdot}\mathrm{d}\boldsymbol{S}=\cfrac{q}{\varepsilon_0}\tag{9.6}$$

&emsp;&emsp;在恒定磁场中，安培环路定理也经常被应用：
$$\oint_L\boldsymbol{B\ \cdot}\mathrm{d}\boldsymbol{l}=\mu_0I\tag{9.7}$$

**四、洛伦兹力与安培力**\
&emsp;&emsp;主要想谈谈其矢量式中各个量摆放顺序的问题。\
&emsp;&emsp;洛伦兹力
$$\boldsymbol{F}=q\boldsymbol{v\ \times B}\tag{9.8}$$

&emsp;&emsp;安培力
$$\boldsymbol{F}=I\boldsymbol{L\ \times B}\tag{9.9}$$

&emsp;&emsp;观察$(9.8)$式和$(9.9)$式，发现它们都能写成“电量·**运动量×场量**”的形式。其中**粗体**为矢量。

**五、磁化强度$\boldsymbol{M}$与磁场强度$\boldsymbol{H}$**\
&emsp;&emsp;我们通常习惯于用磁感应强度$\boldsymbol{B}$来描述磁场，用电场强度$\boldsymbol{E}$来描述电场。当电磁场中存在介质的时候，这种描述方法是不好的。\
&emsp;&emsp;磁化强度$\boldsymbol{M}$与磁场强度$\boldsymbol{H}$是为了研究磁介质的磁化，在磁感应强度$\boldsymbol{B}$的基础上上又增加的两个磁场量。在研究电介质的极化时也曾引入电极化强度$\boldsymbol{P}$和电位移矢量$\boldsymbol{D}$.下面对这些量进行对比分析。\
**1.磁化强度$\boldsymbol{M}$与电极化强度$\boldsymbol{P}$**\
&emsp;&emsp;磁化强度$\boldsymbol{M}$的定义与电极化强度$\boldsymbol{P}$的定义式非常相似：

$$\boldsymbol{M}=\cfrac{\sum\limits_{i=1}^n\boldsymbol{m}_ i }{\Delta V}\qquad \boldsymbol{P}=\cfrac{\sum\limits _{i=1}^n\boldsymbol{p}_i }{\Delta V}\tag{9.10}$$

&emsp;&emsp;磁化强度$\boldsymbol{M}$描述磁介质受到磁化的情况，而磁介质磁化时伴有磁化电流$I'$.所以这两者还是有联系的：\
$$\oint_ L\boldsymbol{M\ \cdot}\mathrm{d}\boldsymbol l=\sum I'\tag{9.11}$$

&emsp;&emsp;其中，$\sum I'$表示穿过环路$L$的所有磁化电流之和。\
&emsp;&emsp;类似地，电极化强度$\boldsymbol{P}$描述电介质在外电场中产生的极化情况，而电介质极化时会产生束缚电荷$q'$.这两者有如下的联系：
$$\oint_ S\boldsymbol{P\ \cdot}\mathrm{d}\boldsymbol S=-\sum q'\tag{9.12}$$

&emsp;&emsp;其中，$\sum q'$表示高斯面$S$内所有的束缚电荷之和。式$(9.11)$与$(9.12)$在形式上非常相似，需要注意的是式$(9.12)$<st>多出了一个负号</st>。\
**2.磁场强度$\boldsymbol H$和电位移矢量$\boldsymbol D$**\
&emsp;&emsp;磁场强度$\boldsymbol{H}$，给我带来的直观感受是，它是磁感应强度$\boldsymbol{B}$在磁介质存在情况下，为了保证某种连续性而定义的表征磁场的量。这是它的定义式
$$\boldsymbol{H}=\cfrac{\boldsymbol B}{\mu_r\mu_0}=\cfrac{\boldsymbol B}{\mu}\tag{9.13}$$

&emsp;&emsp;可以看到，连接磁场强度$\boldsymbol H$与磁感应强度$\boldsymbol B$的桥梁是磁导率$\mu$.\
&emsp;&emsp;在没有磁介质的情况下，磁感应强度$\boldsymbol{B}$在空间内是连续的，因此磁感线也是连续的。但是，在有磁介质的情况下，磁感应强度矢量$\boldsymbol{B}$将会失去它的空间连续性，也就是说，$\boldsymbol B$会<st>在不同磁介质的交界处发生跳变</st>。这一跳变是不同的磁导率造成的。不过这个时候$\boldsymbol H$却具有空间连续性，因此用它描述磁场是比较理想的。\
&emsp;&emsp;当然，对于电场强度$\boldsymbol E$和电极化强度$\boldsymbol D$来说，上面的性质也是成立的。在空间中存在电介质的情况下，$\boldsymbol E$的空间连续性将失去，$\boldsymbol D$的空间连续性将被保留。教材中对于$\boldsymbol D$的引入是下式：
$$\boldsymbol D=\varepsilon _0\boldsymbol E+\boldsymbol P\tag{9.14}$$

&emsp;&emsp;我认为这样的引入很不妥当。可以给出类似式$(9.13)$的定义：
$$\boldsymbol D=\varepsilon_ r\varepsilon_ 0\boldsymbol E=\varepsilon \boldsymbol E\tag{9.15}$$

&emsp;&emsp;从式$(9.15)$能够看到，电位移矢量$\boldsymbol D$与电场强度$\boldsymbol E$之间是通过介电常数$\varepsilon$联系起来的。\
&emsp;&emsp;此外，我们发现磁场强度$\boldsymbol H$与磁化强度$\boldsymbol M$具有相同的量纲，实际上也有积分式
$$\oint_ L\boldsymbol{H\ \cdot}\mathrm{d}\boldsymbol l=\sum I\tag{9.16}$$

&emsp;&emsp;其中，$\sum I$表示穿过环路$L$的所有传导电流之和。我们大致能够得出这样的结论：$\boldsymbol H$描述的是空间某点本来的磁场，$\boldsymbol M$描述这一点由磁介质产生的磁场，$\boldsymbol B$是由前面两个磁场叠加得到的、描述该点实际磁场情况的物理量。这正如式$(9.17)$所描述的那样。
$$\oint_ L(\boldsymbol H+\boldsymbol M)\ \boldsymbol\cdot\mathrm{d}\boldsymbol l=\sum(I+I')=\oint _L \cfrac{\boldsymbol B}{\mu_0}\boldsymbol\cdot\mathrm{d}\boldsymbol l\tag{9.17}$$

&emsp;&emsp;类似地，在存在电介质的电场中，我们也有式$(9.18)$和式$(9.19)$.
$$\oint_ S\boldsymbol{D\ \cdot}\mathrm{d}\boldsymbol S=\sum q\tag{9.18}$$

$$\oint_ S(\boldsymbol D-\boldsymbol P)\ \boldsymbol\cdot\mathrm{d}\boldsymbol S=\sum(q+q')=\oint _S \varepsilon_0\boldsymbol E\boldsymbol\cdot\mathrm{d}\boldsymbol l\tag{9.19}$$

&emsp;&emsp;式$(9.18)$中，$\sum q$表示高斯面$S$内所有的自由电荷之和。\
**六、磁化电流面密度**\
&emsp;&emsp;首先应指出，电流面密度<st>不是</st>电流密度。通常意义上的电流$I$单位是$\mathrm{A}$，流过一根直线，沿着电流垂面方向截得一个点。电流流过一个平面时，沿着电流垂面方向截得一条直线，因此用电流面密度$i$描述，单位$\mathrm{A/m}$.电流流过一个立体时，沿电流垂面方向截得一个平面，因此用电流密度$j$描述，单位$\mathrm{A/m^2}$.\
&emsp;&emsp;磁化电流是上面的第二种，用磁化电流面密度$i_\mathrm{m}$描述。一般要求$i_\mathrm{m}$有两种思路，第一种是根据定义：
$$i_\mathrm{m}=\cfrac{\mathrm{d}I}{\mathrm{d}L}=\cfrac{I}{L}\tag{9.20}$$

&emsp;&emsp;其中$i_\mathrm{m}=\cfrac{I}{L}$只适合于电流沿$L$均匀分布的情况。如果题目中给出了，或者可以求得磁化强度$\boldsymbol M$，也可以采用第二种求法：
$$\boldsymbol i _\mathrm{m}=\boldsymbol{M\ \times e} _\mathrm{n}\tag{9.21}$$

&emsp;&emsp;其中$\boldsymbol e_\mathrm{n}$是磁介质表面法向单位矢量。此时磁化电流面密度的大小$i_\mathrm{m}=M$.

## $Chapter10$&emsp;电磁感应
**一、感应电动势**\
&emsp;&emsp;电源电动势，是**非静电场**场强$\boldsymbol E_\mathrm{k}$从负极到正极的曲线积分：
$$\mathscr{E}=\int _-^+\boldsymbol E _\mathrm{k}\cdot\mathrm{d}\boldsymbol l\tag{10.1}$$

&emsp;&emsp;比如**动生电动势**的情况下，就有$\boldsymbol E _ \mathrm{k}=\boldsymbol{v\times B}$，此时的非静电力是洛伦兹力。有些情况这种非静电力分散在回路的各个角落，分不清电源正负极，那么
$$\mathscr{E}=\oint _L\boldsymbol E _\mathrm{k}\cdot\mathrm{d}\boldsymbol l\tag{10.2}$$

&emsp;&emsp;沿着闭合回路积分即可。**动生电动势**中，如果金属导体本身构成了回路，就适用式$(10.2).$**感生电动势**也属于这种情况，非静电场是感应电场，感应电动势分布在导体的各个部分。\
&emsp;&emsp;感应电场具有有旋场的性质，是一个非保守场，当然不能引入电势的概念。但是，对于<st>感应电场中的导体</st>，我们仍然可以研究导体上$a$点与$b$点的电势差是多少，因为这里的“电势”是针对<st>导体内部电场</st>而言的，由于导体电阻的压降，其内部的电场仍然是一个保守场。\
&emsp;&emsp;不过，所求的电动势如果是感应电动势的话，除了电动势的定义，也不要忘掉唯一真神——法拉第电磁感应定律：
$$\mathscr{E} _ \mathrm i=-\cfrac{\mathrm d\varPhi}{\mathrm dt}\tag{10.3}$$

&emsp;&emsp;如果导体构成的回路不随时间变化，即$S$是常量，那么式$(10.3)$也可以写成：
$$\mathscr E _ \mathrm i =-\int \cfrac{\partial\boldsymbol B}{\partial t}\boldsymbol\cdot\mathrm d\boldsymbol S\tag{10.4}$$

&emsp;&emsp;这个在感生电动势中使用得比较多。\
**二、磁场能量**\
&emsp;&emsp;和电场一样，磁场本身也具有能量。
<table align="center">
    <caption>表 电场和磁场能量对比</caption>
    <tr>
        <th></th>
        <th>电场</th>
        <th>磁场</th>
    </tr>
    <tr>
        <th>能量</th>
        <td>电容中<br>$$W _ \mathrm e =\cfrac{1}{2}CU^2$$</td>
        <td>电感中<br>$$W _ \mathrm m =\cfrac{1}{2}LI^2$$</td>
    </tr>
    <tr>
        <th>能量密度</th>
        <td>$$w _ \mathrm e=\cfrac{1}{2}\boldsymbol{E\cdot D}=\cfrac{1}{2}\varepsilon E^2$$</td>
        <td>$$w _ \mathrm m=\cfrac{1}{2}\boldsymbol{B\cdot H}=\cfrac{B^2}{2\mu}$$</td>
    </tr>
</table>

**三、麦克斯韦方程组（Maxwell\'s Equations）**\
&emsp;&emsp;麦克斯韦方程组的前两式表示了电场、磁场本身的特性。电场有源，磁场无源：
$$\oint _ S\boldsymbol{D\cdot}\mathrm d\boldsymbol S=\sum q=\int _ V \rho\mathrm dV\tag{10.5}$$

$$\oint _ S\boldsymbol{B\cdot}\mathrm d\boldsymbol S=0\tag{10.6}$$

&emsp;&emsp;式Ⅲ是经典的“磁生电”：
$$\oint _ L \boldsymbol{E\cdot}\mathrm d\boldsymbol l=-\int _ S \cfrac{\partial\boldsymbol B}{\partial t}\boldsymbol\cdot \mathrm d\boldsymbol S\tag{10.7}$$

&emsp;&emsp;个人感觉麦克斯韦方程组的核心是位移电流概念的引入。空间中电位移矢量的变化$\cfrac{\partial\boldsymbol D}{\partial t}$（单位$\mathrm{A/m^2}$）具有和传导电流$I$一样的磁效应，从而修正了安培环路定理：
$$\oint _ L\boldsymbol{H\cdot}\mathrm d\boldsymbol l=I+I _ d=\int _ S\left(\boldsymbol j+\cfrac{\partial \boldsymbol D}{\partial t}\right)\boldsymbol\cdot\mathrm d\boldsymbol S\tag{10.8}$$

&emsp;&emsp;这是方程组的式Ⅳ，定量描述“电生磁”。\
&emsp;&emsp;同时，注意**位移电流是真实存在的**。意思不是说位移电流是一种真正意义上的电流，这是一个比较抽象的事情。

## $Chapter 11$&emsp;振动与波动
**一、关于频率相同、方向垂直的简谐运动合成**\
&emsp;&emsp;运动可以用参数方程描述：
$$\begin{cases}
x=A _ 1\cos(\omega t+\varphi _ 1)\\\\ y=A _ 2\cos(\omega t+\varphi _ 2)\end{cases}\tag{11.1}$$

&emsp;&emsp;我们已经知道消去$t$后的运动方程是
$$\cfrac{x^2}{A _1^2}+\cfrac{y^2}{A _2^2}-\cfrac{2xy}{A _1A _2}\cos(\varphi _2-\varphi _1)=\sin^2(\varphi _2-\varphi _1)\tag{11.2}$$

&emsp;&emsp;可以是这样推导的。记$\theta _ 1=\omega t+\varphi _1,\theta _2=\omega t+\varphi _2$.
$$\begin{aligned}\sin^2(\varphi _2-\varphi _1)&=\sin^2(\theta _2-\theta _1)\\\\
&=(\sin\theta _2\cos\theta _1-\cos\theta _2\sin\theta _1)^2\\\\
&=(1-\cos^2\theta _2)\cos^2\theta _1+(1-\cos^2\theta _1)\cos^2\theta _2-2\cos\theta _1\cos\theta _2\sin\theta _1\sin\theta _2\\\\
&=\cos^2\theta _1+\cos^2\theta _2-2\cos \theta _1\cos\theta _2(\cos\theta _1\cos\theta _2+\sin\theta _1\sin\theta _2)\\\\
&=\cfrac{x^2}{A _1^2}+\cfrac{y^2}{A _2^2}-\cfrac{2xy}{A _1A _2}\cos(\theta _2-\theta _1)\\\\
&=\cfrac{x^2}{A _1^2}+\cfrac{y^2}{A _2^2}-\cfrac{2xy}{A _1A _2}\cos(\varphi _2-\varphi _1)\end{aligned}\tag{11.3}$$

**二、关于阻尼振动**\
&emsp;&emsp;阻尼振动的方程为
$$\cfrac{\mathrm{d}^2x}{\mathrm dt^2}+2\beta\cfrac{\mathrm dx}{\mathrm dt}+\omega _0^2x=0\tag{11.4}$$

&emsp;&emsp;书上只说明了在弱阻尼情况下$(\beta < \omega _0)$的通解：
$$x=A _0\mathrm{e}^{-\beta t}\cos\left(\sqrt{\omega _0^2-\beta^2}t+\varphi _0\right)\tag{11.5}$$

&emsp;&emsp;实际上我们可以对微分方程$(11.4)$进行求解。它的特征方程是：
$$\lambda^2+2\beta\lambda+\omega _0^2=0\tag{11.6}$$

&emsp;&emsp;这是一个一元二次方程，判别式$\Delta=4(\beta^2-\omega _0^2)$.\
&emsp;&emsp;在**弱阻尼**$(\beta < \omega _0)$情况下，$\Delta < 0$，记$\omega=\sqrt{\omega _0^2-\beta^2}$，式$(11.6)$有共轭复根
$$\lambda _{1,2}=-\beta\pm\omega \mathrm{i}\tag{11.7}$$

&emsp;&emsp;从而得到$(11.4)$的解为$x=\mathrm{e}^{-\beta t}(C _1\cos\omega t+C _2\sin\omega t)$.这一形式同式$(11.5)$.\
&emsp;&emsp;在**过阻尼**$(\beta > \omega _0)$情况下，$\Delta > 0$，记$\omega'=\sqrt{\beta^2-\omega _0^2}$，式$(11.6)$有两根
$$\lambda _{1,2}=-\beta\pm\omega'\tag{11.8}$$

&emsp;&emsp;此时运动方程$(11.4)$的解的形式为
$$x=\mathrm e^{-\beta t}(A _1\mathrm e^{\omega' t}+A _2\mathrm e^{-\omega' t})\tag{11.9}$$

&emsp;&emsp;在**临界阻尼**$(\beta = \omega _0)$情况下，$\Delta =0$，此时$(11.6)$有重根
$$\lambda _{1,2}=-\beta\tag{11.10}$$

&emsp;&emsp;也可以由此得到运动方程$(11.4)$的解为
$$x=\mathrm e^{-\beta t}(A _0+A _1t)\tag{11.11}$$

&emsp;&emsp;可以统一$(11.4)$的解的形式为$x=\mathrm e^{-\beta t}f(t)$.临界阻尼情况下的$f(t)$是多项式，过阻尼情况下的$f(t)\sim \mathrm e^{|\omega'|t}$ 是指数阶，所以临界阻尼衰减得比过阻尼快。\
**三、波的能量**\
&emsp;&emsp;机械波$y(x,t)=A\cos[\omega(t-\cfrac{x}{u})+\varphi]$在密度为$\rho$的介质中传播时，在任意时刻，某一质元的动能和势能都是相等的。\
&emsp;&emsp;波的平均能量密度$\overline w=\cfrac{1}{2}\rho A^2\omega^2$.\
&emsp;&emsp;波的平均能流密度$I=\overline wu=\cfrac{1}{2}\rho A^2\omega^2u$.\
**四、多普勒效应**\
&emsp;&emsp;当波源（Source）和接收器（Receiver）以接近速度$v _S$和$v _R$相对运动时，有
$$\nu _R=\cfrac{u+v _R}{u-v _S}\nu _S\tag{11.12}$$

&emsp;&emsp;这是机械波的多普勒效应，**观测者体现在分子，波源体现在分母**。其实为了方便记忆，可以将式$(11.12)$变形为式$(11.13)$：
$$\cfrac{\nu _R}{u+v _R}=\cfrac{\nu _S}{u-v _S}\tag{11.13}$$

&emsp;&emsp;接收器在左边，波源在右边。至于$v _R,v _S$前的符号，可以根据常识推断。\
&emsp;&emsp;如果是电磁波的多普勒效应，那就需要考虑相对论因素：
$$\nu _R=\sqrt{\cfrac{c+v}{c-v}}\nu _S\tag{11.14}$$

&emsp;&emsp;方便记忆，也可以变形为如下形式：
$$\cfrac{\nu _R}{\sqrt{c+v}}=\cfrac{\nu _S}{\sqrt{c-v}}\tag{11.15}$$
**五、其他想说的**\
&emsp;&emsp;劲度系数分别为$k _1,k _2$的两根轻弹簧，首尾相连（串行连接）构成劲度系数为$\cfrac{k _1k _2}{k _1+k _2}$的弹簧。如果是把头与头相连、尾与尾相连（并行连接），则构成劲度系数为$k _1+k _2$的弹簧。

## $Chapter 13$&emsp;波动光学
&emsp;&emsp;波动光学，由于之前并未过多接触，所以看起来公式量有些多。但其实也还好，每个知识点都记住一些个**核心公式**就好了，然后从这些比较核心的公式，以比较小的代价去推导其他的公式。\
&emsp;&emsp;这一章需要牢牢扣住<st>光程差$\delta$</st>这一个要点。光程差可以与相位差产生联系：
$$\delta=\cfrac{\lambda}{2\pi}\Delta\varphi\tag{13.1}$$

&emsp;&emsp;从而判断两束光波在某处的叠加情况。这一章的另外一个要点是<st>近似处理</st>。\
**一、双缝干涉（杨氏双缝干涉）**\
&emsp;&emsp;距离为$d$的两个小孔，将它们看作两个**初相位相同**的光源，它们发出的光的强度在距离为$D$的屏幕上发生相干叠加。光程差：
$$\delta=nr _1-nr _2\approx nd\sin\theta\tag{13.2}$$

&emsp;&emsp;式$(13.2)$是双缝干涉的基本公式，约等号处使用了近似处理。可以由它推导其他公式。\
&emsp;&emsp;由于$\theta$很小，近似有$\sin\theta\approx\theta\approx\tan\theta=\cfrac{x}{D}$，其中$x$是干涉点到屏幕中心店的距离。将其与代入式$(13.2)$，就有：
$$\delta=nd\sin\theta\approx\cfrac{ndx}{D}\tag{13.3}$$

&emsp;&emsp;由$Chapter11$的内容，能够比较容易地想到下面的情况：
$$\Delta\varphi=\begin{cases}2k\pi&\text{合振幅极大},\\\\
(2k-1)\pi&\text{合振幅极小}. \end{cases}\tag{13.4}$$

&emsp;&emsp;所以，结合式$(13.1)$，得到
$$\delta=nd\sin\theta=\begin{cases}k\lambda& \text{光强极大},\\\\\left
(k-\cfrac{1}{2}\right)\lambda& \text{光强极小}.\end{cases}\tag{13.5}$$

&emsp;&emsp;显然光强极大对应明纹，光强极小对应暗纹。\
&emsp;&emsp;除了上述方法，也可以只记下面的公式：
$$I _\theta=I _0\cos^2\beta\tag{13.6}$$

&emsp;&emsp;其中的$\beta=\cfrac{\pi nd\sin\theta}{\lambda}$.一般实验都在$n\approx 1$的空气中进行，$\beta=\cfrac{\pi d\sin\theta}{\lambda}$.显然，$\cos^2\beta=1$对应明纹，$\cos^2\beta=0$对应暗纹。

**二、分振幅干涉**\
&emsp;&emsp;先考虑**等倾干涉**，同样可以记住一个基本公式：
$$\delta=2nd\cos\gamma\tag{13.7}$$

&emsp;&emsp;实际如果两个反射面中只有一处发生半波损失，$\delta$还应该加上$\cfrac{\lambda}{2}$.这个公式当然可以现场推导，但是花费的时间会比较多，建议记住。可以通过这个推导明暗纹条件。\
&emsp;&emsp;**等厚干涉**就是对每一个厚度$d$，都考虑式$(13.7)$，每个厚度对应相同的一个光程差$\delta$.\
&emsp;&emsp;对于等倾干涉来说，$\gamma$是一个变量，$\delta$随$\gamma$的变化而不同，因此相同$\gamma$的点（一个一个同心圆）对应相同的$\delta$，从而干涉情况相同。对于等厚干涉来说，$\gamma=0$（即只考虑正入射），但是$d$是变量，$\delta$随$d$的变化而不同，因此相同$d$的点（一系列平行线）对应相同的$\delta$，从而干涉情况相同。\
**三、单缝衍射（单缝夫琅禾费衍射）**\
&emsp;&emsp;公式的推导略显复杂，我们只需要记住结果：产生与狭缝平行的干涉条纹，强度为
$$I _\theta=I _0 \left(\cfrac{\sin\alpha}{\alpha}\right)^2\tag{13.8}$$

&emsp;&emsp;如果实验在$n=1$的环境下进行，$\alpha=\cfrac{\pi a\sin\theta}{\lambda}$.如果$n\neq 1$也一样，$\lambda$代表在介质中的波长。根据该式可以推出各暗纹（极小）的位置，明纹（极大）的位置也可以近似地计算。\
**四、多缝衍射**\
&emsp;&emsp;多缝衍射需要同时考虑干涉和衍射的结果，光强公式为：
$$I _\theta=I _0\left(\cfrac{\sin\alpha}{\alpha}\right)^2\left(\cfrac{\sin N\beta}{\sin\beta}\right)^2\tag{13.9}$$

&emsp;&emsp;$\alpha$是和衍射有关的参数，$\beta$是和干涉有关的参数。实际上，当$N=2$时，式$(13.9)$变为
$$I _\theta=4I _0\left(\cfrac{\sin\alpha}{\alpha}\right)^2\cos^2\beta\tag{13.10}$$

&emsp;&emsp;这个和双缝衍射的$I _\theta=I _0\left(\cfrac{\sin\alpha}{\alpha}\right)^2\cos^2\beta$具有相同的形式。

$\boxed{\mathbb{The\ End}.}$
