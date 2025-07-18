<div style="float: left; width: 64%; padding: 1%;">
    
### 递归算法和非递归算法的转换  

<ul>

> attention: 

非递归遍历算法的难度较大，统考对非递归遍历算法的要求通常不高。  

#### 递归执行过程分析

<ul>

- 三种遍历算法的递归执行过程相同（抹去visit()语句）
- 递归执行过程说明：
  - 向下箭头：更深层递归调用
  - 向上箭头：递归调用返回
  - 标记符号：
    - 三角形：先序访问输出
    - 圆形：中序访问输出
    - 方形：后序访问输出

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/7a51d5bf37d72f50eb146aea747131d612db4759b8ba5278104c5bcb2f119547.jpg)  

---

</ul>

#### 非递归实现分析

<ul>

##### 中序遍历非递归实现

<ul>

- 借助栈的实现思路：
  - 沿左孩子依次入栈直到为空
  - 栈顶元素出栈并访问
  - 处理右子树

```c
void InOrder2(BiTree T){
    InitStack(S); BiTree p=T;       //初始化栈 s; p 是遍历指针
    while(p||!IsEmpty(S)){          //栈不空或 p 不空时循环
        if(p){                      //一路向左
            Push(S,p);              //当前结点入栈
            p=p->lchild;            //左孩子不空，一直向左走
        }
        else{                       //出栈，并转向出栈结点的右子树
            Pop(S,p);visit(p);      //栈顶元素出栈，访问出栈结点
            p=p->rchild;            //向右子树走，p赋值为当前结点的右孩子
                                    //返回 while 循环继续进入 if-else 语句
        }
    }
}
``` 

</ul>

##### 先序遍历非递归实现

<ul>

- 基本思想与中序类似
- 区别：访问结点操作在入栈前进行

```c
void PreOrder2(BiTree T){
    InitStack(S); BiTree p=T;       //初始化栈 s; p 是遍历指针
    while(p||!IsEmpty(S)){          //栈不空或 p 不空时循环
        if(p){                      //一路向左
            visit(p);Push(S,p);     //访问当前结点，并入栈
            p=p->lchild;            //左孩子不空，一直向左走
        }
        else{                       //出栈，并转向出栈结点的右子树
            Pop(S,p);               //栈顶元素出栈
            p=p->rchild;            //向右子树走，p赋值为当前结点的右孩子
                                    //返回 while 循环继续进入 if-else 语句
        }
    }
}
```

</ul>

##### 后序遍历非递归实现

<ul>

- 实现难度最大
- 访问条件：
  - 左右子树都已访问
  - 左子树在右子树前访问
- 实现思路：
  - 从根结点开始入栈
  - 沿左子树搜索直到无左孩子
  - 出栈条件：
    - 右子树为空
    - 右子树刚访问完

</ul>
</ul>
</ul>
    

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
