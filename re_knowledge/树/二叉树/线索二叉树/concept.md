<div style="float: left; width: 64%; padding: 1%;">
    
### 线索二叉树的基本概念  

<ul>

####  <span style="color: silver;">遍历二叉树的特点：
  - 按规则将结点排列成线性序列
  - 每个结点(除首尾)有直接前驱和后继

> pro：后序线索二叉树的定义（2010）  

- 传统二叉链表的局限：
  - 仅能体现父子关系
  - 无法直接获取遍历前驱后继

####  <span style="color: silver;">空指针利用：
  - n个结点中有n+1个空指针
  - 原因：
    - 叶结点有2个空指针
    - 度为1的结点有1个空指针
    - 空指针总数 = 2n₀+n₁
    - n₀=n₂+1
    - 总数 = n₀+n₁+n₂+1 = n+1

####  <span style="color: silver;">线索化规则：
  - 无左子树：lchild指向前驱
  - 无右子树：rchild指向后继
  - 需增加标志域标识指针类型

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/a9348224b92a82715ff985f8c31844579514448dbf87208d26fb3b1653501d4d.jpg)  
其中，标志域的含义:

####  <span style="color: silver;">存储结构：

```c
typedef struct ThreadNode{
    ElemType data;                      //数据元素
    struct ThreadNode *lchild,*rchild;  //左、右孩子指针
    int ltag,rtag;                      //左、右线索标志
}ThreadNode,*ThreadTree;
```

- 线索链表:
  - 以这种结点结构构成的二叉链表as二叉树'存储结构
- 线索:
  - 指向结点前驱和后继的指针
- 线索二叉树:
  - 线索+二叉树
</ul>
    

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
