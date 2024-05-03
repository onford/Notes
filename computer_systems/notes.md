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

# 计算机系统基础笔记

<bw>wr按：\
这一部笔记，主要记录学习过程中的一些想法，以便后续查看时能回忆起当时的理解，并加深印象。实际上并不全面，只是自己想到的一些东西。这部笔记是随着学习过程实时更新的，记录内容可能会又多又累赘，后期会进行整理。</bw>

## $Chapter1$&emsp;计算机系统概述
**一、计算机基本工作原理**\
&emsp;&emsp;现代计算机很多遵循<strong>“存储程序”</strong>的方式，这指的是把事先编好的程序和原始数据送入主存，然后执行程序，由计算机自动地逐条取出、执行指令。\
&emsp;&emsp;冯·诺依曼结构的基本思想有$4$点：\
1.采用存储程序工作方式。\
2.**五个基本部件**：计算机由运算器、控制器、存储器、输入设备和输出设备组成。\
3.**五个基本部件的功能**
<table align="center">
    <caption>表 1 计算机 $5$ 个基本部件的基本功能</caption>
    <tr>
        <th>基本器件</th>
        <th>功能要求</th>
    </tr>
    <tr>
        <td>存储器</td>
        <td>存放数据和指令，两者形式上没有区别，但计算机能够区分</td>
    </tr>
    <tr>
        <td>控制器</td>
        <td>自动执行指令</td>
    </tr>
    <tr>
        <td>运算器</td>
        <td>能进行算术运算和逻辑运算</td>
    </tr>
    <tr>
        <td>输入/输出设备</td>
        <td>操作人员通过它们使用计算机</td>
    </tr>
</table>

4.计算机内部以二进制形式表示指令和数据；每条指令由操作码（指出操作类型）和地址码（指出操作数的地址）两部分组成；一串指令组成程序。

&emsp;&emsp;五个基本部件中，控制器和运算器位于CPU中。CPU的寄存器组如下图所示：
$$\text{CPU寄存器组}\begin{cases}通用寄存器组\begin{cases}
数据寄存器组\begin{cases}累加器(\text{EAX,Accumulator})\\\\基址寄存器(\text{EBX,Base})\\\\计数寄存器(\text{ECX,Count})\\\\数据寄存器(\text{EDX,Data})\end{cases}\\\\指示器变址寄存器组\begin{cases}源变址寄存器(\text{ESI,Source Index})：字符串指令源操作数的指示器\\\\目的变址寄存器(\text{EDI,Destination Index})：字符串指令目的操作数的指示器\\\\堆栈指示器(\text{ESP,Stack Pointer})：存放的是当前堆栈段中栈顶的偏移地址\\\\基址寄存器(\text{EBP,Base Pointer})：对堆栈进行操作\end{cases}\end{cases}\\\\
标志寄存器\begin{cases}\text{条件标志：溢出标志(OF)、符号表示(SF)、零标志(ZF)、进位标志(CF)}\\\\\text{控制标志：方向标志(OF)、中断允许标志(IF)、陷阱标志(TF)}\end{cases}\\\\
指令指针寄存器(\text{EIP})\\\\
段寄存器\begin{cases}代码段寄存器(\text{CS})\\\\堆栈段寄存器(\text{SS})\\\\数据段寄存器(\text{DS})\\\\附加段寄存器(\text{ES,FS,GS})\end{cases}\end{cases}$$

&emsp;&emsp;其中，**数据寄存器组**的作用是保存操作数、运算结果或作指示器、变址寄存器，**减少存取操作数所需要的访问总线和主存储器的时间，加快运行速度**；**指示器变址寄存器组**的作用是**存放操作数的偏移地址**，用作指示器或变址寄存器；**指令指针寄存器**保存下一条将要被CPU执行的指令的偏移地址，其值为该指令到所在段首址的字节距离；段寄存器保存段首描述符。

## $Chapter2$&emsp;数据的机器级表示与处理
**一、浮点数的 IEEE 754 标准**
<table align="center">
    <caption>表 2 IEEE 754 浮点数标准</caption>
    <tr>
        <th>精度类型</th>
        <td>单精度 float $32$ 位</td>
        <td>双精度 double $64$ 位</td>
    </tr>
    <tr>
        <th>阶码</th>
        <td>$8$ 位，$\mathrm{bias}=127/0\mathrm x7\mathrm f$</td>
        <td>$11$ 位，$\mathrm {bias}=1023/0\mathrm x3\mathrm{ff}$</td>
    </tr>
    <tr>
        <th>尾数</th>
        <td>$23$ 位</td>
        <td>$52$ 位</td>
    </tr>
    <tr>
        <th>特殊约定</th>
        <td colspan="2">隐藏位“1”的位置在小数点之前</td>
    </tr>
</table>

