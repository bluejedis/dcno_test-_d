 <span style="color: silver;">

<div style="float: left; width: 64%; padding: 1%;">

## <span style="color: Goldenrod;">平衡</span><span style="color: Gold;">二叉</span><span style="color: green;">树</span>

<ul>

### <span style="color: silver;">定义

<ul>

#### <span style="color: silver;">concept

- 为了避免
  - 树的<span style="color: LightSkyBlue;">高度</span>增长过快
    - 降低二叉排序树的性能
- 规定：
  - 任意node的左、右子树<span style="color: LightSkyBlue;">高度</span><span style="color: Gold;">差</span>的绝对值≤1
  - 这样的二叉树称为<span style="color: Goldenrod;">平衡</span><span style="color: Gold;">二叉</span><span style="color: green;">树</span>（Balanced BinaryTree）或AVL树
- <span style="color: Goldenrod;">平衡</span>因子：
  - node左子树与右子树的<span style="color: LightSkyBlue;">高度</span><span style="color: Gold;">差</span>
  - 值only might -1、0或1

> pro：<span style="color: Goldenrod;">平衡</span><span style="color: Gold;">二叉</span><span style="color: green;">树</span>的定义（2009）

</ul>

<ul>

#### <span style="color: gray;">完整<span style="color: silver;">定义

- special:一棵空树
- 具有以下性质的二叉树：
  - 左子树和右子树都是<span style="color: Goldenrod;">平衡</span><span style="color: Gold;">二叉</span><span style="color: green;">树</span>
  - 左子树和右子树的<span style="color: LightSkyBlue;">高度</span><span style="color: Gold;">差</span>的绝对值≤1

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/42460a711e8a2a7bcbc0a975d83fd52c42972810cdf1ff0354c8c9d9ea7aa463.jpg)`  
<span style="color: Goldenrod;">平衡</span><span style="color: Gold;">二叉</span><span style="color: green;">树</span>和<span style="color: gray;">不</span>~

</ul>

</ul>

<ul>

### <span style="color: GreenYellow;">插入</span>

<ul>

#### <span style="color: silver;">基本思想

- <span style="color: GreenYellow;">插入</span>（或删除）node时：
  -  check <span style="color: GreenYellow;">插入</span>路径上的node whether平衡
  - if imbalance：
    - find most near |<span style="color: Goldenrod;">平衡</span><span style="color: LightSkyBlue;">因子</span>| ＞1 'node_A
      - adjust以A为root的子树
      - keep二叉排序树特性


> pro：<span style="color: Goldenrod;">平衡</span><span style="color: Gold;">二叉</span><span style="color: green;">树</span>中<span style="color: GreenYellow;">插入</span>操作的特点（2015）


 each adjustment: min 不平衡 subtree
 - 以<span style="color: GreenYellow;">插入</span>road上 离<span style="color: GreenYellow;">插入</span>node最近的|<span style="color: Goldenrod;">平衡</span><span style="color: LightSkyBlue;">因子</span>| ＞1的node as 根的subtree


![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/2209bb6cb24b8548ca118f9d5f40aa8899f7ed2e20e83c7fe0c0621ee7b842db.jpg)
图7.10最小不平衡子树(虚线框)

> pro：<span style="color: Goldenrod;">平衡</span><span style="color: Gold;">二叉</span><span style="color: green;">树</span>的<span style="color: GreenYellow;">插入</span>及调整操作的实例（2010、2019、2021）

</ul>

<ul>

####  ❓⚠️<span style="color: silver;">调整规律[^1]

<ul>
❓为什么 单旋转 add node的标号是H+1 ; 在双旋转中却是H-1?
找个详细的描述动图

#####  <span style="color: silver;"> <span style="color: lightgray;">LL</span> 平衡旋转（(to)右单♻️）

- 原因：在node_A ' 左child(L)' 左subtree(L)上<span style="color: GreenYellow;">插入</span>新node
- 过程：
  - A的平衡因子由1增至2
  - B向右上旋转代替A成为根node
  - A向右下旋转成为B的右孩子
  - B的原右子树作为A的左子树

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/0b95eff2c046b43bb6a18bc9a41beacc9de133dbf00206769ee68eb40f6d13e7.jpg)
图7.11LL平衡旋转

</ul>

<ul>

#####  <span style="color: silver;"><span style="color: gray;">RR</span> （(to)左单🔄）

- 原因：在nodeA的右孩子(R)的右子树(R)上<span style="color: GreenYellow;">插入</span>新node
- 过程：
  - A的平衡因子由-1减至-2
  - B向左上旋转代替A成为根node
  - A向左下旋转成为B的左孩子
  - B的原左子树作为A的右子树

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/5619c6d8436c1be38b63d259dcc65e0d4dfdd684c7e61b46edda1f39de83300f.jpg)
图7.12RR平衡旋转

</ul>

<ul>

#####  <span style="color: silver;"><span style="color: lightgray;">L</span><span style="color: gray;">R</span>平衡旋转（先🔄后♻️双旋转）

- 原因：在A的左孩子(L)的右子树(R)上<span style="color: GreenYellow;">插入</span>新node
- 过程：
  - A的平衡因子由1增至2
  - 先将C向左上旋转提升到B的位置
  - 再将C向右上旋转提升到A的位置

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/e7462a89cd7274f34abe2309c0d8eedb6ed3d046096c03916695558689e50a9f.jpg)
图7.13LR平衡旋转

</ul>

<ul>

#####  <span style="color: silver;"><span style="color: gray;">R</span><span style="color: lightgray;">L</span>平衡旋转（先♻️后🔄）

- 原因：在A的右孩子(R)的左子树(L)上<span style="color: GreenYellow;">插入</span>新node
- 过程：
  - A的平衡因子由-1减至-2
  - 先将C向右上旋转提升到B的位置
  - 再将C向左上旋转提升到A的位置

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/044e9dac3e9118af06383caa4ab6770b19e9168a05e12eabac22b4702037505f.jpg)`  
图7.14RL平衡旋转

