<div style="float: left; width: 64%; padding: 1%;">

## 特殊矩阵的压缩存储

<ul>

* 基本概念：
  * 压缩存储：相同元素只分配一个存储空间，零元素不分配空间
  * 特殊矩阵：具有规律分布的相同矩阵元素或零元素的矩阵

### 对称矩阵
> pro：对称矩阵压缩存储的下标对应关系（2018、2020）  

<ul>

* 定义：
  * 满足aij=aji (1≤i,j≤n)的n阶矩阵
* 矩阵划分：
  * 上三角区
  * 主对角线
  * 下三角区
![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/e4256158c828de1e2cb6d0685d7ddee56c4f7c884ab10abb7d55e1bf9d481b93.jpg)  

* 存储方式：
  * 使用一维数组B[n(n+1)/2]存储
  * 只存储下三角部分（含主对角）元素
  * 下标对应关系计算

> attention:  
二维数组A[n][n]和A[0...n-1][0...n-1]的写法是等价的。若数组写为A[1...n][1...n]则说明指定了从下标1开始存储元素。二维数组元素写为a[i][j]，注意数组元素下标i和j通常是从0开始的。矩阵元素通常写为aij或a(i)(j)，注意行号i和列号j是从1开始的。

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
