<div style="float: left; width: 64%; padding: 1%;">

## 串的模式匹配算法KMP算法  

<ul>

### KMP算法的基本思想

<ul>

- 从暴力匹配算法的低效分析出发:
  - 每趟匹配失败都需模式串后移一位重新比较
  - 已匹配相等的字符序列重复比较造成低效
- 改进方向:
  - 分析模式串本身结构
  - 利用已匹配前缀信息优化滑动
  - 避免主串指针回溯

</ul>

### 关键概念定义

<ul>

#### 字符串的前缀、后缀和部分匹配值

<ul>

- 基本概念:
  - 前缀: 除最后一个字符外的所有头部子串
  - 后缀: 除第一个字符外的所有尾部子串
  - 部分匹配值: 字符串前缀和后缀的最长相等前后缀长度

- 示例分析('ababa'):
  - 'a': 前缀后缀为空集, PMV=0
  - 'ab': 前缀{a}, 后缀{b}, PMV=0 
  - 'aba': 前缀{a,ab}∩后缀{a,ba}={a}, PMV=1
  - 'abab': 前缀{a,ab,aba}∩后缀{b,ab,bab}={ab}, PMV=2
  - 'ababa': 前缀{a,ab,aba,abab}∩后缀{a,ba,aba,baba}={a,aba}, PMV=3

</ul>

#### 部分匹配值的应用

<ul>

- 实例分析:
  - 主串: ababcabcacbab
  - 子串: abcac
  - 子串部分匹配值: 00010

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/377aad20736ed34d8161d83be96787936c200fb1acb2b79e434aac502c5bebb4.jpg)  

</ul>

#### 匹配过程分析

<ul>

- 第一趟匹配:
  - 发现不匹配位置
  - 计算移动位数 = 已匹配字符数(2) - 对应PMV(0) = 2

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/2d937d17d0e58b6a37d99b239f990479ce6b593e3a4c44886709745a86ba0658.jpg)  

- 第二趟匹配:
  - 发现不匹配位置
  - 计算移动位数 = 已匹配字符数(4) - 对应PMV(1) = 3

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/9c878b55e5555f3562affbaf3c7438a4ab69ae4a9606ed12fc034b57fdf254a7.jpg)  

- 第三趟匹配:
  - 完全匹配成功

</ul>

#### KMP算法效率分析

<ul>

- 主要优势:
  - 主串指针无需回退
  - 时间复杂度O(n+m)
- 移动规则:
  - PMV为0: 子串直接后移到主串当前位置
  - PMV不为0: 子串滑动对齐相等前后缀

</ul>

### KMP算法的原理是什么

<ul>

#### 部分匹配值的意义

<ul>

- "移动位数 = 已匹配的字符数-对应的部分匹配值"的含义:
  - 当字符不匹配时,已匹配部分的前缀和后缀有最长公共元素
  - 可直接跳过无需比较的部分,提高效率

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/aad83da896298bac9915ea9c4489fa67e12556a127bd80d1503ca19c153b2b4f.jpg)

</ul>

#### next数组的引入

<ul>

- 对算法的改进:
  - Move = (j-1)-PM[j-1]
  - PM表右移一位得到next数组
  - next数组的特点:
    - 首位用-1填充
    - 最后一位舍去
    - 可整体+1简化计算

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/ad045d891fd388f999f29e3a5d57bd91ca2d1f0c91de842b0ae7fd127508ce30.jpg)
![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/7ac119d782f92328295099076ea25ef796b9b4ad845f5b5ae4fafe2968fd1116.jpg)

> pro：KMP匹配过程中指针变化的分析（2015）

</ul>

#### next数组的推导

<ul>

- 基本概念:
  - j = next[j]为子串指针变化公式
  - next[i]表示失配时跳转的位置

- 推导过程:
  - 主串和模式串的匹配条件
  - 失配时的滑动规则
  - k值的确定方法

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/2dbfa2d11030630a5c13a0b2b3423e37db24b5080dda10d4eee8e48614d8ca4d.jpg)

</ul>

##### next函数的具体计算

<ul>

