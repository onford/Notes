<style>
    h1,h2,h3,h4{
        border-bottom : none;
        font-family: "Times New Roman","黑体";
        font-weight: bold;
        color: #4f4f4f;
        margin-top: 24px;
    }
    h1{
        font-size:30px;
        /* margin-bottom: 0px; */
    }
    h2{
        font-size:24px;
        /* margin-bottom: -2px; */
    }
    h3{
        font-size:20px;
        /* margin-bottom: -5px; */
    }
    h4{
        font-size:17px;
        /* margin-bottom: -8px; */
    }
    hr{
        margin: 24px 0;
        border: none;
        border-bottom: 1px solid #ddd;
    }
    p,div,li{
        font-family: "Times New Roman","宋体";
        font-size:17px;
    }
    a,a:visited {
        color: #6795b5;
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
        padding: 0;
        font-size:17px;
        font-family:"Times New Roman","宋体";
        border: 1px solid;
        text-align:center;
    }
    caption{
        font-family:"Times New Roman","黑体";
        font-size:17px;
    }
    code {
	    color: #c7254e;
        background-color: #f9f2f4;
        border-radius: 2px;
    }
</style>

# 信号与线性系统

<bw>wr按：\
《信号与线性系统》这门课全程依赖电路知识，以《电路理论》初级篇为先导，其内容相当于电路理论中部分内容的详细拓展。这一篇笔记会记录我自己的一些观点和看法（专门记我看不懂的）。</bw>

---
## $Chapter1$&emsp;绪论
&emsp;&emsp;一个系统存在着激励 $e(t)$ 和响应 $r(t)$。
### 系统具有的性质  
#### 线性性
&emsp;&emsp;一个系统具备线性性，其抽象表述为：若 $e(t)\rightarrow r(t)$，则 $k _1e _1(t)+k _2e _2(t)\rightarrow k _1r _1(t) +k _2r _2(t)$。
#### 非时变性
&emsp;&emsp;一个系统具备非时变性（时不变性），其抽象表述为：若 $e(t)\rightarrow r(t)$，则 $e(t-t _0)\rightarrow r(t-t _0)$。
#### 因果性
&emsp;&emsp;一个系统在 $t$ 时刻的响应，只和 $t$ 时刻及其之前的时刻的激励有关。

&emsp;&emsp;上面的三个性质中，因果性是最好判定的。只需看 $r(t)$ 的表达式即可。线性性也是好判定的，直接根据抽象定义，构造两个激励 $e _1(t)$ 和 $e _2(t)$ 并判断是否具有该性质即可。\
&emsp;&emsp;关于时不变性的判定，可以构造两个激励 $e _1(t)$ 和 $e _2(t)$，其中 $e _2(t)$ 是 $e _1(t)$ 平移得到的，从而转化为判定：若 $e _1(t)\rightarrow r _1(t)$，是否有 $e _2(t)\rightarrow r _2(t)$。
<blockquote>
&emsp;&emsp;关于时不变性的判定，举个例子：$r(t)=e(1-t)$。这是在习题中碰到的。这个系统是不具备时不变性的，可以按照下面的方式判定：<br>
&emsp;&emsp;记 $e _1(t)\rightarrow e _1(1-t) = r _1(t)$，$e _2(t)=e _1(t-t _0)$。那么 $r _2(t)=e _2(1-t)=e _1(1-t-t _0)=r _1(t+t _0)\neq r _1(t-t _0)$。因此，若 $e(t)\rightarrow r(t)$，无法得到 $e(t-t _0)\rightarrow r(t-t _0)$。<br>
&emsp;&emsp;之所以单独强调时不变性，是因为产生过一个莫名其妙的错误做法：<br>
&emsp;&emsp;将原式中的 $t$ 换成 $t-t _0$ 可得 $r(t-t _0)=e(1-t+t _0)$，记作式 $(1)$。所以对于一个激励 $e(t-t _0)$，根据原式，它产生的响应应该是 $e(1-t+t _0)$，也即 $r(t-t _0)$。所以系统具备时不变性。<br>
&emsp;&emsp;这种错误做法看起来有点像是循环论证，但是它却能够正确地判断 $r(t)=\varepsilon(t)e(t)$ 不具备时不变性。所以花了一个下午的时间总结出时不变性的正确判定方法，并且特意强调，以免以后再落入这个陷阱。
</blockquote>

### 各种各样的响应
#### 古典法
&emsp;&emsp;古典法依据微分方程的数学解形式来定义系统的不同响应。一个 $n$ 阶线性系统的微分方程可以用下面的式子来表示：
$$\cfrac{\mathrm d^nr}{\mathrm dt^n}+a _{n-1}\cfrac{\mathrm d^{n-1}r}{\mathrm dt^{n-1}}+\cdots+a _1\cfrac{\mathrm dr}{\mathrm dt}+a _0r=b _m\cfrac{\mathrm d^me}{\mathrm dt^m}+b _{m-1}\cfrac{\mathrm d^{m-1}e}{\mathrm dt^{m-1}}+b _1\cfrac{\mathrm de}{\mathrm dt}+b _0e\tag{1.1}$$

&emsp;&emsp;这个微分方程对应的齐次方程的通解（通过初值条件确定待定系数），被称作系统的**自然响应（自由响应）**，记作 $r _h(t)$。微分方程对应的特解（也通过初值条件确定了待定系数）被称作系统的**受迫响应**，记作 $r _p(t)$。
<blockquote>
&emsp;&emsp;回顾一下高数里求解微分方程的过程，通解往往带有待定系数 $C _1,C _2\cdots$，但是特解是不带的。这就说明系统的自由响应 $r _h(t)$ 受系统初值的影响，但是受迫响应 $r _p(t)$ 不受影响。<br>
&emsp;&emsp;同时，只有全解出来了，才能确定 $r _h(t)$ 的系数。因此 $r _h(t)$ 的求解会受到 $r _p(t)$ 的制约。
</blockquote>

