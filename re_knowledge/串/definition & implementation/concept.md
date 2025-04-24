<div style="float: left; width: 64%; padding: 1%;">

# \* 定义和实现  

<ul>

>字符串is abbreviated to串;

非数值处理的对象基本都是字符串数据

</ul>

## 基本概念

<ul>

### 串的定义

<ul>

- 串（string）是由 <u>零个</u>or<u>多个</u> **字符**组成的**有限**序列
- 记为：$S={}^{'}a_{1}a_{2}\cdots a_{n}{}^{'}\quad(n\geqslant0)$
  - $S$ 是串名，单引号括起来的字符序列是串的值
  - $a_{i}$ can是字母、数字or其他字符
  - 串中字符的个数 $n$ 称为串的长度
    - $n\!=\!0$ 时的串称为空串（用 $\emptyset$ 表示）

</ul>

### 主串与子串关系

<ul>

- 主串
  - include子串的串称为**主串**
  - string中<u>任意</u>多个连续的字符组成的子序列称为该串的**子串**

</ul>

#### 位置概念

<ul>

- 字符位置
  - 某个字符在串中的**序号**称为该字符在串中的<u>位置</u>
- 子串位置
  - 子串在主string中的位置以子串的第1个字符在主串中的位置来表示

</ul>

#### 串相等条件

<ul>

- 两个<u>串</u>**相等**需满足：
  - 两个string的<u>长度相等</u>
  - 每个<u>对应位置</u>的字符both相等

</ul>

### 示例说明

<ul>

eg，有串 $\mathtt{A}\!=$ 'China Beijing'， $\mathtt{B}\!=$ 'Beijing'， $\mathtt{C}{=}$ 'China'，则它们的长度分别为13、7和5。B和C是A的子串，B在A中的位置是7，C在A中的位置是1。  

</ul>

### 特殊说明

<ul>

notice：由一个or多个空格（空格是特殊字符）组成的串称为**空格串**（注意，空格串不是空串），其长度为串中空格字符的个数。

</ul>

### 串&线性表

<ul>

- 逻辑结构：
  - 串的Logical structure和线性表极为相似
  - 区别only在于串的数据对象限定为字符集

- 基本操作(much different):
- 线性表的Basic operation主要：以<u>单个元素</u>作为操作对象
  - 如查找、插入or删除某个元素等
- 串的Basic operation usually以<u>子串</u>作为操作对象
  - 如查找、插入or删除一个子串等 

</ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
