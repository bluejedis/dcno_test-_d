<div style="float: left; width: 64%; padding: 1%;">


## <span style="color: silver;">concept

<ul>

### <span style="color: silver;">n.

- <span style="color: RoyalBlue;">散列</span><span style="color: green;">函数</span>(哈希<span style="color: green;">函数</span>)
  - 定义：把<span style="color: Gold;">search</span>表中的关键字映射成对应地址的<span style="color: green;">函数</span>
  - 表示：$\operatorname{Hash}(\ker)=$Addr
  - 地址类型：数组下标、索引或内存地址等

- <span style="color: Gold;">冲突</span>
  - 定义：不同关键字映射到同一地址
  - 同义词：发生<span style="color: Gold;">冲突</span>的不同关键字
  - 处理：
    - 需设计良好的<span style="color: RoyalBlue;">散列</span><span style="color: green;">函数</span>减少<span style="color: Gold;">冲突</span>
    - 设计<span style="color: Gold;">冲突</span>处理方法

- <span style="color: RoyalBlue;">散列</span><span style="color: gray;">表</span>(哈希表)
  - 定义：根据关键字直接进行访问的数据结构
  - 特点：建立关键字和存储地址的直接映射
  - 性能：理想情况下<span style="color: Gold;">search</span>时间复杂度为O(1)

</ul>

<ul>

### <span style="color: silver;"><span style="color: Lime;">构造</span>方法

<ul>

#### <span style="color: silver;"><span style="color: Lime;">构造</span>原则

- 定义域必须包含全部关键字
- 地址分布应尽可能均匀
- 计算过程应尽量简单

</ul>

<ul>

#### 直接定址法

- 方法：取关键字的线性<span style="color: green;">函数</span>值为<span style="color: RoyalBlue;">散列</span>地址
- 优点：计算简单，无<span style="color: Gold;">冲突</span>
- 适用：关键字分布基本连续的情况
- 缺点：关键字不连续时浪费空间

</ul>

<ul>

#### 除留余数法

- 方法：$H(\mathrm{kcy})=\mathrm{kcy}\,\%\,p$
- 要点：选择合适的p值
  - p NOT＞表长m
  - p 最接近or等于m的质数
- 目标：使关键字等概率映射到任意地址

</ul>

<ul>

#### 数字分析法

- 适用：已知关键字集合
- 原理：
  - 分析r进制数各位上数码出现频率
  - 选取分布均匀的位作为<span style="color: RoyalBlue;">散列</span>地址
- 局限：更换关键字需重构<span style="color: RoyalBlue;">散列</span><span style="color: green;">函数</span>

</ul>

<ul>

#### 平方取中法

- 方法：取关键字平方值的中间几位
- 特点：
  - <span style="color: RoyalBlue;">散列</span>地址与关键字每位都相关
  - 地址分布较均匀
- 适用：关键字各位取值不均匀或位数较小

</ul>

<ul>

#### 方法选择

- 没有最优的通用方法
- 需根据具体关键字集合情况选择

</ul>

</ul>

</ul>

<ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