#### 近代时域分析法
&emsp;&emsp;近代的时域分析法就把响应分为**零输入响应** $r _{zi}(t)$ 和**零状态响应** $r _{zs}(t)$。这一点同电路理论中的概念。\
&emsp;&emsp;这些响应与全响应 $r(t)$ 之间的关系是：
$$r _h(t)=r _{zi}(t)+r _{zs}(t)=r _h(t)+r _p(t)\tag{1.2}$$

## $Chapter2$&emsp;连续时间系统的时域分析
### 基于冲激函数的信号分解
&emsp;&emsp;这一章首先证明了下面的公式：
$$f(t)=\int _0^tf(\tau)\delta(t-\tau)\mathrm d\tau=\int _{-\infty}^{+\infty}f(\tau)\delta(t-\tau)\mathrm d\tau\tag{2.1}$$

<blockquote>
&emsp;&emsp;式 $(2.1)$ 在书上是通过极限逼近的思想得到的，当然也可以直接利用冲激函数的筛分特性得到。
</blockquote>

&emsp;&emsp;这说明一个信号可以分解成多个多个冲击信号的积分。
### 卷积积分
#### 卷积积分引出
&emsp;&emsp;基于式 $(2.1)$，推导出了一个通过 $e(t)$ 迅速求得 $r(t)$ 的有效办法。记一个系统的单位冲击响应为 $h(t)$ ，即 $\delta(t)\rightarrow h(t)$。由于<st>线性系统</st>的时不变性、齐次性和叠加性，可得 $$\displaystyle\int _0^te(t)\delta(t-\tau)\mathrm d\tau\rightarrow \int _0^te(t)h(t-\tau)\mathrm d\tau\tag {2.2a}$$

<blockquote>&emsp;&emsp;$h(t)$ 是激励为单位冲激函数 $\delta(t)$ 的<strong>零状态响应</strong>，这是 $h(t)$ 的定义。上段文字中“线性系统”四个字标红，因为含有初始值（初始状态）的系统从定义上来说并不是线性系统。<br>
&emsp;&emsp;基于这两个原因，不难理解后文中 $(2.2\mathrm b)$ 求得的 $r(t)$ 只是零状态响应。
</blockquote>

&emsp;&emsp;根据式 $(2.1)$ 知，式 $(2.2\mathrm a)$ 的左边就是 $e(t)$。那么式 $(2.2\mathrm a)$ 的右边当然就是对应的 $r(t)$ 了。因此，激励为 $e(t)$ 时，系统的响应可以通过下式求得：
$$r(t) = \int _0^te(t)h(t-\tau)\mathrm d\tau\tag{2.2b}$$

&emsp;&emsp;式 $(2.2\mathrm b)$ 就是**卷积积分**，且这里求出来的 $r(t)$ 是**零状态响应**。

<blockquote>
&emsp;&emsp;如果可以知道一个系统的单位冲击响应 $h(t)$，根据式 $(2.2)$ 可以直接从激励得到响应，而不需要知道系统的其它细节。
</blockquote>

#### 卷积的定义
&emsp;&emsp;卷积运算是一种抽象出来的运算，它的定义是：
$$f(t) * g(t)=\int_{-\infty}^{+\infty}f(\tau)g(t-\tau)\mathrm d\tau\tag{2.3}$$

#### 卷积的性质
&emsp;&emsp;和很多运算类似，卷积具有**交换律**、对加减法的**分配律**以及**结合律**。对于卷积结果进行微积分运算，有下列结论成立：
$$\cfrac{\mathrm d}{\mathrm dt}[u(t) * v(t)]=u(t) * \cfrac{\mathrm dv(t)}{\mathrm dt}=\cfrac{\mathrm du(t)}{\mathrm dt} * v(t)\tag{2.4}$$

$$\int_{-\infty}^t[u(x) * v(x)]\mathrm dx=u(t) * \left[\int_{-\infty}^tv(x)\mathrm dx\right]=\left[\int_{-\infty}^tu(x)\mathrm dx\right] * v(t)\tag{2.5}$$

&emsp;&emsp;上面的式子当然可以推广到多个函数卷积的导数/积分，以及卷积结果的多阶导数/积分。需要注意的是，$(2.4)$ 的使用没有限制条件，但是 $(2.5)$ 是**不能随便使用**的。这是因为在引入了奇异函数 $\varepsilon(t),\delta(t),\delta'(t)$ 等后，几乎所有的<st>真实信号函数</st>都是无穷阶可导的，但是不是所有函数都可以执行变上限积分。在应用式 $(2.5)$ 是，显然需要保证我们选择的积分函数是可积的。
<blockquote>
&emsp;&emsp;式 $(2.5)$ 的使用前提是显然的，如果在使用 $(2.5)$ 时出现了类似于 $\displaystyle\int_{-\infty}^tx\mathrm dx$ 这种不收敛的反常积分，你一眼就知道不能这样做，自己的做法有问题。<br>
&emsp;&emsp;比如使用 $(2.5)$ 的一半 $\displaystyle\int_{-\infty}^t[u(x) * v(x)]\mathrm dx=u(t) * \left[\int_{-\infty}^tv(x)\mathrm dx\right]$ 时，至少要保证 $\displaystyle\int_{-\infty}^t[u(x) * v(x)]\mathrm dx$ 和 $\displaystyle\int_{-\infty}^tv(x)\mathrm dx$ 都是存在的，而无需考虑 $\displaystyle\int_{-\infty}^tu(x)\mathrm dx$ 是否存在。
</blockquote>

&emsp;&emsp;特别地，根据式子 $(2.4)(2.5)$，可以得到一个比较有用的结果：
$$u(t) * v(t)=\cfrac{\mathrm du(t)}{\mathrm dt} * \int_{-\infty}^tv(x)\mathrm d x\tag{2.6}$$

