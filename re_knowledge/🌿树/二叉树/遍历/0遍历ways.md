<div style="float: left; width: 64%; padding: 1%;">
    
## 二叉树的遍历

<ul>

- ..定义  :
  - 按某条<span style="border-bottom: 2px solid black;">搜索路径</span>访问树中的每个结点  
  - 每个结点 
    - 仅被访问一次  

- 结构特点  
  - 非线性
  - 每个结点might两棵子树  


- 寻找一种规律  
  - 将树中的结点排列在 <u>线性队列</u>上  


>pro：二叉树遍历方式的分析（2009、2011、2012）
pro：（算法题）二叉树遍历的相关应用（2014、2017、2022）

---
- 确定访问顺序：  
  - 根结点（N）  
  - 左子树（L）  
  - 右子树（R）  

- 原则  
  - <span style="border: 1px solid black; padding: 5px; display: inline-block;">优先</span>遍历<span style="border: 1px solid black; padding: 5px; display: inline-block;">L</span>，再遍历R
- 常见的三种次序 
  > 以 N 位置, 而言 
  - 先序遍历（<span style="border-bottom: 3px dotted black;">N</span>LR）   
  - 中..（L<span style="border-bottom: 3px dotted black;">N</span>R）   
  - 后..（LR<span style="border-bottom: 3px dotted black;">N</span>）  



### 遍历方式

<ul>

#### 先序遍历（PreOrder）

<ul>

- 遍历规则：若二叉树为空，则什么也不做；否则
  - 1）访问根结点
  - 2）先序遍历左子树
  - 3）先序遍历右子树

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/bb476333d53f3ddbbf63ed5dee671597c8d51d49b039178da94fd12e16d3cb6c.jpg)

##### 递归算法实现

```c
void PreOrder(BiTree T){
    if(T!=NULL){
        visit(T);               //访问根结点
        PreOrder(T->lchild);    //递归遍历左子树
        PreOrder(T->rchild);    //递归遍历右子树
    }
}
```
</ul>

#### 中序遍历（InOrder）

<ul>

- 遍历规则：若二叉树为空，则什么也不做；否则
  - 1）中序遍历左子树
  - 2）访问根结点
  - 3）中序遍历右子树

>pro：中序序列中结点关系的分析（2017）

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/5a7a1e8979699afa63f476d125c173136bfd388f5b6d78a36bb8bedfd9462925.jpg)

##### 递归算法实现

```c
void InOrder(BiTree T){
    if(T!=NULL){
        InOrder(T->lchild);     //递归遍历左子树
        visit(T);               //访问根结点
        InOrder(T->rchild);     //递归遍历右子树
    }
}
```

</ul>

#### 后序遍历（PostOrder）

<ul>

- 遍历规则：若二叉树为空，则什么也不做；否则
  - 1）后序遍历左子树
  - 2）后序遍历右子树
  - 3）访问根结点

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/83d65a43ce1d35fa50d330ff9b10a6426b21fdcc73aff5dc92b3166bd085a05b.jpg)

##### 递归算法实现

```c
void PostOrder(BiTree T){
    if(T!=NULL){
        PostOrder(T->lchild);   //递归遍历左子树
        PostOrder(T->rchild);   //递归遍历右子树
        visit(T);               //访问根结点
    }
}
```

</ul>
</ul>

### 算法性能分析

<ul>

- 时间复杂度
  - 每个结点都访问一次且仅访问一次，所以时间复杂度都是O(n)
- 空间复杂度
  - 递归工作栈的栈深恰好为树的深度
  - 最坏情况：二叉树是有n个结点且深度为n的单支树，空间复杂度为O(n)

</ul>    

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
