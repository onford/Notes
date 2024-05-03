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


$\boxed{\mathrm{To\ Be\ Continued}}$