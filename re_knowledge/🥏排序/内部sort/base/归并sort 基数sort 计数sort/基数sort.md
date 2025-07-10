<div style="float: left; width: 64%; padding: 1%;">

### 基数sort  

<ul>

#### 基本概念

<ul>

- 一种特别的sort算法
  - 不基于比较和移动进行sort
  - 基于关键字各位的大小进行sort
  - 借助<span style="border: 1px solid black; padding: 5px; display: inline-block;">多关键字</span>sort思想对单逻辑关键字进行sort

</ul>

#### 算法原理

<ul>

##### 关键字组成

<ul>

- 长度为n的线性表中每个结点aj的关键字由d元组(kj^(d-1), kj^(d-2),..., kj^1, kj^0)组成
- 满足0≤kj^i≤r-1 (0≤j<n,0≤i≤d-1)
  - kj^(d-1)为最主位关键字
  - kj^0为最次位关键字

</ul>

##### 实现方法

<ul>

- 最高位优先（MSD）法
  - 按关键字位权重递减依次划分子序列
  - 最后连接成有序序列
- 最低位优先（LSD）法
  - 按关键字位权重递增依次sort
  - 最后形成有序序列

</ul>

</ul>

#### sort过程

<ul>

##### 基本步骤

<ul>

- 使用r个队列Q0,Q1,...,Qr-1
- 对i=0,1,...,d-1依次进行：
  - 分配：
    - 初始化空队列
    - 根据关键字kj^i将aj放入对应队列
  - 收集：
    - 将各队列节点首尾相接形成新序列

</ul>

##### 实例演示

<ul>

- 对10个记录进行sort示例
  - 关键字为1000以下正整数
  - 基数r=10
  - 需要10个链队列
  - 每个关键字由3位子关键字构成

</ul>

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/48cc62165ce2360ed01930db009972b6262a390392448a6089225dc7f219ffea.jpg)  
![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/9c6f2bf6f54e66bb9877535bef33f0c0f8826a93ead82956fa1cc97ee0d7f7ec.jpg)  
![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/16003a2547311992cc50f4c5ee3d857229a213f2dc465318c889f2714a206b93.jpg)  

</ul>

#### 性能分析

<ul>

##### 空间efficiency

<ul>

- 需要r个队列的辅助存储空间
- 空间复杂度为O(r)

</ul>

> pro：元素的移动次数与序列初态无关的sort算法（2015）  

##### 时间efficiency

<ul>

- 需要d趟分配和收集操作
- 一趟分配时间复杂度O(n)
- 一趟收集时间复杂度O(r)
- 总时间复杂度O(d(n+r))
- 与序列初始状态无关

</ul>

##### 稳定性

<ul>

- 是稳定的sort算法
- 不会交换相同关键字的相对位置

</ul>

##### 适用性

<ul>

- 适用于顺序存储和链式存储的线性表

</ul>

</ul>


</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