**二、数据的宽度与存储**\
**1.字长**\
&emsp;&emsp;字长指的是 CPU 内部用于整数运算的数据通路的宽度。等于 CPU 内部用于整数运算的**运算器位数**和**通用寄存器宽度**。\
**2.大/小端方式**\
&emsp;&emsp;两种方式均是以存储区块的最小地址值作为变量的地址。区别在于变量地址所指字节存的是数据的高/低位，分别对应大/小端存储。\
**3.位运算**\
&emsp;&emsp;一般对于**有符号数**，其右移是采取**算术**右移的方式，也就是符号位也跟着拓展。但是有一个例外，$\mathrm{0x80000000}$ 进行算术右移的时候将不会拓展其符号位。

## $Chapter3$&emsp;程序的转换及机器级表示
&emsp;&emsp;这一章都是以 IA-32 架构的计算机为例，所有汇编代码都是 AT&T 格式的。\
**一、寄存器组织和寻址方式**\
**1.寄存器组织**\
&emsp;&emsp;这在之前已经提过了。值得注意的一点是，指令指针寄存器 $\mathrm{EIP}$ 中的内容对汇编代码是不可读的，代码段寄存器 $\mathrm{CS}$ 中的内容是不可写但是可读的。\
**2.寻址方式**\
&emsp;&emsp;根据操作数所在位置的不同，可以分为 $3$ 类寻址方式。\
（1）操作数存放在指令中——**立即寻址**\
&emsp;&emsp;由于操作数不存放在寄存器里，也不存放在内存中，所以它是立即获取的，所以称作**立即数**。汇编格式为：`$n`，其中`n`可以是常数也可以是变量，如果是变量就表示变量的地址。\
（2）操作数存放在寄存器中——**寄存器寻址**\
&emsp;&emsp;寄存器里的内容就是操作数。汇编格式为`%R`，表示寄存器`R`里面的值。\
（3）操作数存放在内存中\
&emsp;&emsp;当操作数存放在内存中，就又有 $4$ 种寻址方式了。\
**a.直接寻址**\
&emsp;&emsp;直接寻址，一般直接采用内存的地址作为操作数。\
&emsp;&emsp;比如，可以采用`mov 0x2000,%eax`将内存地址为`0x2000`的双字数据传给寄存器`eax`；又或者`buf`是一个已经定义的字变量，可以使用`mov buf,%ax`将`buf`所在地址的字数据传递给寄存器`ax`，也可以使用`mov buf+3,%ax`将`buf`往后偏移 $3$ 个字节的地址的字数据传递给寄存器`ax`。\
**b.寄存器间接寻址**\
&emsp;&emsp;这和直接寻址的区别是，采用了一个寄存器作为中转站：先把变量在内存中的地址存入寄存器中，然后再通过寄存器访问相应地址的数据。汇编格式是`(%R)`，表示`%R`的内容，也就是以`%R`为地址读取的内存数据。\
&emsp;&emsp;比如，若寄存器`esi`中的值为`0x1000`，主存地址`1000H`处存储的双字数据为`0x00114514`，那么操作`mov (%esi),%eax`的结果，就是寄存器`eax`中的值变成`0x00114514`。\
**c.变址寻址**\
&emsp;&emsp;这和寄存器间接寻址的区别是，在寄存器所存的地址上还可以进行变换。汇编格式有`X(%R)`和`X(,%R,S)`，表示`R`的内容与`S`相乘后加上`X`，然后取所得地址的内容。\
**d.基址加变址寻址**\
&emsp;&emsp;汇编格式为`X(%BR,%IR,S)`，表示`BR`的内容加上`(IR)*S`，再加上`X`，然后取所得地址的内容。\
**二、IA-32常用指令**\
&emsp;&emsp;需要注意的一点是，IA-32中的大多两操作数指令，两个操作数**不能同时是内存操作数**。\
**1.传送指令**\
$\bigstar$ `mov`&emsp;&ensp;使用方式为`mov ops,opd`，功能`(opd) ←-- (ops)`。\
$\bigstar$ `xchg`&emsp;使用方式为`xchg ops,opd`，功能`(opd) ←-→ (ops)`。\
$\bigstar$ `lea`&emsp;&ensp;使用方式为`lea ops,%R`，功能`%R ←-- ops`。\
**2.加减指令（影响标志寄存器）**\
$\bigstar$ `add`&emsp;&ensp;使用方式为`add ops,opd`，功能`(opd) += ops`。\
$\bigstar$ `inc`&emsp;&ensp;使用方式为`inc opd`，功能`(opd)++`。\
$\bigstar$ `sub`&emsp;&ensp;使用方式为`sub ops,opd`，功能`(opd)-=(ops)`。\
$\bigstar$ `dec`&emsp;&ensp;使用方式为`dec opd`，功能`(opd)--`。\
$\bigstar$ `cmp`\
&emsp;&emsp;当进行`cmp ops,opd`时，进行减法操作`(opd)-(ops)`。实际操作就是，将`(opd)`的补码和`(ops)`的相反数的补码进行加法操作，并根据结果改编标志寄存器内的`OF,CF`标志。