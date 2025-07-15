<div style="float: left; width: 64%; padding: 1%;">

## B树和$\mathbf{B}+$树

考研大纲对B树和${\mathrm{B+}}$树的要求各不相同，重点在于考查B树，不仅要求理解B树的基本特点，还要求掌握B树的建立、<span style="color: GreenYellow;">插入</span>和删除操作，而对${\mathrm{B+}}$树则只考查concept。

<ul>

### B树及其基本操作

所谓$m$阶B树是所有node的平衡因子均=0的<span style="border: 1px solid black; padding: 5px; display: inline-block;">$m$路平衡<span style="color: Gold;">search</span>树</span>。

> pro：B树的定义和特点（2009）

<ul>

#### B树的定义特性

- 一棵$m$阶B树或为空树，或为满足如下特性的$m$叉树：
  - 树中每个node至多有$m$棵子树，即至多有$m-1$个关键字
  - 若根node不是叶node，则至少有2棵子树，即至少有1个关键字
  - 除根node外的所有非叶node至少有$\lceil m/2\rceil$棵子树，即至少有$\lceil m/2\rceil_{-1}$个关键字
  - 所有非叶node的结构如下：

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/641123898fc54d168c81307aaa0f46a0aeb4dc3c39dc6bc0add67a795683e706.jpg)`

  - 其中：
    - $K_{i}$ $(i=1,2,\cdots,n)$为node的关键字，且满足$K_{1}<K_{2}<\cdots<K_{n}$
    - $P_{i}\,\,(i=0,\,1,\cdots,n)$为指向子树根node的指针
    - 指针$P_{i+1}$所指子树中所有node的关键字均＜$K_{i}$
    - $P_{i}$所指子树中所有node的关键字均＞$K_{i}$
    - $n~(\lceil m/2\rceil\!-\!1\!\leqslant\!n\!\leqslant\!m-1)$为node中关键字的个数
  - 所有的叶node都出现在同一层次上，并且不带信息

> pro：B树中关键字数和node数的分析（2013、2014、2018、2021）

</ul>

<ul>

#### B树的性质分析

- 以图7.28所示5阶B树为例：

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/3296559c5d2d7110e03f8b45bfcbf4ee8b8931f234697bbe0eba579683969db7.jpg)`

- 主要性质：
  - node的孩子个数等于该node中关键字个数加1
  - 根node特性：
    - 无关键字时无子树(空树)
    - 有关键字时子树个数≥2
  - 非根非叶node特性：
    - 至少有$\scriptstyle{m/2}\,=\,\left\lceil5/2\right\rceil=3$棵子树
    - 至少有2个关键字
    - 至多有5棵子树和4个关键字
  - 关键字排序特性：
    - 从左到右递增<span style="color: gray;">有</span><span style="color: LightSkyBlue;">序</span>
    - 左侧子树关键字＜当前关键字
    - 右侧子树关键字＞当前关键字
  - 叶node特性：
    - 均在第4层
    - 代表查找失败位置

</ul>



#### B树的查找

<ul>

- 基本特点：
  - 与二叉排序树相似
  - 每个node包含多个关键字
  - 进行多路分支决定

##### 查找操作的两个基本步骤

- 在B树中找node(磁盘操作)
- 在node内找关键字(内存操作)
  - 可用顺序查找或折半查找
  - 查找效率取决于目标node层次数

##### 查找过程

- 从根node开始
- 在当前node<span style="color: gray;">有</span><span style="color: LightSkyBlue;">序</span>表中查找
- 根据比较结果选择子树继续查找
- 直到找到目标或达到叶node

</ul>



#### B树的<span style="color: LightSkyBlue;">高度</span>分析

<ul>

##### <span style="color: LightSkyBlue;">高度</span>定义

- 不包括最后不带信息的叶node层

##### <span style="color: LightSkyBlue;">高度</span>范围分析

- 最小<span style="color: LightSkyBlue;">高度</span>情况：
  - 每个node关键字数最多
  - 满足：$n\!\leqslant\!(m-1)(1+m+m^{2}+\cdots+m^{h-1})=m^{h}-1$
  - 得到：$h\geqslant\log_{m}\left(n+1\right)$

- 最大<span style="color: LightSkyBlue;">高度</span>情况：
  - 每个node关键字数最少
  - 层次node数分析：
    - 第一层：至少1个node
    - 第二层：至少2个node
    - 第三层：至少$2\left\lceil m/2\right\rceil$个node
    - 第$h+1$层：至少$2(\lceil m/2\rceil)^{h-1}$个node
  - 满足：$n+1\!\geqslant\!2(\lceil m/2\rceil)^{h-1}$
  - 得到：$h{\leqslant}\log_{\lceil m/2\rceil}((n+1)/2)+1$

</ul>



#### B树的<span style="color: GreenYellow;">插入</span>操作

<ul>

> pro：通过<span style="color: GreenYellow;">插入</span>操作<span style="color: Lime;">构造</span>一棵初始为空的B树（2020）

