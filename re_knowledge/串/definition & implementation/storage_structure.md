<div style="float: left; width: 64%; padding: 1%;">

## 存储结构  

<ul>

### 定长顺序存储表示  

<ul>

- 特点：
  - 类似于线性表的顺序存储结构
  - 用一组地址连续的存储单元存储串值字符序列
  - 为每个串变量分配固定长度存储区(定长数组)

</ul>

#### 代码实现

<ul>

#define MAXLEN 255/预定义最大串长为255
typedef struct{ 
    char ch[MAXLEN];//每个分量存储一个字符
    int length;/串的实际长度
)sString;  

</ul>

#### 长度限制

<ul>

- 串长度要求：
  - 实际长度必须 ≤ MAXLEN
  - 超过预定义长度的串值会被截断

</ul>

#### 串长表示方法

<ul>

- 方法一：额外变量存储
  - 用变量len存放串的长度
- 方法二：结束标记
  - 在串值后加"\0"标记
  - 串长为隐含值

</ul>

#### 局限性

<ul>

- 操作限制：
  - 插入、联接等操作可能超过MAXLEN
  - 采用"截断"法处理
- 解决方案：
  - 不限定串长最大长度
  - 采用动态分配方式

</ul>

### 堆分配存储表示  

<ul>

- 基本特征：
  - 使用连续存储单元
  - 存储空间动态分配
  - 在程序执行过程中分配

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/f872b2bd2b132f3ab95a92fe5e40c026db9b3e63ed13be51fbf161f5c6c88850.jpg)  

</ul>

#### 实现方式

<ul>

- C语言实现：
  - 使用"堆"自由存储区
  - 通过malloc()和free()函数管理
- 内存管理：
  - malloc()分配所需存储空间
  - 返回指向起始地址的指针
  - 分配失败返回NULL
  - free()释放已分配空间

</ul>

### 块链存储表示  

<ul>

- 基本概念：
  - 类似线性表的链式存储结构
  - 采用链表方式存储串值

</ul>

#### 结点特点

<ul>

- 存储方式：
  - 可存放单个字符
  - 可存放多个字符
- 结构组成：
  - 结点称为块
  - 整个链表称为块链结构

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/56cc1c53a1bb3c19c28d76a784be4cbd4669057a969be98f64ffd7f9effa73a8.jpg)  

</ul>

#### 实现示例

<ul>

- 结点大小为4的链表：
  - 最后结点不满时用"#"补充
- 结点大小为1的链表

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
