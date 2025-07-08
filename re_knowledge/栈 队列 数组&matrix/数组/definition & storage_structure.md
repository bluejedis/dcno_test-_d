<div style="float: left; width: 64%; padding: 1%;">

## 数组的定义  

<ul>

* 数组是由n(n≥1)个相同类型的数据元素构成的有限序列
  * 每个数据元素称为一个数组元素
  * 每个元素在n个线性关系中的序号称为该元素的下标
  * 下标的取值范围称为数组的维界

* 数组与线性表的关系：
  * 数组是线性表的推广
  * 一维数组可视为一个线性表
  * 二维数组可视为其元素是定长数组的线性表
  * 数组一旦被定义，其维数和维界就不再改变
  * 操作仅限于：
    * 初始化和销毁
    * 存取元素
    * 修改元素

</ul>

## 数组的存储结构

<ul>

* 存储特点：
  * 使用计算机语言中的数组数据类型
  * 所有元素在内存中占用连续存储空间

* 一维数组存储：
  * 存储结构关系式：
    * \[
LOC(a_i) = LOC(a_0) + i \times L \quad (0 \leq i < n)
\]
    * L是每个数组元素所占的存储单元

* 多维数组存储：
  * 两种映射方法：
    * 按行优先
    * 按列优先
  * 二维数组<span style="border: 1px solid black; padding: 5px; display: inline-block;">按行</span>优先存储：
    * 存储结构关系式：\[
LOC(a_{i,j}) = LOC(a_{0,0}) + [i \times (h_2 + 1) + j] \times L
\]
    ![image](https://bluejedis.github.io/picx-images-hosting/DS/image.7eh2387438.png)
   
  * 按<span style="border: 1px solid black; padding: 5px; display: inline-block;">列</span>优先存储：
    * 存储结构关系式：\[
LOC(a_{i,j}) = LOC(a_{0,0}) + [j \times (h_1 + 1) + i] \times L
\]
  ![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/431323970be87b0380983b68a2fdb2ce80b5cbf7a18caf848ab1a8260d81a826.jpg) 
</ul>



</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
