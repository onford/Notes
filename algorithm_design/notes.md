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

# **算法设计与分析笔记** 
<bw>wr按：\
算法是计算机专业的重要核心课。这门课使用的教材是第三版算法导论黑皮书，由于课程并没有涉及到书中全部的张杰，笔记只是对其中少数几个部分的理解。\
附：☞<a href="https://walkccc.me/CLRS/" target="new"><font color="orange">算法导论第三版参考答案（English Ver.）</font></a>\
~~这个答案对于很多题目都没有给出完整回答，参考一下就好~~</bw>

## $Part1$ &emsp;分治策略
&emsp;&emsp;主方法用来求解递归式，获得一些<st>渐进紧确界</st>：\
&emsp;&emsp;**主定理**&emsp;令$a\geq 1$和$b > 1$是常数，$f(n)$是一个函数，$T(n)$是定义在非负整数上的递归式
$$T(n)=aT(n/b)+f(n)\tag{1.1}$$

&emsp;&emsp;其中我们将$n/b$解释为$\lfloor n/b\rfloor$或$\lceil n/b\rceil$.那么：\
&emsp;&emsp;1.若对于某个常数$\varepsilon > 0$有$f(n)=O(n^{\log _b a-\varepsilon})$，则$ T(n)=\Theta(n^{\log _b a})$.\
&emsp;&emsp;2.若$f(n)=\Theta(n^{\log _ ba})$，则$T(n)=(n^{\log _ ba}\lg n)$.\
&emsp;&emsp;3.若对于某个常数$\varepsilon > 0$有$f(n)=\Omega(n^{\log _b a+\varepsilon})$，且对于某个常数$c < 1$和足够大的$n$有$af(n/b)\leq cf(n)$，则$T(n)=\Theta(f(n))$.

## $Part2$&emsp;动态规划与贪心算法
&emsp;&emsp;动态规划的两个核心：**最优子结构性**的证明，**状态转移方程**的建立。动态规划运行的核心是**最优子结构性**，证明了这个底层逻辑，动态规划算法就是正确的。
<blockquote>
&emsp;&emsp;实际上，课程所讲述的动态规划全部属于<strong>区间DP</strong>，动态规划还有树形DP、状态压缩DP、期望DP等各种各样的形式。使用动态规划算法解决的经典问题：<br>
&emsp;&emsp;一维DP：钢条切割问题。<br>
&emsp;&emsp;二维DP：矩阵链乘法问题、最长公共子序列（LCS，Longest Common Subsequence）问题，最优二叉搜索树问题，0-1背包问题。<br>
&emsp;&emsp;DP维度，就是开辟的DP数组的维数。可能要使用三维DP的问题：<a href="http://poj.org/problem?id=1185" target="new"><font color="orange">POJ 1185</font></a>。关于这一方面的内容，在这里部署一个<a href="https://blog.csdn.net/weixin_72137075/category_12581277.html" target="new"><font color="orange">动态规划学习</font></a>。
</blockquote>

&emsp;&emsp;贪心算法，在某种程度上可以看做是动态规划的一个特例。动态规划更偏向于穷举，每条路都试一下；贪心算法则是绕开了这种穷举，抄一条近路直接到达目的地，所以很多情况下并不能保证最优解。\
&emsp;&emsp;贪心算法运行的核心是**贪心选择性质**——可以通过做出局部最优解（贪心）来构造全局最优解。只要你证明了这个底层逻辑，贪心算法的正确性一般就能够保证。

<blockquote>
&emsp;&emsp;Huffman树的生成原理，使用了贪心算法：每次调两个最小的结点合并，直到只剩下一个节点，它就是Huffman树的根节点。<br>
&emsp;&emsp;图论中也有很多算法的底层逻辑是贪心算法。比如最小生成树的Prim算法和Kruskal算法，单源最短路径的Dijkstra算法。
</blockquote>

