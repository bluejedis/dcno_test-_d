<div style="float: left; width: 64%; padding: 1%;">

## 基本概念  

### 队列的定义  

#### 概述
* 队列（Queue）简称队
  * 是一种操作受限的线性表
  * 只允许在表的一端进行插入
  * 只允许在表的另一端进行删除

#### 基本操作类型
* 入队/进队：向队列中插入元素
* 出队/离队：删除队列中元素
* 操作特性：先进先出（FirstInFirstOut，FIFO）

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/da7e4f84e84162acb3f9824684070eb0b9c7296ec89a63d06b1c5dec814dbf84.jpg)  
图3.5队列示意图  

#### 基本术语
* 队头（Front）
  * 允许删除的一端
  * 又称队首
* 队尾（Rear）
  * 允许插入的一端
* 空队列
  * 不含任何元素的空表

### 队列常见的基本操作  

#### 初始化操作
* InitQueue（&Q）
  * 初始化队列
  * 构造一个空队列Q

#### 数据操作
* EnQueue（&Q，x）
  * 入队操作
  * 若队列Q未满，将x加入
  * 使之成为新的队尾
* DeQueue（&Q，&x）
  * 出队操作
  * 若队列Q非空，删除队头元素
  * 并用x返回
* GetHead（Q，&x）
  * 读队头元素
  * 若队列Q非空，则将队头元素赋值给x

#### 操作限制说明
* 栈和队列是操作受限的线性表
* 不是任何对线性表的操作都可以作为栈和队列的操作
* 不可以随便读取栈或队列中间的某个数据
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