##### <span style="color: GreenYellow;">插入</span>过程

- 定位阶段：
  - 使用B树查找算法
  - 找到<span style="color: GreenYellow;">插入</span>的终端node位置

- <span style="color: GreenYellow;">插入</span>阶段：
  - 关键字数限制：$[\lceil m/2\rceil\!-\!1,\,m\!-\!1]$
  - 两种情况：
    - <span style="color: GreenYellow;">插入</span>后关键字数<m：直接<span style="color: GreenYellow;">插入</span>
    - <span style="color: GreenYellow;">插入</span>后关键字数>m-1：需要分裂

##### node分裂方法

- 基本步骤：
  - 创建新node
  - 从中间位置分割关键字
  - 左部分保留在原node
  - 右部分移至新node
  - 中间关键字上移至父node
- 特殊情况：
  - 父node可能需要继续分裂
  - 分裂可能传播至根node
  - 可能导致树<span style="color: LightSkyBlue;">高度</span>增1

- 示例(m=3的B树)：

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/80d65ed644ea63d8e94f85979f930603e6eb9b46bb9c910cd6cf03ad6c8bf748.jpg)`

</ul>

</ul>



### B树的删除

<ul>

#### 删除操作概述

- B树的删除操作与<span style="color: GreenYellow;">插入</span>操作类似，但更复杂
- 需确保删除后node关键字个数≥m/2-1
- 可能涉及node的"合并"问题

> pro：B树的删除操作的实例（2012、2022）





#### 非终端node的删除处理

- 当被删关键字k不在终端node时：
  - 可用k的前驱(k')或后继替代
    - 前驱：k左侧子树中"最右下"元素
    - 后继：k右侧子树中"最左下"元素
  - 然后删除k'
  - k'必定在终端node中

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/7238b2b80bcf193f427d7371143169091e88dc7e89de6a71f0c30816046d808c.jpg)`

</ul>



#### 终端node的删除情况

<ul>

##### 情况一：直接删除

- 条件：删除前关键字个数≥⌈m/2⌉
- 操作：直接删去该关键字

##### 情况二：借助兄弟node

- 条件：
  - 删除前关键字个数=⌈m/2⌉-1
  - 相邻兄弟node关键字个数≥⌈m/2⌉
- 操作：调整该node、兄弟node及父node

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/215b6baf0ac411ac31105377425b16f9f12f9828b89f9a64b2c180cfee010990.jpg)`

##### 情况三：node合并

- 条件：
  - 删除前关键字个数=⌈m/2⌉-1
  - 相邻兄弟node关键字个数≤⌈m/2⌉-1
- 操作：与兄弟node及父node关键字合并

> pro：非空B树的<span style="color: Gold;">search</span>、<span style="color: GreenYellow;">插入</span>、删除操作的特点（2023）

</ul>



#### 合并后的处理

- 双亲node为根node时：
  - 若关键字减至0，删除根node
  - 合并后新node成为根
- 双亲node非根node时：
  - 若关键字数减至⌈m/2⌉-2
  - 需与兄弟node调整或合并
  - 重复直至符合B树要求

</ul>

</ul>


---

### B+树的concept

> pro：B+树的应用场合（2017）

<ul>

#### B+树的定义条件

- m阶B+树需满足：
  1. 分支node最多m棵子树
  2. node最小子树要求：
     - 非叶根node至少两棵
     - 其他分支node至少⌈m/2⌉棵
  3. 子树个数等于关键字个数
  4. 叶node特性：
     - 包含全部关键字
     - 包含记录指针
     - 按大小顺序排列
     - 相邻叶node相互链接
  5. 分支node特性：
     - 仅包含子node最大关键字
     - 包含指向子node的指针

> pro：B树和B+树的差异的分析（2016）





#### B+树与B树的主要差异
<ul>

##### 结构差异

- 关键字与子树关系：
  - B+树：n个关键字对应n棵子树
  - B树：n个关键字对应n+1棵子树

##### node特性差异

- 关键字数量范围：
  - B+树：⌈m/2⌉≤n≤m
  - B树：⌈m/2⌉-1≤n≤m-1
- 关键字分布：
  - B+树：叶node包含全部关键字
  - B树：关键字不重复出现

##### 功能特性差异

- node作用：
  - B+树：非叶node仅做索引
  - B树：所有node既存储又索引
- 链接结构：
  - B+树：叶node形成链表
  - B树：node间独立

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/db9dc115f173d19c088aab329b4f42f2125e735f6d5222eacbec4640c3e2ffab.jpg)`

</ul>



#### B+树的操作特点

- 基本类似B树
- <span style="color: Gold;">search</span>特点：
  - 总是遍历到叶node
  - 路径：根node到叶node
  - 支持两种<span style="color: Gold;">search</span>方式：
    - 顺序<span style="color: Gold;">search</span>
    - 多路<span style="color: Gold;">search</span>

</ul>

</ul>

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