> notice: 

LR和RL旋转时，新node究竟是<span style="color: GreenYellow;">插入</span>C的左子树还是<span style="color: GreenYellow;">插入</span>C的右子树不影响旋转过程，而图7.13和图7.14中以<span style="color: GreenYellow;">插入</span>C的左子树中为例。

> pro：<span style="color: Lime;">构造</span><span style="color: Goldenrod;">平衡</span><span style="color: Gold;">二叉</span><span style="color: green;">树</span>的过程（2013）

</ul>

</ul>

<ul>

#### <span style="color: Lime;">构造</span>

- 关键字序列：15，3，7，10，9，8
- 过程：
  - <span style="color: GreenYellow;">插入</span>7后：
    - 最小不平衡子树根为15
    - 执行LR旋转
  - <span style="color: GreenYellow;">插入</span>9后：
    - 最小不平衡子树根为15
    - 执行LL旋转
  - <span style="color: GreenYellow;">插入</span>8后：
    - 最小不平衡子树根为7
    - 执行RL旋转

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/093f0bfc9d39ea0cacad9cfef59f6edf59790e2ed7a6692f2ea8792f99c3b8bf.jpg)`  
图7.15<span style="color: Goldenrod;">平衡</span><span style="color: Gold;">二叉</span><span style="color: green;">树</span>的生成过程

</ul>

</ul>

<ul>

### <span style="color: gray;">删除</span>

<ul>

#### STEP

- 用BST way 删除node_w
- if imbalance：
  - 从w向上回溯 找第一个不平衡node_z
  - y为z的最高孩子node
  - x为y的最高孩子node
- 对以z为根的子树进行平衡调整：
  - LL情况：y是z左孩子，x是y左孩子
  - LR情况：y是z左孩子，x是y右孩子
  - RR情况：y是z右孩子，x是y右孩子
  - RL情况：y是z右孩子，x是y左孩子



#### 与<span style="color: GreenYellow;">插入</span>操作的区别

- <span style="color: GreenYellow;">插入</span>操作：
  - 仅需对z为根的子树调整
- 删除操作：
  - 调整z为根的子树后
  - 若<span style="color: LightSkyBlue;">高度</span>减1，可能需要继续向上调整
  - 可能一直调整到根node



####  <span style="color: silver;">eg

- 以删除node32为例：
  - 32为叶node直接删除
  - 找到第一个不平衡node44(z)
  - 78为y，50为x
  - 满足RL情况，执行先右后左双旋转

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/7583531b4059bdd4839026ef84e33d80a0e80d188229f9a181a9205146f44d1b.jpg)`  
图7.16<span style="color: Goldenrod;">平衡</span><span style="color: Gold;">二叉</span><span style="color: green;">树</span>的删除

