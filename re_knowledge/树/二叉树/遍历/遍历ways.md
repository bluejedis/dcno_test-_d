<div style="float: left; width: 64%; padding: 1%;">
    
## 二叉树的遍历

<ul>

三义树的遍历是指按某条搜索路径访问树中每个结点，使得每个结点均被访问一次，而且仅被访问一次。由于二叉树是一种非线性结构，每个结点都可能有两棵子树，因此需要寻找一种规律，以便使二叉树上的结点能排列在一个线性队列上，进而便于遍历。

pro：二叉树遍历方式的分析（2009、2011、2012）pro：（算法题）二叉树遍历的相关应用（2014、2017、2022）

由二叉树的递归定义可知，遍历一棵二叉树便要决定对根结点N、左子树L和右子树R的访问顺序。按照先遍历左子树再遍历右子树的原则，常见的遍历次序有先序（NLR）、中序（LNR）和后序（LRN）三种遍历算法，其中"序"指的是根结点在何时被访问。

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

void PreOrder（BiTree T){
    if（T!=NULL){
        visit(T);  //访问根结点
        PreOrder(T->lchild);  //递归遍历左子树
        PreOrder（T->rchild);  //递归遍历右子树

</ul>

#### 中序遍历（InOrder）

<ul>

- 遍历规则：若二叉树为空，则什么也不做；否则
  - 1）中序遍历左子树
  - 2）访问根结点
  - 3）中序遍历右子树

pro：中序序列中结点关系的分析（2017）

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/5a7a1e8979699afa63f476d125c173136bfd388f5b6d78a36bb8bedfd9462925.jpg)

##### 递归算法实现

void InOrder（BiTree T）{
    if（T!=NULL){
        InOrder（T->lchild);  //递归遍历左子树
        visit(T);  //访问根结点
        InOrder(T->rchild);  //递归遍历右子树

</ul>

#### 后序遍历（PostOrder）

<ul>

- 遍历规则：若二叉树为空，则什么也不做；否则
  - 1）后序遍历左子树
  - 2）后序遍历右子树
  - 3）访问根结点

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/83d65a43ce1d35fa50d330ff9b10a6426b21fdcc73aff5dc92b3166bd085a05b.jpg)

##### 递归算法实现

void PostOrder（BiTree T){
    if（T!=NULL){
        PostOrder(T->lchild);  //递归遍历左子树
        PostOrder(T->rchild);  //递归遍历右子树
        visit(T);  //访问根结点

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
