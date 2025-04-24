<div style="float: left; width: 64%; padding: 1%;">

### 稀疏矩阵
> pro：存储稀疏矩阵需要保存的信息（2023）  

<ul>

* 定义：
  * 非零元素个数t << 矩阵元素总数s的矩阵

* 存储特点：
  * 仅存储非零元素
  * 需存储元素的行列位置
  * 使用三元组(行标i，列标j，值aij)表示
![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/b0c42fe0d8732a593781e47414cea74094d463474100aa7492a58b47b74fc271.jpg)  

> pro：适合稀疏矩阵压缩存储的存储结构（2017）  

* 存储结构：
  * 可使用数组存储
  * 可使用十字链表存储
  * 需保存：
    * 三元组表
    * 矩阵行数
    * 矩阵列数
    * 非零元素个数

</ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
