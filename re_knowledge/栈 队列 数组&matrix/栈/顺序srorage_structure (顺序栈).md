<div style="float: left; width: 64%; padding: 1%;">

## 顺序存储结构

<ul>

### 顺序栈的基本概念
- 采用顺序存储的栈称为顺序栈
  - 利用连续存储单元存放数据元素
  - 附设指针（top）指示栈顶位置

### 顺序栈的实现
<ul>

#### 数据结构定义
<ul>

#define MaxSize 50//定义栈中元素的最大个数
typedef struct{ 
    Elemtype data[MaxSize];//存放栈中元素
    int top; //栈顶指针 
}SqStack;
</ul>

#### 栈的基本属性
<ul>

- 栈顶指针：s.top
  - 初始时设置s.top=-1
- 栈顶元素：S.data[S.top]
- 基本操作
  - 进栈：栈不满时，指针先加1，再送值
  - 出栈：栈非空时，先取值，再指针减1
- 状态判断
  - 栈空条件：S.top==-1
  - 栈满条件：S.top==MaxSize-1
  - 栈长：S.top+1
</ul>

#### 另一种实现方式
<ul>

- 初始设置：S.top=0
- 操作方式
  - 进栈：先送值，指针再加1
  - 出栈：指针先减1，再取值
- 状态判断
  - 栈空条件：S.top==0
  - 栈满条件：S.top==MaxSize

>attention: 栈和队列的判空、判满条件，会因实际给的条件不同而变化，下面的代码实现是在栈顶指针初始化为-1的条件下的相应方法，而其他情况则需具体问题具体分析。

</ul>
</ul>

## 顺序栈的基本操作

<ul>

>pro：出/入栈操作的模拟（2009）

- 栈操作的示意图如图3.2所示
  - 图3.2(a)是空栈
  - 图3.2(c)是A、B、C、D、E共5个元素依次入栈后的结果
  - 图3.2(d)是在图3.2(c)之后E、D、C的相继出栈
    - 此时栈中还有2个元素
    - 或许最近出栈的元素C、D、E仍在原先的单元存储着
    - 但top指针已经指向了新的栈顶，元素C、D、E已不在栈中
    - 读者应通过该示意图深刻理解栈顶指针的作用

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/33624a050419102d021d22fcad1a1b9b9ce7d2f891ec502117a6376ac3ae2992.jpg)  
图3.2栈顶指针和栈中元素之间的关系

### 顺序栈基本操作实现
<ul>

#### 初始化
<ul>

void InitStack（SqStack &S){
    s.top  $\scriptstyle{\varepsilon=-1}$  /初始化栈顶指针

</ul>

#### 判栈空

<ul>

bool StackEmpty(SqStack S){
    if(s.top  $==-1$  一 //栈 
        returntrue;
    else
        return false;
</ul>


#### 进栈

<ul>

bool Push(SqStack &S,ElemType x){
    if(s.top  $==$  MaxSize-1) /栈满，报错 
        return false;
    S.data[  $++\mathbb{S}$  .top]  $=\!\mathrm{x}$  /指针先加1，再入栈 
    returntrue;
</ul>

#### 出栈

<ul>

bool Pop（SqStack &S,ElemType &x){
    if(s.top  $==1$  /栈空，报错 
        return false;
    $\scriptstyle{\mathrm{x}}={\mathrm{s}}$  .data[s.top--]; /先出栈，指针再减1 
    returntrue;

</ul>

#### 读栈顶元素

<ul>

bool GetTop（SqStack S,ElemType &x){
    if(s.top  $==-1$  一 /栈空，报错 
        return false;
    $\scriptstyle{\mathrm{x}=\mathrm{S}}$ .data[s.top]; $/\mathrm{x}$ 记录栈顶元素
    return true;


> attention:  

这里的top指的是栈顶元素。于是：
- 进栈操作为S.data $_{[++S.\thinspace t o p]=x}$
- 出栈操作为 $\scriptstyle{\mathrm{x}=\mathrm{S}}$ .data[s.top--]
- 若栈顶指针初始化为s.top $\scriptstyle{\boldsymbol{\mathbf{\varepsilon}}}=0$：
  - 即top指向栈顶元素的下一位置
  - 入栈操作变为S.data $\scriptstyle[S,\,\mathsf{t o p}^{++}\,]\,=\,\mathrm{x}$
  - 出栈操作变为 $\scriptstyle{\mathrm{x}=\mathrm{S}}$ .data[--S.top]
  - 相应的栈空栈满条件也会发生变化
</ul>
</ul>


## 共享栈

<ul>

- 利用栈底位置相对不变的特性
  - 可让两个顺序栈共享一个一维数组空间
  - 将两个栈的栈底分别设置在共享空间的两端
  - 两个栈顶向共享空间的中间延伸

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/1c0004fb22716e3b1a316c37cc6ce28b1dd46cc1c751801d6c9ab8fc25d3ee2e.jpg)  
图3.3两个顺序栈共享存储空间

- 两个栈的栈顶指针都指向栈顶元素
  - top $_{0=-1}$ 时0号栈为空
  - top1 $=$ Max Size 1空
  - 仅当两个栈顶指针相邻（top1-top $_{;0=1}$ ）时，判断为栈满
  - 0号栈进栈时top0先加1再赋值
  - 1号栈进栈时top1先减1再赋值
  - 出栈时则刚好相反

- 共享栈特点：
  - 为了更有效地利用存储空间
  - 两个栈的空间相互调节
  - 只有在整个存储空间被占满时才发生上溢
  - 存取数据的时间复杂度均为 $O(1)$
  - 对存取效率没有影响

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