&emsp;&emsp;上式还能互换 $u(t),v(t)$ 的地位，这里略去不写。式 $(2.6)$ 的使用条件是 $\displaystyle\int_{-\infty}^tv(x)\mathrm dx$ 存在，且<st> $\lim\limits_{t\rightarrow -\infty}u(t) * v(t)=0$</st>。红色的式子也可以等价地表述为 $u(t) * v(t)=\displaystyle\int_{-\infty}^t[u(x) * v(x)]'\mathrm dx$。\
&emsp;&emsp;这是因为式 $(2.6)$ 可以看作是对式子 $u(t) * v(t)=u(t) * v(t)$ 两边分别运用 $(2.4)(2.5)$ 得到的，只不过等号右边选择了不同的函数进行操作。需要注意的是，左边的 $u(t) * v(t)$ 在进行微分、积分后要能够还原出 $u(t) * v(t)$。如果先进行微分，那么：
$$\int_{-\infty}^t\cfrac{\mathrm d[u(x) * v(x)]}{\mathrm dx}\mathrm dt=u(t) * v(t)-u(-\infty) * v(-\infty)\tag{2.7}$$

&emsp;&emsp;显然只有满足 $\lim\limits_{x\rightarrow -\infty}u(t) * v(t)=0$，左边才能复原。如果先进行积分，那么首先就要保证 $\displaystyle\int_{-\infty}^t[u(x) * v(x)]\mathrm dx$ 存在，显然也需要满足 $\lim\limits_{x\rightarrow -\infty}u(t) * v(t)=0$，否则反常积分不收敛。
<blockquote>
&emsp;&emsp;同时，有的地方说 $(2.6)$ 成立的条件是 $u(t)=\displaystyle\int_{-\infty}^tu'(x)\mathrm dx$，也就是 $\lim\limits_{x\rightarrow -\infty}u(x)=0$，这个条件仅仅是充分条件，其必要性不成立。<br>
&emsp;&emsp;考虑 $u(t)=1+\varepsilon(t),v(t)=\left[\mathrm e^{-t}-\cfrac{1}{(t+1)^2}\right]\varepsilon(t)$，虽然不满足 $\lim\limits_{x\rightarrow -\infty}u(x)=0$，但是依然可以使用 $(2.6)$ 式：
$$u(t) * v(t)=\delta(t) * \int_{-\infty}^t\left[\mathrm e^{-x}-\cfrac{1}{(x+1)^2}\right]\varepsilon(x)\mathrm dx=\varepsilon(t)\int_0^t\left[\mathrm e^{-x}-\cfrac{1}{(x+1)^2}\right]\mathrm dx=\left(\cfrac{1}{t+1}-\mathrm e^{-t}\right)\varepsilon(t)\tag{2.8}$$
</blockquote>

&emsp;&emsp;除此之外，还有一个延时的性质：若 $f(t)=f _1(t) * f _2(t)$，则有 $f(t-t _1-t _2)=f _1(t-t _1) * f _2(t-t _2)$。

