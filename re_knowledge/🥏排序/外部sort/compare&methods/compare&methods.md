<div style="float: left; width: 64%; padding: 1%;">

## 概述

<ul>

- 外部sort可能会考查相关概念、方法和sort过程
- 外部sort的算法比较复杂，不会在算法设计上进行考查
- 主要内容：
  - 外部sort指大文件sort，待sort记录存储在外存中，无法一次性装入内存
  - 减少平衡归并中外存读/写次数的方法：
    - 增大归并路数
    - 减少归并段个数
  - 利用败者树增大归并路数
  - 利用置换-选择sort增大归并段长度来减少归并段个数
  - 由长度不等的归并段进行多路平衡归并，需要构造最佳归并树

</ul>

## 基本概念

<ul>

- 内部sort：在内存中进行的sort算法
- 外部sort：
  - 适用于大文件sort
  - 记录存储在外存上
  - 需要分批调入内存进行sort
  - 需要多次内存和外存交换

</ul>

## 方法

<ul>

### 基本原理

<ul>

- 文件存储特点：
  - 按块存储在磁盘上
  - 操作系统按块读/写
  - 磁盘读/写时间远超内存运算时间
  - 主要考虑I/O次数

</ul>

> pro：对大文件sort时使用的sort算法（2016）  

### sort过程

<ul>

- 两个阶段：
  1. 初始化阶段：
     - 根据内存缓冲区大小分割文件
     - 对子文件进行内部sort
     - 生成有序子文件（归并段/顺串）
  2. 归并阶段：
     - 对归并段逐趟归并
     - 直至得到完整有序文件

</ul>

### 归并实现

<ul>

- 内存分配：
  - 三个缓冲区
    - 两个输入缓冲区
    - 一个输出缓冲区

</ul>

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/f9dfc2273b2657ab8f22bac4053500f6f3c968af70843c709cd6de6d27e0e7f8.jpg)  
图8.14二路归并  

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/594c62b9eed6c74fbcd2ef228dc89133d1f7dacc1faac7b8cf3699861e02d96b.jpg)  
图8.15二路平衡归并的sort过程  

### 时间开销

<ul>

- 总时间组成：
  - 内部sort时间
  - 外存信息读/写时间
  - 内部归并时间
- 优化重点：
  - 减少I/O次数
  - 以磁盘块为单位读写

</ul>

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/29ffd4a87f89e3a71844bdb43087db397877ef3872bcda905c7c5cc68854e819.jpg)  
图8.164路平衡归并的sort过程  

### 优化策略

<ul>

- 增大归并路数k：
  - 减少归并趟数
  - 减少磁盘I/O次数
- 减少初始归并段个数r：
  - 降低归并树高度
  - 减少归并趟数S

</ul>

</ul>


</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
