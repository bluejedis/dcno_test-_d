<div style="float: left; width: 64%; padding: 1%;">
    
### 基本定义

<ul>

- 树是 <span style="border: 1px solid black; padding: 5px; display: inline-block;">$n$</span>  $（n{\geqslant}0$ ）个**结点**的**有限集**
  - $n=0$ 时，称为空树
    - 在任意一棵非空树中应满足:
    - 有且仅有 <span style="border-bottom: 3px dotted black;">一个</span>特定的称为<span style="border: 1px solid black; padding: 5px; display: inline-block;">根</span>的结点
  - $n>1$ 时，其余结点可分为 $m$  ($m\!>\!0$) 个互不相交的<span style="border-bottom: 2px solid black;">有限集</span> $T_{1},T_{2},\cdots,T_{m}$ 
      - 根的<span style="border-bottom: 2px solid black;">子树</span>:
        - 每个集合本身又是一棵树
      

</ul>

### 特点

<ul>

- <span style="border: 1px solid black; padding: 5px; display: inline-block;">递归</span>的数据结构
- <span style="border: 1px solid black; padding: 5px; display: inline-block;">分层</span>结构，特点：
  - 根结点<span style="border-bottom: 2px solid black;">NO</span> <span style="border-bottom: 3px dotted black;">前驱</span>，除根结点外的所有结点有且只有一个前驱
  - 树中all结点都可以有 <span style="border-bottom: 2px solid black;">零个</span>or<span style="border-bottom: 2px solid black;">多个</span> <span style="border-bottom: 3px dotted black;">后继</span>
- 树的应用特征：
  - 层次结构
  - 某个NODE at most只和 上一层的<u>一个</u> 结点有直接关系
  - 在 $n$ 个结点的树中有 <span style="border-bottom: 2px solid black;">$n\!-\!1$ 条边</span>

</ul>   

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