- 两种情况分析:
  - pk = pj时的处理
  - pk ≠ pj时的处理
- 实例说明:
  - 6字符模式串的next值计算过程

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/fd6fc648f51ead06104f3b6607b7412dd6e3e3d3020eac6f6751cbd3eaaf9d00.jpg)

</ul>

##### 代码实现

<ul>

- next值计算程序:

```c
void get_next(SString T,int next[]){
    int i=1,j=0;
    next[1]=0;
    while(i<T.length){
        if(j==0||T.ch[i]==T.ch[j]){
            ++i; ++j;
            next[i]=j;      //若pi=pj，则 next[j+1]=next[j]+1
        }
        else
            j=next[j];      //否则令 j=next[j]，循环继续
    }
}
```

</ul>

#### KMP匹配算法

<ul>

- 算法特点:
  - 形式类似简单模式匹配
  - 失配时i不变,j回退
- 代码实现:

```c
int Index_KMP(SString S,SString T,int next[]){
    int i=1, j=1;
    while(i<=S.length&&j<=T.length){
        if(j==0||S.ch[i]==T.ch[j]){
            ++i; ++j;            //继续比较后继字符
        }
        else
            j=next[j];          //模式串向右移动
    }
    if(j>T.length)
        return i-T.length;      //匹配成功
    else
        return 0;
}
```
> KMP匹配过程中比较次数的分析（2019）

</ul>

#### 算法效率分析

<ul>

- 时间复杂度比较:
  - 普通模式匹配: O(mn)
  - KMP算法: O(m+n)
- 实际应用:
  - 普通算法仍被广泛使用
  - KMP在部分匹配较多时优势明显
  - KMP主要优点是主串不回溯

</ul>

### KMP算法的进一步优化  

<ul>

#### 优化背景

<ul>

- next数组在某些情况下存在缺陷需要进一步优化
- 以模式串"aaaab"和主串"aaa baa aab"为例：

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/89c15cad9b3226daad524eb2c8f2a36edfa137b898562d900f05e8bab1751ffd.jpg)  

</ul>

#### 问题分析

<ul>

- 当i=4、j=4时出现失配情况
  - S4与p4(b≠a)失配
  - 使用原next数组需要进行3次无意义比较
    - S4与p3
    - S4与p2
    - S4与p1

</ul>

#### 问题根源

<ul>

- 问题在于出现pj=pnext[j]的情况
  - 当pj≠sj时，下次匹配必然是pnext[j]跟sj比较
  - 若pj=pnext[j]，则等于用相同字符重复比较
  - 这种比较毫无意义且必然失配

</ul>

#### 优化方案

<ul>

- 当出现pj=pnext[j]时：
  - 需要递归处理
  - 将next[j]修正为next[next[j]]
  - 直至两者不相等为止
  - 更新后的数组命名为nextval

</ul>

##### 优化算法实现

<ul>

```c
void get_nextval(SString T,int nextval[]){
    int i=1, j=0;
    nextval[1]=0;
    while(i<T.length){
        if(j==0||T.ch[i]==T.ch[j]){
            ++i; ++j;
            if(T.ch[i]!=T.ch[j]) nextval[i]=j;
            else nextval[i]=nextval[j];
        }
        else
            j=nextval[j];
    }
}
```

</ul>

#### 学习建议

<ul>

- KMP算法对初学者来说理解难度较大
- 建议：
  - 多次阅读本章内容
  - 参考其他教材相关内容
  - 通过多方面学习来巩固这个知识点

</ul>

### note 

<ul>

学习KMP算法时，应从分析暴力法的端入手，思考如何去优化它。

实际上，已匹配相等的序列就是模式串的某个前缀，因此每次回溯就相当于模式串与模式串的某个前缀比较，这种频繁的重复比较是效率低的原因。

这时，可从分析模式串本身的结构入手，以便得知当匹配到某个字符不等时，应该向后滑动到什么位置，即已匹配相等的前缀和模式串若首尾重合，则对齐它们，对齐部分显然无须再比较，下一步则是直接从主串的当前位置继续进行比较。  

~统考不会考KMP算法题~

</ul>
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
