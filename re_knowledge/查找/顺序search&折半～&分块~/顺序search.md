 <span style="color: silver;">
<div style="float: left; width: 64%; padding: 1%;">
    
## <span style="color: silver;"><span style="color: LightSkyBlue;">顺序</span>~

<ul>

### <span style="color: silver;">concept

- 又称<span style="color: orange;">线性</span><span style="color: Gold;">search</span>
- 适用范围：
  - <span style="color: LightSkyBlue;">顺序</span>表：通过 <u>数组下标</u> 递增扫描
  - <span style="color: RoyalBlue;">链</span>表：通过 <u>指针next</u> 扫描

</ul>

<ul>

### <span style="color: silver;"><span style="color: gray;">一般</span><span style="color: orange;">线性</span>表的顺序<span style="color: Gold;">search</span>

<ul>

#### <span style="color: silver;">基本思想

- from<span style="color: orange;">线性</span>表一<span style="color: LightSkyBlue;">端</span>开始逐个检查关键字
  - find<span style="color: GreenYellow;">满足</span>条件元素 → return位置
- till表另一端not find → return失败

</ul>

<ul>

#### <span style="color: LightSkyBlue;">算法

```c
typedef struct{
    ElemType *elem;     //动态数组基址
    int TableLen;       //表的长度
}SSTable;

int Search_Seq(SSTable ST, ElemType key){
    ST.elem[0]=key;                         //“哨兵”
    for(int i=ST.TableLen;ST.elem[i]!=key;--i);  //从后往前找
    return i;   //若查找成功，则返回元素下标；若查找失败，则返回 0
}
```

</ul>

<ul>

#### <span style="color: silver;"><span style="color: Gold;">性能</span>分析

- <span style="color: Gold;">search</span>成功时<span style="color: LightSkyBlue;">平均</span>长度：
  - $\operatorname{ASL}_{成功}=\sum_{i=1}^{n}P_{i}(n-i+1)$[^1]

  - 当Pi=1/n时：
    - (namely 每个元素的查找概率)[^2]
    - $\operatorname{ASL}_{成功}{=}{\frac{n+1}{2}}$
- ~失败时：ASL=n+1

</ul>

<ul>

#### <span style="color: silver;"><span style="color: LightSkyBlue;">优</span><span style="color: GreenYellow;">缺</span>点

- 缺点：n较大时效率低
- 优点：
  - 存储方式灵活
  - 无序序要求
  - 适用于链表

</ul>

</ul>

<ul>

### <span style="color: silver;"><span style="color: GreenYellow;"><span style="color: gray;">有</span><span style="color: LightSkyBlue;">序</span></span><span style="color: orange;">线性</span>表的顺序<span style="color: Gold;">search</span>

<ul>

#### <span style="color: silver;">Feature

- 提前know表is<u>关键字<span style="color: gray;">有</span><span style="color: LightSkyBlue;">序</span></u>
- False:
  - <span style="color: Gold;">search</span>失败时can<span style="color: GreenYellow;">提前</span>返回
  - 可降低<span style="color: Gold;">search</span>失败的<span style="color: LightSkyBlue;"><span style="color: LightSkyBlue;">平均</span></span><span style="color: gray;">长度

> pro：<span style="color: gray;">有</span><span style="color: LightSkyBlue;">序</span>线性表的顺序<span style="color: Gold;">search</span>的应用（2013）

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/b9a556e5c788039f2fe0a08be26af8476e380c1fcd30a762adcbe9951bfa13c7.jpg)`
↑<span style="color: gray;">有</span><span style="color: LightSkyBlue;">序</span>顺序表上的顺序查找判定树

</ul>

<ul>

#### <span style="color: silver;"><span style="color: Gold;">性能</span>分析

- <span style="color: Gold;">search</span><span style="color: Gold;">成功</span>：same as<span style="color: gray;">一般</span>线性表
- <span style="color: Gold;">search</span><span style="color: GreenYellow;">失败</span>：
  - $\operatorname{ASL}_{false}=\!\!\sum_{j=1}^{n}q_{j}(l_{j}-1)$[^3]
    - $$=\!\frac{1\!+2\!+\!\cdots\!+n\!+\!n}{n\!+\!1}$$[^4]
    - $=\!\frac{n}{2}\!+\!\frac{n}{n\!+\!1}$
  - 当n=6时：ASL=3.86

</ul>

<ul>

#### <span style="color: silver;">attention

- 思想与<span style="color: Gold;">折</span><span style="color: gray;">半</span><span style="color: Gold;">search</span>不同
  - could have <span style="color: RoyalBlue;">链</span>式存储结构
  - 折半~only<span style="color: LightSkyBlue;">顺序</span>存储结构

</ul>

</ul>

</ul>

<ul>


</div>
<div style="float: right; width: 26%; padding: 1%;">


![2-210R0143451633](https://bluejedis.github.io/picx-images-hosting/ds/2-210R0143451633.3golp8087p.gif)

</div>
<div style="clear: both;"></div>

[^1]: 
    - 通式:  $\text{ASL}_{\text{success}} = \sum_{i=1}^{n} p_i \cdot d_i$
      - $d_i$ 是该元素的深度（比较次数）
    - 此处:
      - $=P_1 \cdot n + P_2 \cdot (n-1) + P_3 \cdot (n-2) + \cdots + P_n \cdot 1$
        - 即 加权求和， n为定值， i为变量

[^2]: - usually, 查找表中记录的P并不相等



[^3]:
    - $ q_j $：落入第 $ j $ 个区间的概率
      - if 查找概率same→ $ q_j = \frac{1}{n+1} $
    - $ l_j $：查找该失败位置needed比较次数（usually =该失败位置的路径长度）
    - $ l_j - 1 $：有时调整计算方式
[^4]: - 推导:🔎//待sum
      - 假设均匀概率和平衡树结构