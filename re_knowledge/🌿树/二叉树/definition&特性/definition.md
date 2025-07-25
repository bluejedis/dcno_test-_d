<div style="float: left; width: 64%; padding: 1%;">

### 二叉树的定义  
<ul>

#### 基本定义
- 二叉树是一种特殊的树形结构
  - 每个结点至多只有两棵子树
  - 二叉树的子树有<span style="border-bottom: 3px dotted black;">左右之分</span>，其次序不能任意颠倒

#### 递归定义
- 二叉树是 $n$ ($n{\geqslant}0$) 个结点的有限集合：
  - 或者为空二叉树，即 $n=0$
  - 或者由一个根结点和两个互不相交的被称为根的左子树和右子树组成
    - 左子树和右子树又分别是一棵二叉树

#### 基本特征
- 二叉树是<span style="border: 1px solid black; padding: 5px; display: inline-block;">有序</span>树
  - 左、右子树颠倒会成为不同的二叉树
  - 即使只有一棵子树，也要区分左右

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/a9c401a0608c49b1b443c3b48c43f6a1ee4376c25cae2385958287b1cf7a89d5.jpg)  
图5.2二叉树的5种基本形态  

#### 与 度为2的有序树' 区别
- 结点数量要求不同
  - <span style="border-bottom: 3px dotted black;">度为2</span>的树至少有<span style="border-bottom: 2px solid black;">3个结点</span>
  - 二叉树can<span style="border: 1px solid black; padding: 5px; display: inline-block;">空</span>
- 孩子次序区分方式不同
  - 度为2的有序树：孩子左右次序<u>相对</u>于另一个孩子而言
  - 二叉树：孩子次序是<span style="border-bottom: 3px dotted black;">确定</span>的，需明确左右次序

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
