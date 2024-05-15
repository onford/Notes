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
    code {
	font-size: 16px;
	line-height: 30px;
	background-color: #ebeaea;
	padding-left: 0.25em;
	padding-right: 0.25em;
	padding-top: 0.15em;
	padding-bottom: 0.15em;
	border-radius: 3px;
}
</style>

# 信号与线性系统

<bw>wr按：\
《信号与线性系统》这门课全程依赖电路知识，以《电路理论》初级篇为先导，其内容相当于电路理论中部分内容的详细拓展。这一篇笔记会记录我自己的一些观点和看法（专门记我看不懂的）。</bw>

## $Chater1$&emsp;绪论
&emsp;&emsp;一个系统存在着激励 $e(t)$ 和响应 $r(t)$。\
**一、系统具有的性质**\
**线性性**：一个系统具备线性性，其抽象表述为：若 $e(t)\rightarrow r(t)$，则 $k _1e _1(t)+k _2e _2(t)\rightarrow k _1r _1(t) +k _2r _2(t)$。\
**非时变性**：一个系统具备非时变性（时不变性），其抽象表述为：若 $e(t)\rightarrow r(t)$，则 $e(t-t _0)\rightarrow r(t-t _0)$。\
**因果性**：一个系统在 $t$ 时刻的响应，只和 $t$ 时刻及其之前的时刻的激励有关。

&emsp;&emsp;上面的三个性质中，因果性是最好判定的。只需看 $r(t)$ 的表达式即可。线性性也是好判定的，直接根据抽象定义，构造两个激励 $e _1(t)$ 和 $e _2(t)$ 并判断是否具有该性质即可。\
&emsp;&emsp;关于时不变性的判定，可以构造两个激励 $e _1(t)$ 和 $e _2(t)$，其中 $e _2(t)$ 是 $e _1(t)$ 平移得到的，从而转化为判定：若 $e _1(t)\rightarrow r _1(t)$，是否有 $e _2(t)\rightarrow r _2(t)$。
<blockquote>
&emsp;&emsp;关于时不变性的判定，举个例子：$r(t)=e(1-t)$。这是在习题中碰到的。这个系统是不具备时不变性的，可以按照下面的方式判定：<br>
&emsp;&emsp;记 $e _1(t)\rightarrow e _1(1-t) = r _1(t)$，$e _2(t)=e _1(t-t _0)$。那么 $r _2(t)=e _2(1-t)=e _1(1-t-t _0)=r _1(t+t _0)\neq r _1(t-t _0)$。因此，若 $e(t)\rightarrow r(t)$，无法得到 $e(t-t _0)\rightarrow r(t-t _0)$。<br>
&emsp;&emsp;之所以单独强调时不变性，是因为产生过一个莫名其妙的错误做法：<br>
&emsp;&emsp;将原式中的 $t$ 换成 $t-t _0$ 可得 $r(t-t _0)=e(1-t+t _0)$，记作式 $(1)$。所以对于一个激励 $e(t-t _0)$，根据原式，它产生的响应应该是 $e(1-t+t _0)$，也即 $r(t-t _0)$。所以系统具备时不变性。<br>
&emsp;&emsp;这种错误做法看起来有点像是循环论证，但是它却能够正确地判断 $r(t)=\varepsilon(t)e(t)$ 不具备时不变性。所以花了一个下午的时间总结出时不变性的正确判定方法，并且特意强调，以免以后再落入这个陷阱。
</blockquote>

**二、各种各样的响应**\
**1.古典法**\
&emsp;&emsp;古典法依据微分方程的数学解形式来定义系统的不同响应。一个 $n$ 阶线性系统的微分方程可以用下面的式子来表示：
$$\cfrac{\mathrm d^nr}{\mathrm dt^n}+a _{n-1}\cfrac{\mathrm d^{n-1}r}{\mathrm dt^{n-1}}+\cdots+a _1\cfrac{\mathrm dr}{\mathrm dt}+a _0r=b _m\cfrac{\mathrm d^me}{\mathrm dt^m}+b _{m-1}\cfrac{\mathrm d^{m-1}e}{\mathrm dt^{m-1}}+b _1\cfrac{\mathrm de}{\mathrm dt}+b _0e\tag{1.1}$$

