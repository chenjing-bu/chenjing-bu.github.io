---
title: 顶点代数直观指南
date: 2024-12-01
lastmod: 2025-03-18
tags: [数学]
tagline: 翻译自英文原文
abstract: |
  顶点代数的一种直观解释.
---

顶点代数是一种有些神秘的代数结构.
其基本思想来自物理学中的共形场论,
它们同时也与数学的各个领域有着深刻的联系.

我在撰写本科毕业论文时第一次接触顶点代数.
那时, 我感觉它们相当令人困惑.
它们的定义很技术化,
而我查阅的所有标准参考文献, 包括
\[[Frenkel, Ben-Zvi 2004](#参考文献)\] 和
\[[Kac 1998](#参考文献)\] (还声称 ｢写给初学者｣!),
都没有在直观上提供太大帮助.

现在, 与这些奇怪的代数打交道一段时间后,
我大概能更好地理解它们了.
但我仍然很惊讶, 它们背后的简单直观想法,
这些是专家们熟知的,
但却十分不容易在文献中找到.
我怀疑这些想法可能根本没有以明确形式写下来过.

因此, 我决定写下这篇笔记来解释这些想法.
我希望这能对其他正在学习顶点代数的人有所帮助,
尤其是那些像我几年前一样感到困惑的人.

{{<toc>}}

## 想法

简而言之, 顶点代数是一种**二维**代数结构.

我们将通常的结合代数看作是一种**一维**结构,
也就是定义在一条直线 $\mathbb{R}$ 上的结构,
即给定直线上的几个点,
如果我们在每个点上放一个代数的元素,
就能按照直线给出的顺序将它们相乘.
我们可以移动这些点, 只要这些点不改变顺序,
相应的乘积就不会改变.
如下图左侧所示.

{{< centre width="36em" >}}
![顶点代数示意图](/posts/2024/vertex-algebras-done-right/1.png)
{{< /centre >}}

而在顶点代数中, 元素是在复平面上相乘的.
也就是说, 给定几个点 $z_1, \dotsc, z_n \in \mathbb{C}$,
如果我们在每个点 $z_i$ 上放一个元素 $a_i$,
就能得到乘积 $a_1 (z_1) \cdots a_n (z_n)$.

顶点代数的一个主要特征是,
乘积 $a_1 (z_1) \cdots a_n (z_n)$
**亚纯**地依赖于各个变量 $z_i$.
并且, 该乘积只有在 $z_i = z_j$ 时才能有极点,
其中 $i \neq j$,
即只有两点相撞时, 乘积才可能有极点.

{{<spoiler title="与小圆盘算畴的联系">}}
如果你听说过**小圆盘算畴** $\mathbb{E}_n$
([*n*Lab](https://ncatlab.org/nlab/show/little+cubes+operad)),
你可能会觉察到顶点代数与 $\mathbb{E}_2$-代数之间的相似性.
其主要区别就在于上述的亚纯性.
在 $\mathbb{E}_2$-代数中,
乘积连续地依赖于点的位置,
并且, 例如当一个点绕另一个点转动一周时,
这能探测到该代数的高阶同伦结构.
顶点代数并不关心同伦结构 (向量空间是可缩的),
但从中可以提取导数或者留数等额外信息,
这来源于其亚纯性.

此关系可以用**分解代数**
([*n*Lab](https://ncatlab.org/nlab/show/factorization+algebra))
的理论来更精确地描述,
它在某种意义上同时推广了上述两种代数.

另可参见[此 MathOverflow 问题](https://mathoverflow.net/a/54008/484230).
{{</spoiler>}}

## 新定义

以下是顶点代数的一个新定义.
我认为这比标准定义更有启发性,
我们稍后再来讨论后者.

{{<block title="定义">}}
**顶点代数**是:

- 向量空间 $V$,

- 带有单位元 $1 \in V$,

- 以及一族乘法操作

  $$
    \begin{aligned}
      V^{\otimes n} & \longrightarrow V [[z_1, \dotsc, z_n]] \\, [(z_i - z_j)^{-1}] \ ,
      \\\\[.5em]
      a_1 \otimes \cdots \otimes a_n & \longmapsto a_1 (z_1) \cdots a_n (z_n) \ ,
    \end{aligned}
  $$

  其中 $0$ 元乘法给出单位元 $1$,

满足以下性质:

- **单位律:** 总有 $a (0) = a$,
  即 $a (z) = a + O (z)$.

- **交换律:** 乘积 $a_1 (z_1) \cdots a_n (z_n)$
  不依赖于因子的顺序.
  例如, $a (z) \cdot b (w) = b (w) \cdot a (z)$.

- **结合律:** 这包括一系列公理, 例如

  $$
    \begin{aligned}
      & \bigl[ a_1 (z_1) \cdot a_2 (z_2) \bigr] (z) \cdot
      \bigl[ b_1 (w_1) \cdot b_2 (w_2) \bigr] (w)
      \\\\[.5em]
      & \qquad =
      a_1 (z_1 + z) \cdot a_2 (z_2 + z) \cdot
      b_1 (w_1 + w) \cdot b_2 (w_2 + w) \ ,
    \end{aligned}
  $$

  其中我们按照 $|z_i|, |w_i| \ll |z|, |w|$ 来展开右侧的幂级数.
  这是对两组两个元素的情况,
  对于任意数量的任意大小的组都有类似的公理.
  括号中的变量遵循以下规则:
  当等号左侧的两个变量叠在一起时,
  我们在等号右侧把它们加起来.

{{</block>}}

这个结合律看起来可能很复杂,
但实际上它就是普通的乘法结合律,
只是加入了一堆 $z$ 和 $w$ 变量.

这种更直接的定义在
\[[Borcherds 1998](#参考文献)\]
中有所暗示, 但没有完全阐明.
\[[Kim 2011](#参考文献)\]
对此进行了更严格的论证,
但奇怪的是, 他没有用顶点代数的语言来表述其结果.
我是从 Dominic Joyce 的一篇未发表的论文中学到这一点的.
截至本文撰写时, 我还不知道任何严格提及此定义的文献.

{{<spoiler title="注记">}}
从技术上看, 也许可以说这比传统定义更复杂,
因为结合律包括无穷多个公理.
然而, 这并不是本文的重点, 重点在于让定义更直观,
而新的定义看起来更像普通代数的定义.

另外, 基于上述定义,
我们可能会期望顶点代数是某个范畴中的交换代数对象.
事实上, 这几乎是正确的, 但这里的范畴中不是所有态射都能复合.
这一点在
\[[Borcherds 1998](#参考文献): Example 6.6\]
中有所解释.
{{</spoiler>}}

## 场与平移

仔细观察上述定义,
我们可以提取一些有用的信息.
这里, 我将重点解释结论, 而略去细节.

首先, 由于定义了 $1$ 元乘法,
这意味着每个元素 $a \in V$ 都自带一个幂级数 $a (z) \in V [[z]]$,
有的人可能称之为 $a$ 对应的**场** (而另一些人则不会!).

从而, 我们可以对场 $a (z)$ 关于 $z$ 求导,
这定义了幂级数 $\partial_z a (z) \in V [[z]]$.
我们将 $z = 0$ 处的导数记为

$$
  T a = \partial_z a (z) \\, \bigr|_{z = 0} \in V \ .
$$

我们也有 $(T a) (z) = \partial_z a (z)$,
这说明将 $\partial_z a (z)$ 也称为场是合理的.
类似地, 也可以对 $a (z)$ 求高阶导数.

上述算子 $T \colon V \to V$ 称为**平移算子**,
但我觉得这个名字有些误导, 应该称之为求导算子之类.
事实上, 真正的平移算子应该是

$$
  \exp (z T) = \sum_{n = 0}^\infty \frac{z^n}{n!} T^n
  \colon V \longrightarrow V [[z]] \ .
$$

让我来详细解释一点. 我们有恒等式
$\exp (z \partial_z) \\, a (w) = a (z + w)$,
这是完全形式的结论,
并不涉及任何顶点代数的性质.
这意味着

$$
  \exp (z T) \\, a (w) = a (z + w) \ ,
$$

这才是称之为平移算子的真正原因.
特别地, 取 $w = 0$ 得到

$$
  a (z) = \exp (z T) \\, a \ ,
$$

这可以看作场 $a (z)$ 的另一种定义,
也会对接下来理解顶点代数的传统定义有所帮助.

## 传统定义

现在, 我们来解释顶点代数的标准定义如何与新定义相吻合.
其标准定义在不同文献中略有不同,
但都类似于以下定义, 取自
\[[Frenkel, Ben-Zvi 2004](#参考文献)\].

{{<block title="定义">}}
**顶点代数**是:

- 向量空间 $V$,

- 带有单位元 $1 \in V$,

- 以及算子 $T \colon V \to V$, 称为平移算子,

- 以及乘法操作

  $$
    \begin{aligned}
      V \otimes V
      & \longrightarrow
      V [[z]] [z^{-1}] \ ,
      \\\\[.5em]
      a \otimes b
      & \longmapsto
      Y (a, z) \\, b \ ,
    \end{aligned}
  $$

满足以下性质:

- **单位律:** $Y (1, z) = \operatorname{id}_V$,
  并且 $Y (a, z) \\, 1 = a + O (z)$.

- **平移:** 交换子
  $[T, Y (a, z)] = \partial_z Y (a, z)$, 并且 $T (1) = 0$.

- **定域性:** 对任意 $a, b \in V$, 存在 $n > 0$ 使得
  $(z - w)^n \cdot [Y (a, z), Y (b, w)] = 0$.

{{</block>}}

要从新定义中得到这个标准定义,
平移算子 $T$ 就如之前一样,
而乘法操作 $Y (a, z) \\, b$ 定义为

$$
  Y (a, z) \\, b = a (z) \cdot b (0) \ .
$$

乘积 $Y (a, z) \\, 1 \in V [[z]]$
就是之前的 $a (z)$.
更一般地, 之前的乘积
$a_1 (z_1) \cdots a_n (z_n)$ 就是现在的
$Y (a_1, z_1) \cdots Y (a_n, z_n) \\, 1$.
更准确地说, 在之前的乘积中将 $(z_i - z_j)^{-1}$
按照 $|z_j| \ll |z_i|$ 展开为幂级数,
其中 $i < j$,
就得到现在的乘积.

这里的平移公理只是换一种方式来说明 $T$ 是求导算子.

最后, 定域性公理可能看起来很奇怪.
但事实上, 在我们之前介绍的新定义中, 这只是在说
$a (z) \cdot b (w) = b (w) \cdot a (z)$,
只是用了更复杂的方式来表述,
因为在传统定义中,
我们必须选择一个顺序来展开幂级数:
在乘积
$Y (a, z) \\, Y (b, w) \\, c$ 和
$Y (b, w) \\, Y (a, z) \\, c$ 中,
前者是按照 $|w| \ll |z|$ 展开的,
而后者是按照 $|z| \ll |w|$ 展开的,
因此它们可能不相等,
尽管它们都是同一个表达式的展开.
例如, 我们可能会遇到类似下面的情况:

$$
  \sum_{n = 0}^\infty \frac{w^n}{z^{n + 1}}
  \sim \frac{1}{z - w}
  = -\frac{1}{w - z}
  \sim -\sum_{n = 0}^\infty \frac{z^n}{w^{n + 1}} \ ,
$$

其中最左和最右的项给出了同一个表达式的不同展开.
然而, 乘以 $(z - w)$ 后, 两边都变成了 $1$.
一般来说, 我们可能需要乘以更高次幂 $(z - w)^n$ 来使它们相等,
但这总是可能的,
我们需要的幂次 $n$ 就是原来的表达式在 $z = w$ 处的极点阶数.

## 一个例子

我们通过一个例子,
看看这个新定义如何帮助我们理解顶点代数的其他性质.

有一个关于顶点代数的性质, 有时称为**反对称性**
(例如见 \[[Frenkel, Ben-Zvi 2004](#参考文献): Proposition 3.2.5\]).
它指的是下面的恒等式:

$$
  Y (a, z) \\, b = \exp (z T) \\, Y (b, -z) \\, a \ .
$$

在了解这个新定义之前,
我一直觉得这个公式难以理解,
但从新的角度看,
这只是下面的恒等式:

$$
  a (z) \cdot b (0) = b (0) \cdot a (z) = \bigl( b (-z) \cdot a (0) \bigr) (z) \ ,
$$

这里, 我们回忆根据结合律,
当变量叠在一起时, 我们把它们相加,
这就是我们在最后一步中所做的.
类似这样的论述帮助我在我自己的工作中简化了不少思考过程.

## 参考文献

- **Borcherds,** R. E. (1998).
  Vertex algebras.\
  {{<dimmed>}}
  _Topological field theory, primitive forms and related topics_,
  35--77.
  Birkhäuser.
  {{</dimmed>}}\
  ([zbMATH](https://zbmath.org/0956.17019))
  ([arXiv](https://arxiv.org/abs/q-alg/9706008))

- **Frenkel,** E., and **Ben-Zvi,** D. (2004).
  _Vertex algebras and algebraic curves_, 2nd ed.\
  {{<dimmed>}}
  Mathematical Surveys and Monographs 88.
  American Mathematical Society.
  {{</dimmed>}}\
  ([doi](https://doi.org/10.1090/surv/088))
  ([zbMATH](https://zbmath.org/1106.17035))

- **Kac,** V. (1998).
  _Vertex algebras for beginners_, 2nd ed.\
  {{<dimmed>}}
  University Lecture Series 10.
  American Mathematical Society.
  {{</dimmed>}}\
  ([doi](https://doi.org/10.1112/s0024609397353612))
  ([zbMATH](https://zbmath.org/0924.17023))

- **Kim,** N. (2011).
  Associativity of field algebras.\
  {{<dimmed>}}
  _Annales Henri Poincaré_ 12 (6), 1145--1168.
  {{</dimmed>}}\
  ([doi](https://doi.org/10.1007/s00023-011-0092-5))
  ([zbMATH](https://zbmath.org/1226.81115))

另见:

- ***n*Lab:**
  [Vertex operator algebra](https://ncatlab.org/nlab/show/vertex+operator+algebra).

- **Wikipedia:**
  [Vertex operator algebra](https://en.wikipedia.org/wiki/Vertex_operator_algebra).

- **香蕉空间:**
  [顶点代数](https://www.bananaspace.org/wiki/%E9%A1%B6%E7%82%B9%E4%BB%A3%E6%95%B0).