## $Part3$&emsp;基本图算法
**一、最小生成树**\
&emsp;&emsp;最小生成树的概念，是针对于无向连通图的。有两个贪心算法：\
&emsp;&emsp;**Prim算法**：从一个源点$S$开始。在不形成环的情况下，每次选择连接$S$所在的连通分支的边中，权重最小的那个。直到只剩下一个连通分支。\
&emsp;&emsp;**Kruskal算法**：在不形成环的情况下，从所有的边中选择权重最小的，直到只剩下一个连通分支。\
**二、单源最短路径**\
&emsp;&emsp;**Bellman-Ford算法**：如果图$G$有$n$个节点，在初始化之后，执行$n-1$轮松弛。每轮松弛都是按照特定的顺序松弛$G$中所有的边。根据操作后结点的$d$值是否满足三角不等式，返回bool值，代表该图中最短路径是否能够定义。
<blockquote>
&emsp;&emsp;初始化操作（后面的Dijkstra也是）：对所有的结点$v\in V$，置$v.d=\infty\ \mathrm{and}\ v.\pi=\mathrm{NIL}$.然后置$s.d=0$，其中$s$是源节点。<br>
&emsp;&emsp;Bellman-Ford返回的bool值，也代表“图$G$中是否含有可以由$s$到达的负权重回路”。一旦返回True，那么对于所有的结点$v\in V$，都有$\delta(s,v)=v.d$.<br>
&emsp;&emsp;在手动运行Bellman-Ford算法的时候，有两种松弛方式：<br>
&emsp;&emsp;（1）用每轮松弛操作前的$d$值进行松弛，是一种“并行松弛”。每轮松弛后的结果与边松弛的先后顺序无关，我们可以按照任意的顺序对这些边进行松弛。<br>
&emsp;&emsp;（2）每次松弛时采用最新的$d$值，是一种“串行松弛”。这个依赖于每条边的松弛顺序，也就是说，松弛顺序不同，一轮松弛得到的结果也会有区别。<br>
&emsp;&emsp;比如我在第一次松弛的时候，得到了$u.d=6$，$v.d=7$，图中有$w(u,v)=3$.在进行第二轮松弛的时候，$(u,v)$被松弛之前，先更新了$u.d =2$.如果是采取松弛方式（2），在后续对$(u,v)$进行松弛的时候，$v.d$会被更新为$2+3=5$；如果是采取松弛方式（1），在后续对$(u,v)$进行松弛的时候，使用的$u.d$仍然是第一轮松弛得到的$6$，所以$v.d$不会改变。<br>
&emsp;&emsp;Bellman-Ford实际的运行方式是松弛方式（2），但不理解有的题目要我们用方式（1）。不过，虽然方式（2）每轮松弛的结果依赖边松弛的顺序，但是在算法返回True的情况下，最终的结果和这个松弛顺序是无关的——最终$v.d$都会收敛到$\delta(s,v)$.
</blockquote>

&emsp;&emsp;算法的优点是<st>可以处理含有负权重边的图</st>，缺点是时间复杂度$O(VE)$有点大。简单图的边数$E$可以达到$O(V^2)$的规模，这个时候Bellman-Ford算法的时间复杂度就是$O(n^3)$.\
&emsp;&emsp;**Dijkstra算法**：维持一个集合$S$.在初始化之后，不断重复这样的操作：\
&emsp;&emsp;1.对于不在$S$中的结点，找到$d$值最小的那个$v$加入$S$.\
&emsp;&emsp;2.松弛所有从$v$发出的边。\
&emsp;&emsp;最后，所有的结点都会进入$S$.此时算法终止。Dijkstra算法在时间复杂度上优于Bellman-Ford算法， 不经优化就能达到$O(n^2)$的复杂度，但是<st>不能处理含有负权重边的图</st>。\
&emsp;&emsp;**SPFA算法**：维持一个队列$Q$，初始时有且只有源节点$s$.重复这样的操作：每次从$Q$中出队队首节点$v$，松弛所有从$v$发出的边，在松弛中$d$值改变的结点都入队。直到$Q$空时，算法终止。它的优点是<st>可以处理含有负权重边的图</st>，并且时间复杂度也显著优于Bellman-Ford算法。但是貌似泛用性不强，容易被卡。\
**三、多源最短路径**\
&emsp;&emsp;有一种自然的想法，对从$u$到$v$的路径长度$l$进行动态规划：求出所有节点对在路径长度不大于$l=l _ 0$时的最短路径，就可以自底向上地推导所有结点对在路径长度不大于$l=l _ 0+1$时的最短路径。这种动态规划的时间复杂度是$O(n^3\lg n)$.\
&emsp;&emsp;**Floyd-Warshall算法**也是一个动态规划的算法，但思路是先求出所有结点对在经过中间结点$v _ c$编号$c\in [1,k]$时的最短路径，再自底向上地推导出所有节点在经过中间节点编号$c\in [1,k+1]$时的最短路径。时间复杂度可以降至$O(n^3)$.
<blockquote>
&emsp;&emsp;Floy-Warshall算法可以看作是三维DP。数组$dp[i][j][k]$表示在中间节点编号$c\in [1,k]$的时候，从结点$i$结点到$j$的最短距离。状态转移方程是：
$$dp[i][j][k]=\min(dp[i][j][k-1],dp[i][k][k-1]+dp[k][j][k-1])\tag{3.1}$$
&emsp;&emsp;由于状态转移方程中$dp[…][…][k]$只和$dp[…][…][k-1]$有关，其实可以把$dp$数组的第三维压掉，变成二维DP.
</blockquote>