</ul>

</ul>

<ul>

### <span style="color: Gold;">search</span>

> pro: 指定条件下<span style="color: Goldenrod;">平衡</span><span style="color: Gold;">二叉</span><span style="color: green;">树</span>的node数的分析（2012）

<ul>

####  <span style="color: silver;">process

- same as BST
- 比较次数 ≤ 树的深度

</ul>

<ul>

#### <span style="color: silver;">node数 min

- 深度为h的最少node数 $n_h$：
  - n_0=0, n_1=1, n_2=2
  - $n_h=n_{h-2}+n_{h-1}+1$
    - pic中 推导：n3=4, n4=7, n5=12,...
- 含n个node的<span style="color: Goldenrod;">平衡</span><span style="color: Gold;">二叉</span><span style="color: green;">树</span>：
  - 最大深度为$O(log_2n)$
  - <span style="color: LightSkyBlue;">平均</span><span style="color: Gold;">search</span>效率为O(log2n)

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/05527187cb555c4a8c169a1c9bb747cea9d526708b08d8e44da08c7188104059.jpg)`  
图7.17node个数n最少的<span style="color: Goldenrod;">平衡</span><span style="color: Gold;">二叉</span><span style="color: green;">树</span>

> notice: 

used in 求解给定node数的 ~ 的<span style="color: Gold;">search</span>所需的最多比较次数 or树的最大<span style="color: LightSkyBlue;">高度</span>）。
- such as 在含有12个node的<span style="color: Goldenrod;">平衡</span><span style="color: Gold;">二叉</span><span style="color: green;">树</span>中<span style="color: Gold;">search</span>某个node的最多比较次数？

</ul>

<ul>

#### <span style="color: silver;">node数 max

- 即 满二叉树

</ul>

</ul>

</ul>

<ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

- <span style="color: Goldenrod;">平衡</span>因子：
  - node左子树与右子树的<span style="color: LightSkyBlue;">高度</span><span style="color: Gold;">差</span>
  - 值only might -1、0或1

- <span style="color: GreenYellow;">插入</span>
- 离<span style="color: GreenYellow;">插入</span>node最近的|<span style="color: Goldenrod;">平衡</span><span style="color: LightSkyBlue;">因子</span>| ＞1的node as 根的子树


![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/2209bb6cb24b8548ca118f9d5f40aa8899f7ed2e20e83c7fe0c0621ee7b842db.jpg)

- principle
  - LL

![image](https://bluejedis.github.io/picx-images-hosting/ds/image.3nrtncn4zy.png)

  - RR

![image](https://bluejedis.github.io/picx-images-hosting/ds/image.2dowh1ah54.png)
</div>
<div style="clear: both;"></div>

[^1]:动图详解+1个eg include all process https://blog.csdn.net/tunmang5421/article/details/124085854
    - 静态图描述: https://blog.csdn.net/jinking01/article/details/105986893