&emsp;&emsp;这个微分方程对应的齐次方程的通解（通过初值条件确定待定系数），被称作系统的**自然响应（自由响应）**，记作 $r _h(t)$。微分方程对应的特解（也通过初值条件确定了待定系数）被称作系统的**受迫响应**，记作 $r _p(t)$。\
**2.近代时域分析法**\
&emsp;&emsp;近代的时域分析法就把响应分为**零输入响应** $r _{zi}(t)$ 和**零状态响应** $r _{zs}(t)$。这一点同电路理论中的概念。

&emsp;&emsp;这些响应与全响应 $r(t)$ 之间的关系是：
$$r _h(t)=r _{zi}(t)+r _{zs}(t)=r _h(t)+r _p(t)\tag{1.2}$$

## $Chapter2$&emsp;连续时间系统的时域分析
**一、卷积积分**\
&emsp;&emsp;这一章首先证明了下面的公式：
$$f(t)=\int _0^tf(\tau)\delta(t-\tau)\mathrm d\tau=\int _{-\infty}^{+\infty}f(\tau)\delta(t-\tau)\mathrm d\tau\tag{2.1}$$

&emsp;&emsp;这说明一个信号可以分解成多个多个冲击性信号的积分。\
&emsp;&emsp;记一个系统的单位冲击响应为 $h(t)$ ，即 $\delta(t)\rightarrow h(t)$。由于线性系统的时不变性、齐次性和叠加性，可得 $\displaystyle\int _0^te(t)\delta(t-\tau)\mathrm d\tau\rightarrow \int _0^te(t)h(t-\tau)\mathrm d\tau$。\
&emsp;&emsp;因此，激励 $e(t)$ 时，系统的响应为
$$r(t) = \int _0^te(t)h(t-\tau)\mathrm d\tau\tag{2.2}$$

&emsp;&emsp;式 $(2.2)$ 就是**卷积积分**。

<blockquote>
&emsp;&emsp;<strong>冲激响应</strong>是激励为 $\delta(t)$ 的<strong>零状态响应</strong>。如果可以知道一个系统的单位冲击响应 $h(t)$，根据式 $(2.2)$ 可以直接从激励得到响应，而不需要知道系统的其它细节。
</blockquote>

**二、卷积的性质**\
&emsp;&emsp;卷积运算是一种抽象出来的运算，它的定义是：
$$f(t) * g(t)=\int_{-\infty}^{+\infty}f(\tau)g(t-\tau)\mathrm d\tau\tag{2.3}$$

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

&emsp;&emsp;上式还能互换 $u(t),v(t)$ 的地位，这里略去不写。式 $(2.6)$ 的使用条件是 $\displaystyle\int_{-\infty}^tv(x)\mathrm dx$ 存在，且<st> $\lim\limits_{x\rightarrow -\infty}u(t) * v(t)=0$</st>。
<blockquote>
&emsp;&emsp;这是因为式 $(2.6)$ 可以看作是对式子 $u(t) * v(t)=u(t) * v(t)$ 两边分别运用 $(2.4)(2.5)$ 得到的，只不过等号右边选择了不同的函数进行操作。需要注意的是，左边在进行微分、积分后要能够得到原来的式子。如果先进行微分，那么：
$$\int_{-\infty}^t\cfrac{\mathrm d[u(x) * v(x)]}{\mathrm dx}\mathrm dt=u(t) * v(t)-u(-\infty) * v(-\infty)\tag{2.7}$$
&emsp;&emsp;显然只有满足 $\lim\limits_{x\rightarrow -\infty}u(t) * v(t)=0$，左边才能复原。如果先进行积分，那么首先就要保证 $\displaystyle\int_{-\infty}^t[u(x) * v(x)]\mathrm dx$ 存在，显然也需要满足 $\lim\limits_{x\rightarrow -\infty}u(t) * v(t)=0$，否则反常积分不收敛。<br>
&emsp;&emsp;同时，有的地方说 $(2.6)$ 成立的条件是 $u(t)=\displaystyle\int_{-\infty}^tu'(x)\mathrm dx$，也就是 $\lim\limits_{x\rightarrow -\infty}u(x)=0$，这个条件是不准确的，至少其必要性不成立。<br>
&emsp;&emsp;考虑 $u(t)=1+\varepsilon(t),v(t)=\left[\mathrm e^{-t}-\cfrac{1}{(t+1)^2}\right]\varepsilon(t)$，虽然不满足 $\lim\limits_{x\rightarrow -\infty}u(x)=0$，但是依然可以使用 $(2.6)$ 式：
$$u(t) * v(t)=\delta(t) * \int_{-\infty}^t\left[\mathrm e^{-x}-\cfrac{1}{(x+1)^2}\right]\varepsilon(x)\mathrm dx=\varepsilon(t)\int_0^t\left[\mathrm e^{-x}-\cfrac{1}{(x+1)^2}\right]\mathrm dx=\left(\cfrac{1}{t+1}-\mathrm e^{-t}\right)\varepsilon(t)\tag{2.8}$$
</blockquote>