&emsp;&emsp;**Johnson算法**的设计还是比较巧妙的，它的核心思想就是在确保最短路径不变的情况下，把图$G$的边权$w$转化成非负的权重$\hat w$，让Dijkstra能跑起来。
<blockquote>
&emsp;&emsp;Johnson算法引入一个外部节点$s$加入$V$中，同时向$E$中添加$n$条由$s$发出、到$V$中的结点的边，生成图$G'$.在图$G'$中以$s$为源点运行Bellman-Ford算法，给每个节点标记一个$h$值$h(v)=\delta(s,v)$.<br>
&emsp;&emsp;如果Bellman-Ford算法返回True，说明图$G$不含负权重回路，以$\hat w(u,v)=w(u,v)+h(u)-h(v)$运行Dijkstra算法，能够得到各结点对之间的最短距离$\hat\delta(u,v)$.修正后的$\delta(u,v)=\hat\delta(u,v)-h(u)+h(v)$就是我们需要求的结果。<br>
&emsp;&emsp;Johnson算法适用于稀疏图，究其原因还是Bellman-Ford在非稀疏图上跑起来很需要时间。
</blockquote>

## $Part4$&emsp;图树周游
&emsp;&emsp;关于图树周游，其实无非是深搜、广搜、按层遍历（树）等一些基本方法。课程课件中涉及到了一个求连通图$G$关节点的方法：
<blockquote>
&emsp;&emsp;关节点，就是割点。对于连通图$G$，其连通分支$p(G)=1$.割点指的就是满足$p(G-\{v\}) > 1$的这些点$v$.
</blockquote>

&emsp;&emsp;对图$G$进行深度优先遍历，能够得到一颗深度优先生成树$T$，$T$中包含了$G$中所有的顶点和部分边。在图$G$中，但是不在生成树$T$中的边称为<st>逆边</st>。
<blockquote>
&emsp;&emsp;使用深度优先遍历的好处是，图$G$中不存在这样一条边$(u,v)$，使得在$T$中$u$和$v$没有祖孙关系（互相不是对方的祖先），也可以说是图$G$中不含相对$T$的<strong>交叉边</strong>。如果是使用广度优先生成树$T$，$G$就可能存在相对$T$的交叉边。
</blockquote>

&emsp;&emsp;图$G$中每一个结点$v$都有**深度优先数**$\mathrm{DFN}(v)$，表示结点$v$是深度优先遍历图$G$时第几个被遍历到的结点。每个节点$v$还有一个**最低深度优先数**$L(v)$，它的定义是：
$$L(v)=\min \lbrace \mathrm{DFN}(v),\min\lbrace L(w)|w是v的儿子\rbrace, \min\lbrace \mathrm{DFN}(w)|(v,w)是一条逆边 \rbrace \rbrace \tag{4.1}$$

&emsp;&emsp;直观地，$L(v)$就是$v$通过一条子孙路径且至多后随一条逆边所可能到达的最低深度优先数。判定割点的规则是，在深度优先生成树$T$中，根节点如果至少有两个儿子就是割点，非根节点$v$如果存在一个儿子$w$满足$L(w)\geq \mathrm{DFN}(v)$就是割点。

&emsp;&emsp;一开始我觉得这种方法很高级，后来的学习过程中知道了这种方法原来是强大的<a href="https://zhuanlan.zhihu.com/p/660554775" target="new"><font color="orange">Tarjan算法</font></a>的一个子方法，关于Tarjan算法的学习正在进行中。

$\boxed{\mathbb{The\ End.}}$
