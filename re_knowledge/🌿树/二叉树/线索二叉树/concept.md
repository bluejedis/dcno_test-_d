<div style="float: left; width: 64%; padding: 1%;">
    
### 线索二叉树的基本概念  

<ul>

####  <span style="color: silver;">遍历二叉树的特点：
  - 按规则 将结点排列成<span style="border-bottom: 3px dotted black;">线性</span>序列
  - 每个结点(除首尾)have 直接<span style="border-bottom: 2px solid black;">前驱</span>和<span style="border-bottom: 2px solid black;">后继</span>

> pro：后序线索二叉树的定义（2010）  

- 传统二叉链表的局限：
  - only 体现父子关系
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
  - 需增加<span style="border: 1px solid black; padding: 5px; display: inline-block;">标志域</span>标识指针类型

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/a9348224b92a82715ff985f8c31844579514448dbf87208d26fb3b1653501d4d.jpg)  
其中，标志域的含义:
$$ \boxed{\text{ltag}} = 
\begin{cases} 
0, & \text{lchild域指示node' l孩子} \\
1, & \text{.. ..前驱} 
\end{cases}$$
$$
\boxed{\text{rtag}} = 
\begin{cases} 
0, & \text{rchild域.. r..} \\
1, & \text{.. ..后继}
\end{cases} 
$$

---
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
  - 指向结点前驱和后继的<span style="border: 1px solid black; padding: 5px; display: inline-block;">指针</span>
- 线索二叉树:
  - 线索+二叉树
</ul>
    

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
