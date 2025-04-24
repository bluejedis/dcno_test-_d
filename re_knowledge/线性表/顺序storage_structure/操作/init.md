<div style="float: left; width: 64%; padding: 1%;">

## 顺序表上基本操作的实现  

<ul>

>pro：顺序表上操作的时间复杂度分析（2023）这里仅讨论顺序表的初始化、插入、删除和按值查找，其他基本操作的算法都很简单。  

> attention: 在各种操作的实现中（包括严蔚敏老师撰写的教材），往往可以忽略边界条件判断、变量定义、内存分配不足等细节，即不要求代码具有可执行性，而重点在于算法的思想。  

### 顺序表的初始化

<ul>

#### 静态分配初始化

<ul>

- 声明时已分配数组空间
- 只需设置长度为0

/SqListL;/声明一个顺序表
void InitList(SqList &L){ 
    L.length = 0  //顺序表初始长度为0

</ul>

#### 动态分配初始化

<ul>

- 分配预定义大小的数组空间
- 设置长度为0
- MaxSize指示当前存储空间大小

void InitList（SeqList &L){
    L.data = （ElemType*）malloc（MaxSize*sizeof（ElemType））;
    L.length = 0  /顺序表初始长度为0 
    L.MaxSize = InitSize;/初始存储容量

</ul>

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