&emsp;&emsp;除此之外，还有一个延时的性质：若 $f(t)=f _1(t) * f _2(t)$，则有 $f(t-t _1-t _2)=f _1(t-t _1) * f _2(t-t _2)$。

## $Chapter3$&emsp;连续信号的正交分解
**一、傅里叶级数**\
&emsp;&emsp;对于真实信号函数 $f(t)$ 来说，一般都可以分解为傅里叶级数：
$$f(t)=\cfrac{a _0}{2}+\sum _{n=1}^\infty(a _n\cos n\varOmega t+b _n\sin n\varOmega t)\tag{3.1}$$

<blockquote>
&emsp;&emsp;根据 Dirichlet 条件，上式中的 “$=$” 写作 “$\sim$” 更严谨，因为可能会存在一些离散的点，等式左右两边在这些点上的取值不相等。但是毕竟是个别离散的点，工程上可以直接忽略，所以直接使用了 “$=$”。
</blockquote>

&emsp;&emsp;其中，系数 $a _n,b _n$ 的求解公式是：
$$\begin{cases}\displaystyle a _n=\cfrac{2}{T}\int _{t _1}^{t _1+T}f(t)\cos n\varOmega t\mathrm dt\\\\
\displaystyle b _n=\cfrac{2}{T}\int _{t _1}^{t _1+T}f(t)\sin n\varOmega t\mathrm dt\end{cases}\tag{3.2}$$

&emsp;&emsp;其中有 $T=2\pi/\varOmega$。显然，式 $(3.2)$ 也可以使用配角公式，写作式 $(3.3)$ 所示：
$$f(t)=\cfrac{a _0}{2}+\sum _{n=1}^\infty A_n\cos(n\varOmega t+\varphi _n)\tag{3.3}$$

&emsp;&emsp;如果考虑到欧拉公式，使用复指数消去三角函数，就得到了 $f(t)$ 的**指数傅里叶级数**：
$$f(t)=\cfrac{1}{2}\sum_{n=-\infty}^{+\infty}A _n\mathrm e^{\mathrm j(n\varOmega t+\varphi _n)}=\cfrac{1}{2}\sum _{n=-\infty}^{+\infty}\dot A _n\mathrm e^{\mathrm jn\varOmega t}\tag{3.4}$$

&emsp;&emsp;其中的 $A _n$ 和 $\varphi _n$ 和 $(3.3)$ 里面是一样的。同时 $(3.4)$ 中还满足 $A _n=A _{-n},\varphi _n=-\varphi _{-n}$。有的地方使用 $F _n$ 和 $\dot F _n$，它们分别有 $F _n=A _n/2$，$\dot F _n=\dot A _n/2$。

$\boxed{\mathrm{To\ Be\ Continued}}$