### 系统响应的时域求解
&emsp;&emsp;正如所提到的[第一章](#各种各样的响应)中所提到的那样，一个线性系统至少包含 $4$ 种类型的响应，其中又包含一种特殊的**单位冲击响应**。下面归纳一下这些响应的求解方法。

#### 单位冲激响应 $h(t)$
<blockquote>
&emsp;&emsp;单位冲激响应的求解，书上给出了一种解法，老师给出了一种解法。<br>
&emsp;&emsp;书上给出的解法叫做<strong>海维赛德部分因式分解法</strong>。这种方法很好，也非常容易掌握，但是老师没讲。这是因为该方法基于拉普拉斯变换，并且使用起来和拉普拉斯变换法高度相似。所以只需要掌握拉普拉斯变换就好了。<br>
&emsp;&emsp;因此我们在这一章需要学会老师的解法。
</blockquote>

&emsp;&emsp;单位冲激响应其实是 $0^+$ 系统的零输入响应。这给了我们求解 $h(t)$ 的思路：
- 系统在 $0^-$ 时刻是零状态的，即 $r^{(n)}(0^-)=0$。在 $t=0$ 时刻忽然到来的激励 $\delta(t)$ 改变了系统的状态，使得 $r^{(n)}(0^+)\neq 0$。
- 系统在 $t\geq 0^+$ 时按照零输入响应的方式求解——列微分方程，根据初值 $r^{(n)}(0^+)$ 求取微分方程的**通解** $h(t)$。

&emsp;&emsp;求微分方程的通解自然是容易的，关键在如何求系统的初值 $r^{(n)}(0^+)$ 。这个初值可以用**冲击平衡法**求取。\
&emsp;&emsp;在引入奇异函数后，我们可以将常见信号大致分为以下 $2$ 类：**连续函数**，**非连续的连续函数的导数**（后文简称非连续函数）。其中非连续函数可以写成 $\varepsilon^{(n)}(t)(n\geq 0)$ 或其组合的形式，其中最大的 $n$ 值为其**间断阶**（这是为了方便理解编造的术语）。比如 $x(t)=\varepsilon(t)+\delta'(t)$ 的间断阶为 $2$。
<blockquote>
&emsp;&emsp;考虑一个连续函数 $x(t)$ 在某个点 $t _0$ 处很“尖锐”，也就是 $x(t)$ 在 $t _0$ 两侧的导数值不相等，那么 $x'(t)$ 将会成为<strong>非连续函数</strong>并出现阶跃项。若再求导，将依次出现冲击项、冲击偶项，间断阶以 $1$ 为步长不断升高……<br>&emsp;&emsp;当然了，也有一些函数不属于上面 $2$ 类中的任何一类，比如 Dirichlet 函数那样的，但这种函数无法在实际信号中实现，故不考虑这些函数。
</blockquote>

&emsp;&emsp;<strong>冲击平衡法的思想就是令微分方程中 $r(t)$ 的最高阶导数项是一个非连续函数，且其间断阶等于方程中非 $r(t)$ 的最高的间断阶，利用待定系数法求解。</strong>该思想还能用来求单位阶跃响应，单位冲击偶响应等。\
&emsp;&emsp;用一个例子来说明，有下面的微分方程：
$$i''(t)+6i'(t)+8i(t)=\delta'(t)\tag{2.9}$$

&emsp;&emsp;其中 $i(t)$ 的最高导数项是 $i''(t)$，方程中最高间断阶是 $\delta'(t)$ 的 $2$，那么就令 $i''(t)$ 的间断阶是 $2$，从而 $i''(t)$ 有下面的形式：
$$i''(t)=a\delta'(t)+b\delta(t)+c\varepsilon(t)+\xi(t)\tag{2.10}$$

&emsp;&emsp;其中 $a,b,c$ 都是待定系数，$\xi(t)$ 是连续函数，且 $t<0$ 时 $\xi(t)=0$。将 $(2.10)$ 代入 $(2.9)$ 中，**间断阶相等的非连续项一一对应**，有：
$$\begin{cases}a\delta'(t)=\delta'(t)\\\\
(b+6a)\delta(t)=0\\\\
(c+6b+8a)\varepsilon(t)=0\end{cases}\tag{2.11}$$

&emsp;&emsp;从而解得 $a=1,b=-6,c=28$。**最后使得函数在 $t=0$ 左右跳变的只有阶跃函数 $\varepsilon(t)$**，这样就有 $i''(0^+)=i''(0^-)+c=1$。根据 $(2.10)$ 还可以知道 $i'(t)$ 中含有阶跃项 $b\varepsilon(t)$，$i(t)$ 中含有阶跃项 $a\varepsilon(t)$（你可以从下面看到阶跃项不止我说的这些，我没提到的阶跃项实际上是连续函数），从而得到 $i'(0^+)=b=-6,i(0^+)=a=1$。
<blockquote>
&emsp;&emsp;在代入 $i''(t)$ 表达式得到 $(2.11)$ 式的过程中，我们省略了将连续项对应的步骤。其实连续项也是可以自洽的。为方便描述令 $\eta(t)=\displaystyle\int _{-\infty}^t\mathrm du\int _{-\infty}^u\xi(v)\mathrm dv$，从而 $\xi(t)=\eta''(t)$。考虑到 $i''(0^-)=i'(0^-)=i(0^-)=0$，有：
$$\begin{cases}i'(t)=a\delta(t)+(b+ct)\varepsilon(t)+\eta'(t)\\
i(t)=\left(a+bt+\cfrac{t^2}{2}\right)\varepsilon(t)+\eta(t)\end{cases}\tag{2.12}$$
&emsp;&emsp;把连续项拿出来是
$$\eta''(t)+6\eta'(t)+8\eta(t)=-(6ct+8bt+4t^2)\varepsilon(t)\tag{2.13}$$
&emsp;&emsp;相当于 $\eta(t)$ 是激励为 $-(6ct+8bt+4t^2)\varepsilon(t)$ 时的零状态响应，可以用微积分的常规方法求解。
</blockquote>

#### 三对响应的求解及其关系
&emsp;&emsp;这里涉及到的三对响应分别是：\
$\bigstar$&emsp;**零输入响应与零状态响应**\
&emsp;&emsp;在时域上，这两个响应都可以单独地通过系统的微分方程求得。特别地，零状态响应还可以由式 $(2.2)$ 卷积求得。\
&emsp;&emsp;从这一对响应出发，可以直接得到后两对响应。\
$\bigstar$&emsp;**自由响应与受迫响应**\
&emsp;&emsp;在时域上，这两个响应也是可以单独地通过系统的微分方程求得。特点是自由响应对应系统的特征频率，受迫响应对应非特征频率。
<blockquote>
&emsp;&emsp;自由响应、受迫响应的频率特点使得它们可以很好地从全响应中区分开来。例如给出一个系统的微分方程是 $u'(t)+u=e(t)$，全响应是 $u(t)=\left(1+\cfrac{1}{2}\mathrm e^{-t}-\cfrac{1}{2}\mathrm e^{-3t}\right)\varepsilon(t)$。可以发现系统微分方程具有特征根 $\lambda=-1$，从而全响应中任何与 $\mathrm e^{-t}\varepsilon(t)$ 线性相关的都是自由响应，非线性相关的都是受迫响应。因此不难得到自由响应 $u _h(t)=\cfrac{1}{2}\mathrm e^{-t}\varepsilon(t)$，受迫响应 $u _p(t)=\left(1-\cfrac{1}{2}\mathrm e^{-3t}\right)\varepsilon(t)$。
</blockquote>

$\bigstar$&emsp;**瞬态响应与稳态响应**\
&emsp;&emsp;这个一般通过全响应直接分析得到的。如果没有给出全响应，要通过前面的某一对响应相加得到。如其名，随时间收敛到 $0$ 的是瞬态响应，否则就是稳态响应。

&emsp;&emsp;上面提到的这些相应的关系是：
<div align="center"><img src="responce.svg" width="30%"></img></div>

## $Chapter3$&emsp;连续信号的正交分解

**一、傅里叶级数**\
&emsp;&emsp;对于真实信号**周期函数** $f(t)$ 来说，一般都可以分解为傅里叶级数：
$$f(t)=\cfrac{a _0}{2}+\sum _{n=1}^\infty(a _n\cos n\varOmega t+b _n\sin n\varOmega t)\tag{3.1}$$

<blockquote>
&emsp;&emsp;根据 Dirichlet 条件，上式中的 “$=$” 写作 “$\sim$” 更严谨，因为可能会存在一些离散的点，等式左右两边在这些点上的取值不相等。但是毕竟是个别离散的点，工程上可以直接忽略，所以直接使用了 “$=$”。
</blockquote>

&emsp;&emsp;其中，系数 $a _n,b _n$ 的求解公式是：
$$\begin{cases}\displaystyle a _n=\cfrac{2}{T}\int _{t _1}^{t _1+T}f(t)\cos n\varOmega t\mathrm dt\\\\
\displaystyle b _n=\cfrac{2}{T}\int _{t _1}^{t _1+T}f(t)\sin n\varOmega t\mathrm dt\end{cases}\tag{3.2}$$

&emsp;&emsp;其中有 $T=2\pi/\varOmega$，是函数 $f(t)$ 的周期。显然，式 $(3.2)$ 也可以使用配角公式，写作式 $(3.3)$ 所示：
$$f(t)=\cfrac{a _0}{2}+\sum _{n=1}^\infty A_n\cos(n\varOmega t+\varphi _n)\tag{3.3}$$

&emsp;&emsp;如果考虑到欧拉公式，使用复指数消去三角函数，就得到了 $f(t)$ 的**指数傅里叶级数**：
$$f(t)=\cfrac{1}{2}\sum_{n=-\infty}^{+\infty}A _n\mathrm e^{\mathrm j(n\varOmega t+\varphi _n)}=\cfrac{1}{2}\sum _{n=-\infty}^{+\infty}\dot A _n\mathrm e^{\mathrm jn\varOmega t}\tag{3.4}$$

&emsp;&emsp;其中的 $A _n$ 和 $\varphi _n$ 和 $(3.3)$ 里面是一样的。同时 $(3.4)$ 中还满足 $A _n=A _{-n},\varphi _n=-\varphi _{-n}$。有的地方使用 $F _n$ 和 $\dot F _n$，它们分别有 $F _n=A _n/2$，$\dot F _n=\dot A _n/2$。\
**二、傅里叶变换及其性质**\
**1.傅里叶变换**\
&emsp;&emsp;当周期函数的 $T$ 趋于无穷大时，这个函数就不再具备周期性，同时其傅里叶级数中 $k$ 次谐波和 $k+1$ 次谐波的频率差也趋于 $0$，离散的函数有向连续转变的趋势，级数和有向定积分转变的趋势。对比式 $(3.4)$，对于**非周期函数** $f(t)$，有：
$$f(t)=\cfrac{1}{2\pi}\int _{-\infty}^{+\infty} F(\omega)\mathrm e^{\mathrm j\omega t}\mathrm d\omega\tag{3.5}$$

<blockquote>
&emsp;&emsp;有的地方也把 $F(\omega)$ 写作 $F(\mathrm j\omega)$。为了方便，后面都记作 $F(\omega)$。
</blockquote>

&emsp;&emsp;其中“系数” $F(\omega)$ 可以通过下式求得：
$$F(\omega)=\int _{-\infty}^{+\infty}f(t)\mathrm e^{-\mathrm j\omega t}\mathrm dt\tag{3.6}$$

&emsp;&emsp;式 $(3.5)(3.6)$ 被统称为傅里叶变换式，$(3.6)$ 被称为正变换，也写作 $F(\omega)=\mathscr F\lbrace f(t)\rbrace $；$(3.5)$ 被称为反变换，也写作 $f(t)=\mathscr F^{-1}\lbrace F(\omega)\rbrace $。\
&emsp;&emsp;特别地，<st>单矩形脉冲信号 $f(t)=A[\varepsilon(-\tau/2)-\varepsilon(\tau/2)]$ 的傅里叶变换是 $F(\omega)=A\tau \mathrm{Sa}\left(\cfrac{\omega\tau}{2}\right)$</st>。其中，**抽样函数** $\mathrm{Sa}(t)=\cfrac{\sin t}{t}$。
<table width="100%">
<caption>表1 单矩形脉冲信号及其傅里叶变换</caption>
    <tr>
        <td width="50%">单矩形脉冲信号 $f(t)$</td>
        <td width="50%">单矩形脉冲信号的傅里叶变换 $F(\omega)$</td>
    </tr>
    <tr>
        <th><img src="fig1.svg"></img></th>
        <th><img src="fig2.svg"></img></th>
    </tr>
</table>

**2.傅里叶变换的性质**\
&emsp;&emsp;傅里叶变换具有的性质有：\
**线性特性**：$\mathscr F\lbrace af _1(t) +bf _2(t)\rbrace =a\mathscr F\lbrace  f _1(t)\rbrace  + b\mathscr F\lbrace  f _2(t)\rbrace $。\
**延时特性**：若 $f(t)\leftrightarrow F(\omega)$，则 $f(t-t _0)\leftrightarrow F(\omega)\mathrm e^{-\mathrm j\omega t _0}$。\
**移频特性**：若 $f(t)\leftrightarrow F(\omega)$，则 $f(t)\mathrm e^{\mathrm j\omega _ct}\leftrightarrow F(\omega-\omega _c)$。特别的，由于余弦函数可以用复指数表示，因此也存在 $f(t)\cos\omega _ct\leftrightarrow \cfrac{1}{2}[F(\omega+\omega _c)+F(\omega-\omega _c)]$。\
**对称特性**（非常有用）：若 $f(t)\leftrightarrow F(\omega)$，则 $F(t)\leftrightarrow 2\pi f(-\omega)$。

<blockquote>
&emsp;&emsp;对称特性非常适合用于求已知反变换的函数的正变换。例如，抽样函数是单矩形脉冲函数的傅里叶变换，但是直接求抽样函数的傅里叶变换会比较困难。
$$\begin{aligned}\mathscr F\lbrace \mathrm{Sa}(t)\rbrace&=\int _{-\infty}^{+\infty}\mathrm{Sa}(t)\mathrm e^{-\mathrm j\omega t}\mathrm dt\\
&=2\int _{0}^{+\infty}\cfrac{\sin t}{t}\cos(\omega t)\\
&=\int _{0}^{+\infty}\cfrac{\sin(1+\omega) t+\sin(1-\omega)t}{t}\mathrm dt\end{aligned}\tag{3.7}$$
根据狄利克雷积分：
$$\int _0^{+\infty}\cfrac{\sin x}{x}\mathrm dx=\cfrac{\pi}{2}\tag{3.8}$$
可得当 $-1< \omega< 1$ 时，$\mathscr F\lbrace\mathrm{Sa}(t)\rbrace=\pi$;当 $\omega > 1$ 或 $\omega < -1$ 时，$\mathscr F\lbrace\mathrm{Sa}(t)\rbrace=0$。即 $\mathscr F\lbrace\mathrm{Sa}(t)\rbrace\leftrightarrow \pi[\varepsilon(\omega+1)-\varepsilon(\omega-1)]$。<br>
&emsp;&emsp;显然用对称特性会比直接计算快一些：令 $A=\cfrac{1}{2}$ 和 $\tau=2$，那么有：
$$\cfrac{1}{2}[\varepsilon(t+1)-\varepsilon(t-1)]\leftrightarrow \mathrm{Sa}(\omega)\tag{3.8}$$
根据对称特性有：
$$\mathrm{Sa}(t)\leftrightarrow \pi[\varepsilon(-\omega+1)-\varepsilon(-\omega-1)]\tag{3.9}$$
式 $(3.9)$ 和用狄利克雷积分获得的结果是一样的。
</blockquote>

**微分特性**：分为时域上的微分和频域上的微分。若 $f(t)\leftrightarrow F(\omega)$，则有 $\cfrac{\mathrm d^nf(t)}{\mathrm dt^n}\leftrightarrow (\mathrm j\omega)^nF(\omega)$ 和 $(-\mathrm jt)^nf(t)\leftrightarrow \cfrac{\mathrm d^nF(\omega)}{\mathrm dt^n}$。\
**积分特性**：分为时域上的积分和频域上的积分。若 $f(t)\leftrightarrow F(\omega)$，且不考虑 $t=0,\omega=0$ 时 $f(t),F(\omega)$ 的取值，则有 $\displaystyle\int _{-\infty}^t f(\tau)\mathrm d\tau\leftrightarrow \cfrac{1}{\mathrm j\omega}F(\omega)$ 和 $\displaystyle\cfrac{1}{-\mathrm jt}f(t)\leftrightarrow\int _{-\infty}^\omega F(\varOmega)\mathrm d\varOmega$。需要注意的是式中的积分都应该收敛。\
**卷积特性**（非常重要）：\
&emsp;&emsp;**特性一**：两个信号的卷积的傅里叶变换是它们分别傅里叶变换的乘积：$f _1(t) * f _2(t)\leftrightarrow \mathscr F\lbrace f _1(t)\rbrace\mathscr F\lbrace f _2(t)\rbrace$。\
&emsp;&emsp;**特性二**：两个信号的乘积的傅里叶变换是它们分别傅里叶变换的卷积的 $\cfrac{1}{2\pi}$：$f _1(t)f _2(t)\leftrightarrow \cfrac{1}{2\pi}\mathscr F\lbrace f _1(t)\rbrace * \mathscr F\lbrace f _2(t)\rbrace$。这一结论可以由特性一和对称特性导出。
<blockquote>
&emsp;&emsp;下面给出由特性一和对称特性导出特性二的过程。不妨记 $\mathscr F\lbrace g _1(t)\rbrace=G _1(\omega)$，$\mathscr F\lbrace g _2(t)\rbrace=G _2(\omega)$。由特性一，有 $g _1(t) * g _2(t)\leftrightarrow G _1(\omega)G _2(\omega)$。因此得到三个傅里叶变换关系：
$$\begin{cases}g _1(t)\leftrightarrow G _1(\omega)\\
g _2(t)\leftrightarrow G _2(\omega)\\
g _1(t) * g _2(t)\leftrightarrow G _1(\omega)G _2(\omega)\end{cases}\tag{3.10}$$
根据<strong>对称特性</strong>，有：
$$\begin{cases}G _1(t)\leftrightarrow 2\pi g _1(-\omega)\\
G _2(t)\leftrightarrow 2\pi g _2(-\omega)\\
G _1(t)G _2(t)\leftrightarrow 2\pi g _1(-\omega) * g _2(-\omega)\end{cases}\tag{3.11}$$
由 $(3.11)$ 前两式可得 $\mathscr F\lbrace G _1(t)\rbrace=2\pi g _1(-\omega)$，$\mathscr F\lbrace G _2(t)\rbrace=2\pi g _2(-\omega)$。代入第三式即得：
$$G _1(t)G _2(t)\leftrightarrow \cfrac{1}{2\pi}\mathscr F\lbrace G _1(t)\rbrace * \mathscr F\lbrace G _2(t)\rbrace\tag{3.12}$$
</blockquote>

## $Chapter4$&emsp;连续时间系统的频域分析
&emsp;&emsp;这一章是运用**傅里叶变换**将信号在时域上的分析转移到**频域**。相比于**拉普拉斯变换**，傅里叶变换<st>只能求解系统的零状态响应</st>。
<blockquote>
&emsp;&emsp;通过对傅里叶变换只能求解系统的零状态响应，说明它无法考虑系统的初值条件。一个很关键的原因就是，很多激励函数的傅里叶变换都是不存在的；另一个关键原因就是傅里叶变换考虑了 $t < 0$ 的时间域。式 $(3.6)$ 中我们可以感性地看到，当 $t\rightarrow -\infty$ 时，复变量 $\mathrm e^{-\mathrm j\omega t}$ 会不停地在复平面旋转；如果 $f(t)$ 是实信号，只有 $\lim\limits _{t\rightarrow -\infty}f(t)=0$，反常积分才可能收敛，傅里叶变换 $F(\omega)$ 才有可能存在。<br>
&emsp;&emsp;由于我们在频域求解时，对 $r(t)$ 进行了傅里叶变换，其前提就是傅里叶变换存在，因而有 $\lim\limits _{t\rightarrow -\infty}r(t)=0$，即系统无初始储能。<br>
&emsp;&emsp;基于相同的原因，双边拉普拉斯变换应该也存在只能求解零状态响应的问题；但是单边拉普拉斯变换因为积分下限是 $0$，$\mathrm e^{-st}$ 中的 $s$ 就不会跑到负无穷那边去，因而不需要条件 $\lim\limits _{t\rightarrow -\infty}f(t)=0$。
</blockquote>

**一、频率分析方法**\
**1.频率响应函数**\
&emsp;&emsp;频率响应函数 $H(\omega)$ 描述了系统对特定频率的激励的响应特征。一方面，根据系统 $r(t)$ 与 $e(t)$ 的微分方程，经过傅里叶变换后得到频域的方程，从而**定义**频率响应函数：
$$H(\omega)=\cfrac{R(\omega)}{E(\omega)}\tag{4.1}$$

&emsp;&emsp;若已知 $E(\omega)$，可以直接与频响函数相乘得 $R(\omega)$。另一方面，根据 $(2.2)$ 的卷积式也能得到 $R(\omega)=H(\omega)E(\omega)$，从而发现**频响函数是冲激响应的傅里叶变换**，即 $h(t)\leftrightarrow H(\omega)$。\
**2.利用频响函数进行频域分析**\
&emsp;&emsp;对于给定的激励信号 $e(t)$，可以按照下面的步骤，在频域求响应 $r(t)$：\
(1) 对 $e(t)$ 傅里叶变换得 $E(\omega)$。\
(2) 设法得到频响函数 $H(\omega)$，求 $R(\omega)=H(\omega)E(\omega)$。\
(3) 对 $R(\omega)$ 反变换得 $r(t)$。\
&emsp;&emsp;上面的方法都是要用傅里叶变换的，一般都是用上面的方法。但是如果遇到了**周期信号**，特别是正弦信号，可以不用傅里叶变换就求出系统的响应；这其实就是电路理论里面的相量法解正弦稳态电路。这种方法的核心思想就是：若 $e(t)=A\cos(\omega t+\varphi)$，则 $r(t)=A|H(\omega)|\cos(wt+\varphi+\varphi(\omega))$。其中 $H(\omega)=|H(\omega)|\varphi(\omega)$。
<blockquote>
&emsp;&emsp;对此书上有一个例子。我们仍然用 $\dot E=E\angle\varphi$（相量）记 $E\mathrm e^{\mathrm j(\omega t+\varphi)}$，对于 $H(\omega)$ 就记成 $|H(\omega)|\angle\varphi(\omega)$。当激励为 $e(t)=2+2\cos t+2\cos 2t$ 时，将其分成三个相量 $\dot E _0=2$，$\dot E _1=2\angle 0^\circ$，$\dot E _2=2\angle 0^\circ$。如果通过一些别的手段能够得到 $H(0)=2\angle 0^\circ$，$H(1)=1\angle-\mathrm j90^\circ$，$H(2)=0\angle 0^\circ$，就能够分别得到 $\dot R _0=4\angle 0^\circ$，$\dot R _1=2\angle -\mathrm j90^\circ$，$\dot R _2=0\angle 0^\circ$。转换成时域并合并，就有 $r(t)=4+2\cos\left(t-\cfrac{\pi}{2}\right)=4+2\sin t$。
</blockquote>

**二、理想低通滤波器的冲激响应与阶跃响应**\
&emsp;&emsp;归一化理想低筒滤波器的频响函数 $H(\omega)$ 满足 $|H(\omega)|=\varepsilon(t+\omega _{c0})-\varepsilon(t-\omega _{c0})$，$\varphi(\omega)=-\omega t _0$。它禁止一切频率高于 $\omega _{c0}$ 的分量通过，对于频率小于 $\omega _{c0}$ 的分量，会延时 $t _0$ 时间。这非常符合人们对理想滤波器的构想，既实现了滤波，又考虑了物理上不可忽略的延时因素。\
&emsp;&emsp;通过对这个频响函数进行分析，即傅里叶反变换，我们可以求出单位冲击响应 $h(t)$，也可以用其他方法求出单位阶跃响应。两个响应的图像都很符合我们的预期，但是并不完全符合，因为图象总是会有抖动。同时，我们发现能够确定 $t<0$ 对应响应的值，而冲激响应只在 $t=0$ 作用，阶跃响应只在 $t>0$ 作用，因而理想滤波器**不满足因果律**，是不可实现的。

## $Chapter5$&emsp;连续时间系统的复频域分析
**一、拉普拉斯变换**\
&emsp;&emsp;拉普拉斯变换通过引入一个**收敛因子** $\mathrm e^{-\sigma t}$，使得对于那些没有傅里叶变换的信号 $f(t)$ 而言，$f(t)\mathrm e^{-\sigma t}$ 有傅里叶变换。对后者的傅里叶变换就是对 $f(t)$ 的拉普拉斯变换。**双边**拉普拉斯变换为：
$$F(s)=\int _{-\infty}^{+\infty}f(t)\mathrm e^{-st}\mathrm dt\tag{5.1}$$

反变换为：
$$f(t)=\cfrac{1}{2\pi\mathrm j}\int _{\sigma-\mathrm j\infty}^{\sigma+\mathrm j\infty}F(s)\mathrm e^{st}\mathrm ds\tag{5.2}$$

<blockquote>
&emsp;&emsp;实际上，并不是对于所有信号 $f(t)$，总存在 $\sigma$ 使其收敛，例如一些比指数增长还快的信号 $f(t)=\mathrm e^{t^2}$。但是这种信号在工程运用中是不会碰到的，可以认为所有实际出现的信号的阶都不会高于指数。
</blockquote>

&emsp;&emsp;实际上，我们一般只用到**单边**拉普拉斯变换：
$$\begin{cases}F(s)=\displaystyle\int _0^{+\infty}f(t)\mathrm e^{-st}\mathrm dt\\\\
f(t)=\displaystyle\left[\cfrac{1}{2\pi\mathrm j}\int _{\sigma-\mathrm j\infty}^{\sigma+\mathrm j\infty}F(s)\mathrm e^{st}\mathrm ds\right]\varepsilon(t)\end{cases}\tag{5.3}$$

<table align="center">
<caption>表2 常见函数的拉普拉斯变换</caption>
<tr>
    <th>公式编号</th>
    <th>$f(t)$</th>
    <th>$F(s)$</th>
</tr>
<tr>
    <td>$1$</td>
    <td>$\delta(t)$</td>
    <td>$1$</td>
</tr>
<tr>
    <td>$2$</td>
    <td>$\varepsilon(t)$</td>
    <td>$\cfrac{1}{s}$</td>
</tr>
<tr>
    <td>$3$</td>
    <td>$t\varepsilon(t)$</td>
    <td>$\cfrac{1}{s^2}$</td>
</tr>
<tr>
    <td>$4$</td>
    <td>$t^n\varepsilon(t)$</td>
    <td>$\cfrac{n!}{s^{n+1}}$</td>
</tr>
<tr>
    <td>$5$</td>
    <td>$\mathrm e^{\alpha t}\varepsilon(t)$</td>
    <td>$\cfrac{1}{s-\alpha}$</td>
</tr>
<tr>
    <td>$6$</td>
    <td>$t\mathrm e^{\alpha t}\varepsilon(t)$</td>
    <td>$\cfrac{1}{(s-\alpha)^2}$</td>
</tr>
<tr>
    <td>$7$</td>
    <td>$t^n\mathrm e^{\alpha t}\varepsilon(t)$</td>
    <td>$\cfrac{n!}{(s-\alpha)^{n+1}}$</td>
</tr>
<tr>
    <td>$8$</td>
    <td>$\sin(\omega t)\varepsilon(t)$</td>
    <td>$\cfrac{\omega}{s^2+\omega^2}$</td>
</tr>
<tr>
    <td>$9$</td>
    <td>$\cos(\omega t)\varepsilon(t)$</td>
    <td>$\cfrac{s}{s^2+\omega^2}$</td>
</tr>
<tr>
    <td>$10$</td>
    <td>$\mathrm e^{\alpha t}\sin(\omega t)\varepsilon(t)$</td>
    <td>$\cfrac{\omega}{(s-\alpha)^2+\omega^2}$</td>
</tr>
<tr>
    <td>$11$</td>
    <td>$\mathrm e^{\alpha t}\cos(\omega t)\varepsilon(t)$</td>
    <td>$\cfrac{s-\alpha}{(s-\alpha)^2+\omega^2}$</td>
</tr>
</table>

**二、拉普拉斯反变换的求解**\
&emsp;&emsp;从积分上下限 $\sigma\pm\mathrm j\omega$ 来看，拉普拉斯反变换不像傅里叶反变换一样，它直接求不是很好算。除了复变中的方法之外，要求 $F(s)$ 的原函数，只能通过将 $F(s)$ 拆解成一些简单项的和，利用拉普拉斯变换的线性性，逐项对照上表求反变换。
<blockquote>
&emsp;&emsp;例如，$F(s)=\cfrac{1+s}{s^2}$，求其反变换可以对照上表的第 $2,3$ 项：
$$f(t)=\mathscr L^{-1}\left\lbrace\cfrac{1+s}{s^2}\right\rbrace=\mathscr L^{-1}\left\lbrace\cfrac{1}{s^2}\right\rbrace+\mathscr L^{-1}\left\lbrace\cfrac{1}{s}\right\rbrace=(1+t)\varepsilon(t)\tag{5.4}$$ 
</blockquote>

**三、拉普拉斯变换的性质**\
&emsp;&emsp;拉普拉斯变换是通过傅里叶变换得到的，所以很多性质都可以参考傅里叶变换。应用于连续时间系统的分析，拉普拉斯主要有两个性质和傅里叶变换中稍有区别：\
**1.时域微分性质**\
&emsp;&emsp;时域微分能够计入初始值，这是单边傅里叶变换 $(5.3)$ 的特性决定的：
$$\mathscr L\left\lbrace\cfrac{\mathrm d^nf(t)}{\mathrm dt}\right\rbrace=s^nF(s)-s^{n-1}f(0^-)-s^{n-1}f ' (0^-)-\cdots-f^{(n-1)}(0^-)\tag{5.5}$$

&emsp;&emsp;$n$ 阶微分需要 $n$ 个初始值。因此已知初始值，可以用拉普拉斯变换来求系统的全响应。\
**2.时域积分性质**\
&emsp;&emsp;一般拉普拉斯变换处理的都是 $t=0$ 开始的有始信号 $f(t)$，因而 $t<0^-$ 时 $f(t)=0$。对于这样的 $f(t)$，满足下面的积分性质：
$$\mathscr L\left\lbrace\int _{-\infty}^tf(\tau)\mathrm d\tau\right\rbrace=\cfrac{F(s)}{s}\tag{5.6}$$

## $Chapter6$&emsp;连续时间系统的系统函数
&emsp;&emsp;这一章主要涉及到系统函数的**极零图**和系统**稳定性**。系统函数 $H(s)=\cfrac{N(s)}{D(s)}$，使得 $N(s)=0$ 的根称为**零点**，使得 $D(s)=0$ 的根称为**极点**。将极点（用×）和零点（用○）在复平面（对拉普拉斯变换而言应该说 $s$ 平面更合适）中标出来，就得到系统的极零图。\
&emsp;&emsp;系统的稳定性指的是一个系统在激励函数有界时，响应函数也有界。从**零输入响应**上来看，系统一开始有初始储能，将按照系统的固有频率进行响应。极点就反映了这种固有频率，$D(s)$ 一个 $s=\sigma+\mathrm j\omega$ 的单根就对应了零输入响应中的一个分量 $\mathrm e^{\sigma t}(C _1\sin \omega t+C _2\cos \omega t)\varepsilon(t)$。要保证这些零输入响应的分量都是有界的，即 $\sigma\leq 0$。对于多重根，响应分量前面会多出 $t^k$ 因子，所以需要 $\sigma < 0$。\
&emsp;&emsp;从**零状态响应**上来看，系统稳定与系统的冲激响应 $h(t)$ 绝对可积是等价的。
$$\int _{-\infty}^{+\infty}|h(\tau)|<\infty\tag{6.1}$$

&emsp;&emsp;与数学中不同的一点是，这里的绝对可积貌似并不要求积分存在。这也就是说，$h(t)=\sin t+2\cos t$ 这样的冲激响应也被认为是绝对可积的。\
&emsp;&emsp;无论是从**零输入响应**还是**零状态响应**来看，两者的结果是可以相互转换的。冲激响应在 $0^-$ 时间系统中属于零状态响应，在 $0^+$ 时间系统中就属于零输入响应。$h(t)$ 是否绝对可积，就看它在 $0^+$ 时间系统的自由响应是否是有界的。
<blockquote>
&emsp;&emsp;有界并不等同于绝对可积，比如 $h(t)=\arctan t\varepsilon(t)$ 这样的响应。但是我们在求解响应的时候一般只能得到 $\mathrm e^{\sigma t}(C _1\sin \omega t+C _2\cos \omega t)\varepsilon(t)$ 这种形式的结果，这种结果有界和绝对可积是等价的。
</blockquote>

## $Chapter 7$&emsp;离散时间系统的时域分析

$\boxed{\mathrm{To\ Be\ Continued}}$