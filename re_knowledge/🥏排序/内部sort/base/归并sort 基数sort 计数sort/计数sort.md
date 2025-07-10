<div style="float: left; width: 64%; padding: 1%;">

### 计数sort

<ul>

#### 基本思想

<ul>

- 不基于比较的sort算法
- 统计小于x的元素个数确定最终位置

</ul>

>**attention**  

计数sort并不在统考大纲的范围内，但其sort思想在历年真题中多次涉及！  

#### 算法实现

<ul>

##### 数据结构

<ul>

- 输入数组A[n]
- 输出数组B[n]
- 计数数组C[k]

</ul>

> pro：计数sort相关的思想和代码的分析（2021）  

##### 算法步骤

<ul>

- 初始化计数数组
  - 统计元素出现次数
  - 累加计算≤x的元素个数
- 从后往前放置元素to正确位置

```c
void CountSort(ElemType A[],ElemType B[],int n,int k){
    int i,C[k];
    for(i=0;i<k;i++)
        C[i]=0;                     //初始化计数数组
    for(i=0;i<n;i++)
        C[A[i]]++;                  //遍历输入数组，统计每个元素出现的次数
                                    //C[A[i]]保存的是等于A[i]的元素个数
    for(i=1;i<k;i++)
        C[i]=C[i]+C[i-1];           //C[x]保存的是小于或等于x的元素个数
    for(i=n-1;i>=0;i--){            //从后往前遍历输入数组
        B[C[A[i]]-1]=A[i];          //将元素A[i]放在输出数组B[]的正确位置上
        C[A[i]]=C[A[i]]-1;
    }
}
```

</ul>

##### 示例演示

<ul>

- 输入数组A[]={2,4,3,0,2,3}的sort过程

</ul>

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/e6d44032ce8506b47ebbb00a8709f6c74ae4f9f3c10eef0ae5cff2a9686fb669.jpg)  

</ul>

#### 性能分析

<ul>

##### 空间efficiency

<ul>

- 空间复杂度O(n+k)或O(k)
- 用空间换时间的策略

</ul>

##### 时间efficiency

<ul>

- 总时间复杂度O(n+k)
- k=O(n)时为O(n)
- k>O(nlogn)时不如比较类sort

</ul>

##### 稳定性

<ul>

- 是稳定的sort算法
- 相同元素相对位置不变

</ul>

##### 适用性

<ul>

- 更适用于<span style="border: 1px solid black; padding: 5px; display: inline-block;">顺序</span>存储
- 适用于整数且范围不太大的序列

</ul>

</ul>

</ul>


</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
