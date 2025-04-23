<div style="float: left; width: 64%; padding: 1%;">
    
## <span style="color: silver;"><span style="color: LightSkyBlue;">顺序</span>~

<ul>

### <span style="color: silver;">concept

- 又称<span style="color: orange;">线性</span><span style="color: Gold;">search</span>
- 适用范围：
  - <span style="color: LightSkyBlue;">顺序</span>表：通过数组下标递增扫描
  - <span style="color: RoyalBlue;">链</span>表：通过指针next扫描

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
    ElemType *elem;
    int TableLen;
}SSTable;

int <span style="color: Gold;">search</span>_Seq(SSTable ST,ElemType key){
    ST.elem[0]=key;
    for(int i=ST.TableLen;ST.elem[i]!=key;--i);
    return i;
}
```

</ul>

<ul>

#### <span style="color: silver;"><span style="color: Gold;">性能</span>分析

- <span style="color: Gold;">search</span>成功时<span style="color: LightSkyBlue;">平均</span>长度：
  - $\operatorname{ASL}_{\mathfrak{h}(n;i)}=\sum_{i=1}^{n}P_{i}(n-i+1)$
  - 当Pi=1/n时：$\operatorname{PSL}_{n|k\rangle n|}{=}{\frac{n+1}{2}}$
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
  - <span style="color: LightSkyBlue;">平均</span>长度：$\operatorname{ASL}_{\mathcal{K}:n\times l}=\!\!\sum_{j=1}^{n}q_{j}(l_{j}-1)\!=\!\frac{1\!+2\!+\!\cdots\!+n\!+\!n}{n\!+\!1}\!=\!\frac{n}{2}\!+\!\frac{n}{n\!+\!1}$
  - 当n=6时：ASL=3.86

</ul>

<ul>

#### <span style="color: silver;">attention

- 思想与<span style="color: Gold;">折</span><span style="color: gray;">半</span><span style="color: Gold;">search</span>不同
  - <span style="color: RoyalBlue;">链</span>式存储结构
  - 折半~only<span style="color: LightSkyBlue;">顺序</span>存储结构

</ul>

</ul>

</ul>

<ul>


</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
