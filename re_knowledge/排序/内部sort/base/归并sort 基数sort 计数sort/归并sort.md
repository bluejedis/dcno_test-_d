<div style="float: left; width: 64%; padding: 1%;">

### 归并sort  

<ul>

>pro：二路归并操作的功能（2022）  

#### 基本概念

<ul>

- 归并sort与基于交换、选择等sort思想不同
- 归并含义：将两个或两个以上的有序表合并成新的有序表
- 基本过程：
  - 将n个记录视为n个有序子表(每个长度为1)
  - 两两归并得到⌈n/2⌉个长度为2或1的有序表
  - 继续两两归并直到合并成一个长度为n的有序表

</ul>

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/365d58fda45f0a53c2d1bd276f956db5d5d2faf07813666f234e33ea5ffff7d7.jpg)  
图8.9二路归并sort示例  

> pro：（算法题）归并sort思想的应用（2011）  

#### Merge操作实现

<ul>

##### 功能描述

<ul>

- 将前后相邻的两个有序表归并为一个有序表
- 两段有序表位于A[low..mid]和A[mid+1..high]

</ul>

##### 实现步骤

<ul>

- 复制数据到辅助数组B
- 比较B中两段数据
- 将较小值放入A中
- 处理剩余数据

</ul>

```c
ElemType *B=(ElemType *)malloc((n+1)*sizeof(ElemType)); //辅助数组B
void Merge(ElemType A[],int low,int mid,int high){
//表 A 的两段 A[low..mid] 和 A[mid+1..high] 各自有序，将它们合并成一个有序表
    int i,j,k;
    for(k=low;k<=high;k++)
        B[k]=A[k];                      //将A 中所有元素复制到 B 中
    for(i=low,j=mid+1,k=i;i<=mid&&j<=high;k++){
        if(B[i]<=B[j])                  //比较 B 的两个段中的元素
            A[k]=B[i++];                //将较小值复制到 A 中
        else
            A[k]=B[j++];
    }
    while(i<=mid) A[k++]=B[i++];    //若第一个表未检测完,复制
    while(j<=high) A[k++]=B[j++];   //若第二个表未检测完,复制
}
```

</ul>

>**attention**  

在上面的代码中，最后两个while循环只有一个会执行  

#### 归并sort的实现

<ul>

##### 一趟归并操作

<ul>

- 调用⌈n/2h⌉次merge()算法
- 将相邻长度为h的有序段两两归并
- 得到长度为2h的有序段
- 需要进行logn趟

</ul>

##### 递归实现

<ul>

###### 分解阶段

<ul>

- 将n个元素的待sort表分成两个n/2元素的子表
- 递归对子表进行sort

</ul>

###### 合并阶段

<ul>

- 合并两个已sort的子表得到sort结果

</ul>

```c
void MergeSort(ElemType A[],int low,int high){
    if(low<high){
        int mid=(low+high)/2;       //从中间划分两个子序列
        MergeSort(A,low,mid);       //对左侧子序列进行递归排序
        MergeSort(A,mid+1,high);    //对右侧子序列进行递归排序
        Merge(A,low,mid,high);      //归并
    }
} 
```

</ul>

</ul>

> pro： 归并sort和插入sort的对比（2017）  

#### 性能分析

<ul>

##### 空间efficiency

<ul>

- Merge操作需要n个辅助单元
- 空间复杂度为O(n)

</ul>

##### 时间efficiency

<ul>

- 每趟归并时间复杂度O(n)
- 需要⌈log₂n⌉趟归并
- 总时间复杂度O(nlog₂n)

</ul>

##### 稳定性

<ul>

- 是稳定的sort算法
- Merge操作不改变相同关键字记录的相对次序

</ul>

##### 适用性

<ul>

- 适用于顺序存储和链式存储的线性表

</ul>

</ul>

>**attention**  

一般而言，对于 $N$ 个元素进行 $k$ 路归并sort时，sort的趟数 $m$ 满足 $k^{m}\!=\!N$ ，thus $m\!=\!\log_{k}\!N$ 又考虑到 $m$ 为整数，thus $\scriptstyle m\,=\,\lceil\log_{k}N\rceil_{\circ}$ 这和前面的二路归并sort算法是一致的。

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
