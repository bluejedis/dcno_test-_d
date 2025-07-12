<div style="float: left; width: 64%; padding: 1%;">
    
### 层次遍历  

<ul>




- 遍历顺序：
  - 自上而下
  - 从左至右
  - 按层次顺序访问结点

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/fcc01cff756f99920e69dd2b2480873979105c906664f3b0bf11376b861896dd.jpg)  



#### 算法实现

<ul>

- 借助队列实现
- 基本步骤：
  - 根结点入队
  - 队列非空时：
    - 队头结点出队并访问
    - 左孩子存在则入队
    - 右孩子存在则入队
- 算法代码：
  
```c
void LevelOrder(BiTree T){
    InitQueue(Q);               //初始化辅助队列
    BiTree p;
    EnQueue(Q,T);               //将根结点入队
    while(!IsEmpty(Q)){         //队列不空则循环
        DeQueue(Q, p);          //队头结点出队
        visit(p);               //访问出队结点
        if(p->lchild!=NULL)
            EnQueue(Q,p->lchild); //若左孩子不空，则左孩子入队
        if(p->rchild!=NULL)
            EnQueue(Q,p->rchild); //若右孩子不空，则右孩子入队
    }
}
```
  

> attention: 

- 二叉树遍历 
  - 是其他所有二叉树操作的基础  

- 依赖遍历的典型操作  
  - 结点关系操作：  
    - 求结点的双亲  
    - ..孩子  
  - 结构分析操作：  
    - 求二叉树的深度  
    - 求叶结点个数  
  - 逻辑判断操作：  
    - 判断两棵二叉树是否相同  
---

- 必须掌握：  
  - 不同遍历方式（先序/中序/后序等）  
  - 灵活应用遍历解决实际问题

</ul>
</ul>    

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
