<div style="float: left; width: 64%; padding: 1%;">


### 几种特殊的二叉树  
<ul>

#### 满..
- 定义：高度为 $h$，且有 <span style="border: 1px solid black; padding: 5px; display: inline-block;">$2^h\!-\!1$</span> 个结点的二叉树
- 特点：
  - 每层都含有最多的结点
  - 叶结点都在最下层
  - 除叶结点外每个结点度数为2
- 编号规则：
  - 从根结点(编号为1)开始
  - 自<span style="border-bottom: 3px dotted black;">上</span>而<span style="border-bottom: 3px dotted black;">下</span>，自<span style="border-bottom: 3px dotted black;">左</span>向<span style="border-bottom: 3px dotted black;">右</span>
  - 编号为 $i$ 的结点关系：
    - 双亲：<span style="border: 1px solid black; padding: 5px; display: inline-block;">$\lfloor i/2\rfloor$</span>
    - 左孩子：2i
    - 右..：2i+1

#### 完全..
- 定义：
  - 高度为 $h$、有 $n$ 个结点的二叉树，其结点与高度为 $h$ 的满二叉树中编号1~n的结点一一对应

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/bdec3149d9bd6e25b24dc7017ddcb7cbf0abc9f5ff55b78c04ee30a8463a64aa.jpg)  
图5.3两种特殊形态的二叉树  

<span style="font-size: 14px;"> <span style="border-bottom: 2px solid black;">除最后一层外</span>，其他各层的节点数都达到最大，最后一层的节点从左到右连续排列，且节点必须靠左对齐</span>
- 特点：
  - 结点性质：$i{\leqslant}\lfloor n/2\rfloor$ 为分支结点，否则为叶结点
  - 叶结点分布：只可能在最大的两层上出现
  - 度为1的结点：最多一个，且只有左孩子
  - 编号规律：编号i后的叶结点性质
  - 分支结点特征：
    - n为奇数：每个分支结点都有左右孩子
    - n为偶数：最大编号分支结点只有左孩子

---
#### ..排序树
- 特点：
  - 左子树结点关键字 < 根结点
  - 右子树结点关键字 > 根结点
  - 左右子树各自也是二叉排序树

#### 平衡..

- 定义：
  - $|\Delta h| \le 1$
  - 任意结点的左右子树高度差绝对值不超过1

> pro：正则 $\pmb{k}$ 叉树树高和结点数的关系的应用（2016）  

#### 正则..
- 定义：每个分支结点都有2个孩子
- 特点：只有度为0或2的结点
---
</ul>


### 二叉树的<span style="color: orange;">性质  

<ul>

#### 性质1：叶结点数 & 度为2的结点数关系
- 公式：<span style="border: 1px solid black; padding: 5px; display: inline-block;">$n_0\!=\!n_2+1$</span>
- 证明过程：
  - 设度为0,1,2的结点数分别为 $n_0,n_1,n_2$
  - 总结点数 $n\!=\!n_0+n_1+n_2$
  - 分支数 $B\!=\!n_1+2n_2$
  - 结点与分支关系：$n\,{=}\,B+1$
  - 推导得：$n_0\!=\!n_2+1$

> attention: 
该性质经常在选择题中涉及，希望读者牢记并灵活应用。  

---
####  <span style="color: silver;">性质2：层次结点数关系
>m=2'特殊情况
- 第 $k$ 层最多有 $2^{k-1}$ 个结点（$k\!\geqslant\!1$）
- 具体分布：
  - 第1层：最多1个结点
  - 第2层：最多2个结点
  - 规律：形成公比为2的等比数列

####  <span style="color: silver;">性质3：高度与结点数关系
- 高度为 $h$ 的二叉树最多有 $2^h\!-\!1$ 个结点（$h{\geqslant}1$）

> attention: 
性质2和性质3还可以拓展到 $m$ 叉树的情况，即 $m$ 叉树的第 $k$ 层最多有 $m^{k-1}$ 个结点，高度为 $h$ 的 $m$ 叉树至多有 $(2^h\!-\!1)/(m\!-\!1)$ 个结点。  
---
####  <span style="color: silver;">性质4：完全二叉树的编号特性
- 分支结点判定：$i{\leqslant}\lfloor n/2\rfloor$
- 叶结点分布：最大两层
- 度为1结点特性：最多一个且只有左孩子
- 编号规律：结点i后的叶结点性质
- 分支结点特征：
  - n为奇数：都有左右孩子
  - n为偶数：最大编号分支结点只有左孩子
- 结点关系：
  - 双亲编号：$\lfloor i/2\rfloor$（i>1）
  - 左孩子：2i
  - 右孩子：2i+1
- 层次计算：<span style="border: 1px solid black; padding: 5px; display: inline-block;">$\lfloor\log_2i\rfloor+1$</span>

####  <span style="color: silver;">性质5：完全二叉树的高度
- 公式：$\lceil\log_2(n+1)\rceil$ 或 $\lfloor\log_2\!n\rfloor+1$
- 证明：
  - 设高度为 $h$
  - $2^{h-1}<n+1\leqslant2^h$
  - 得出：$h=\lceil\log_2(n+1)\rceil$ 或 $h\!=\!\lfloor\log_2\!n\rfloor\!+1$
</ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
