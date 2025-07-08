<div style="float: left; width: 64%; padding: 1%;">

# 线性表的顺序表示  

<ul>

## 顺序表的定义  

<ul>

### 基本概念

<ul>

- （算法题）顺序表的应用（2010、2011、2018、2020）
- 线性表的顺序存储又称顺序表
  - 用连续存储单元依次存储数据元素
  - 逻辑相邻元素在物理位置上也相邻
  - 第1个元素存储在起始位置
  - 第i个元素后紧接第i+1个元素
  - i为元素ai的位序
- 特点：表中元素的逻辑顺序与物理顺序相同

</ul>

### 存储结构

<ul>

- 假设起始位置为Loc(A)
- sizeof(ElemType)为每个元素存储空间大小
- 存储结构如图所示：

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/be429ac9c6545cfdfb42d2e69bd07d28e3670d31c3050a3298f9ba85cd4fd2f5.jpg)  

#### 随机存取特性

<ul>

- 每个元素位置与起始位置相差固定常数
- 可以随机存取任意元素
- 通常用数组描述顺序存储结构

> attention: 
线性表中元素的位序是从1开始的，而数组中元素的下标是从0开始的。

</ul>

</ul>

### 存储方式

<ul>

#### 静态分配

<ul>

- 特点：
  - 数组大小固定
  - 空间事先固定
  - 可能产生溢出
- 代码实现：

#define MaxSize 50//定义线性表的最大长度
typedef struct{
    ElemType data[MaxSize];//顺序表的元素
    int length;//顺序表的当前长度
}SqList; //顺序表的类型定义

```c
#define MaxSize 50              //定义线性表的最大长度
typedef struct{
    ElemType data[MaxSize];   //顺序表的元素
    int length;               //顺序表的当前长度
}SqList;                        //顺序表的类型定义
```

</ul>

#### 动态分配

<ul>

- 特点：
  - 运行时分配空间
  - 空间不足时可扩充
  - 无需一次性划分所有空间
- 代码实现：

```c
#define InitSize 100            //表长度的初始定义
typedef struct{
    ElemType *data;           //指示动态分配数组的指针
    int MaxSize,length;       //数组的最大容量和当前个数
}SeqList;                        //动态分配数组顺序表的类型定义
```

C 的初始动态分配语句为



*C++的初始动态分配语句为*



- 初始动态分配语句：
  - C语言：
```c
L.data=(ElemType*)malloc(sizeof(ElemType)*InitSize);
```
  - C++：
```cpp
L.data=new ElemType[InitSize];
```
> attention: 

动态分配并不是链式存储，它同样属于顺序存储结构，物理结构没有变化，依然是随机存取方式，只是分配的空间大小可以在运行时动态决定。  

</ul>

</ul>

### 优缺点分析

<ul>

#### 优点

<ul>

- 可进行随机访问，O(1)时间找到指定元素
- 存储密度高，每个结点只存储数据元素

</ul>

#### 缺点

<ul>

- 插入删除需要移动大量元素
  - 插入平均移动n/2个元素
  - 删除平均移动(n-1)/2个元素
- 需要连续存储空间，不够灵活

</ul>

</ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
