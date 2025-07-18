<div style="float: left; width: 64%; padding: 1%;">

## 【复习提示】  

<ul>

线性表是算法题命题的重点。这类算法题的实现比较容易且代码量较少，但是要求具有最优的性能（时间/空间复杂度），才能获得满分。因此，应牢固掌握线性表的各种基本操作（基于两种存储结构），在平时的学习中多注重培养动手能力。

另需提醒的是，算法最重要的是思想！考场上的时间紧迫，在试卷上不一定要求代码具有实际的可执行性，因此应尽力表达出算法的思想和步骤，而不必过于拘泥所有细节。

此外，采用时间/空间复杂度较差的方法也能拿到大部分分数，因此在时间紧迫的情况下，建议直接采用暴力法。注意，算法题只能用 $\mathrm{C}/\mathrm{C}++$ 语言实现。  

</ul>

</ul>

# 线性表的定义和基本操作  

<ul>

## 线性表的定义  

<ul>

### 基本概念

<ul>

- 线性表是具有相同数据类型的 $n$  $_{n\geqslant0}$ ）个数据元素的有限序列
  - $n$ 为表长
  - 当 $n\,=\,0$ 时线性表是一个空表
- 若用 $L$ 命名线性表，则其一般表示为：
  $L=(a_{1},a_{2},\cdots,a_{i},a_{i+1},\cdots,a_{n})$
  - $a_{1}$ 是唯一的"第一个"数据元素，又称表头元素
  - $a_{n}$ 是唯一的"最后一个"数据元素，又称表尾元素
  - 除第一个元素外，每个元素有且仅有一个直接前驱
  - 除最后一个元素外，每个元素有且仅有一个直接后继

</ul>

### 线性表特点

<ul>

- 元素个数有限
- 元素具有逻辑上的顺序性，有先后次序
- 元素都是数据元素，每个元素都是单个元素
- 元素的数据类型都相同，占相同大小存储空间
- 元素具有抽象性，只讨论逻辑关系

> attention: 

- <span style="border: 1px solid black; padding: 5px; display: inline-block;">线性表</span>
  - 逻辑结构
  - 表示元素之间一对一的相邻关系
- <span style="border: 1px solid black; padding: 5px; display: inline-block;">顺序</span>表&<span style="border: 1px solid black; padding: 5px; display: inline-block;">链</span>表
  - 存储结构
</ul>

</ul>

## 线性表的基本操作  

<ul>

### 核心操作列表

<ul>

- InitList（&L）：初始化表
  - 构造一个空的线性表
- Length（L）：求表长
  - 返回线性表L的长度，即L中数据元素的个数
- LocateElem $(\mathbb{L},\mathsf{e})$：按值查找操作
  - 在表L中查找具有给定关键字值的元素
- GetElem $(\mathbb{L},\dot{\Sigma})$：按位查找操作
  - 获取表L中第1个位置的元素的值
- ListInsert（&L，i，e）：插入操作
  - 在表L中的第i个位置上插入指定元素e
- ListDelete（&L，i，&e）：删除操作
  - 删除表L中第i个位置的元素，并用e返回删除元素的值
- PrintList（L）：输出操作
  - 按前后顺序输出线性表L的所有元素值
- Empty（L）：判空操作
  - 若L为空表，则返回true，否则返回false
- DestroyList（&L）：销毁操作
  - 销毁线性表，并释放线性表L所占用的内存空间

> attention: 

- 基本操作的实现取决于采用哪种存储结构，存储结构不同，算法的实现也不同。 
-  符号"&"表示 $\mathrm{C++}$ 语言中的引用调用，在C语言中采用指针也可达到同样的效果。  

</ul>

</ul>

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
