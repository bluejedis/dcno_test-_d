<div style="float: left; width: 64%; padding: 1%;">
    
### 由遍历序列构造二叉树  

<ul>

> pro：先序序列对应的不同二叉树的分析（2015）  

#### 基本概念

<ul>

- 对于给定二叉树：
  - 四种遍历序列都是确定的
  - <u>单一</u>遍历序列<span style="border-bottom: 3px dotted black;">无法</span> <u>唯一确定</u>二叉树
  - <span style="border: 1px solid black; padding: 5px; display: inline-block;">中序</span>序列 + 其他任一序列可唯一确定二叉树

</ul>

#### 构造方法

<ul>

##### 中序+先

<ul>

> pro：先序序列和中序序列相同时确定的二叉树（2017）
由先序序列和中序序列构造一棵二叉树（2020、2021）
- 构造原理：
  - <span style="border-bottom: 3px dotted black;">先序</span>序列第一个结点为<span style="border-bottom: 2px solid black;">根</span>结点
  - <span style="border: 1px solid black; padding: 5px; display: inline-block;">根</span>结点将<span style="border-bottom: 3px dotted black;">中序</span>序列分为<span style="border-bottom: 2px solid black;">左右子树
  - 
  - 子序列长度相等 原则
  - <u>递归</u>分解确定树结构

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/f95f56d393b614bbe625168363fd791b2fa3b99d431538422cdb0c9dfce8aee8.jpg)  

- 构造示例：
  - 序列：
    - 先序：<span style="border: 1px solid black; padding: 5px; display: inline-block;">A</span>BCDEFGHI
    - 中序：BC<span style="border: 1px solid black; padding: 5px; display: inline-block;">A</span>EDGHFI
  - 分析过程：
    - A为根结点
    - BC为左子树中序序列
    - EDGHFI为右子树中序序列
    - 递归分解其余结点

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/1bdfc32800eb0bdcdf69f66b04372af5f987fca29874a7edb3170bdcc7281785.jpg) 

---

</ul>

##### ..+后

<ul>

>pro: 由后序序列和树形构造一棵二叉树（2017、2023）
- 构造原理：
  - <span style="border: 1px solid black; padding: 5px; display: inline-block;">后序</span>序列<span style="border-bottom: 3px dotted black;">最后</span>一个结点为<span style="border-bottom: 2px solid black;">根</span>结点
  - 根结点分割中序序列
  - 递归分解确定结构

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/b7ff525d65d5eecf2e799de58498c82c5cc855212f4dedd5b861b42917822ce2.jpg)  

</ul>

##### ..+层

<ul>

- 构造原理：
  - <span style="border: 1px solid black; padding: 5px; display: inline-block;">层序</span> <span style="border-bottom: 3px dotted black;">第一个</span>结点为<span style="border-bottom: 2px solid black;">根</span>结点
  - 分割中序序列
  - 左子树根in层序第二位
  - R根紧随其后
  - 递归划分确定结构

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/bfeb791360f3d1b1e847316927966170a32c8f5faecc10370d6de9816a2ae6c1.jpg)  

</ul>

#### 注意事项

<ul>

- 无法唯一确定二叉树的组合：
  - 先序序列+后序序列
  - 先序序列+层序序列
  - 后序序列+层序序列
- 示例：
  - 两棵不同二叉树可能有相同的：
    - 先序序列：AB
    - 后序序列：BA
    - 层序序列：AB

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/8a85e2de2af6b7d96b93dbde3997116acee9adafbb64aa34b17139eaf5456102.jpg)  
图5.16两棵不同的二叉树  

</ul>
</ul>
</ul>
</ul>
    

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
