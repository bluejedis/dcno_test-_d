<div style="float: left; width: 64%; padding: 1%;">

# 串的模式匹配  

<ul>

## 简单的模式匹配算法

<ul>

### 基本概念

<ul>

- 子串的定位操作通常称为串的模式匹配
- 目的是求子串（模式串）在主串中的位置
- 采用定长顺序存储结构
- 使用暴力匹配算法，不依赖其他串操作

</ul>

### 算法实现

<ul>

```c
int Index(SString S,SString T){
    int i=1,j=1;
    while(i<=S.length && j<=T.length){
        if(S.ch[i]==T.ch[j]){
            ++i; ++j;            //继续比较后继字符
        }
        else{
            i=i-j+2; j=1;       //指针后退重新开始匹配
        }
    }
    if(j>T.length) return i-T.length;
    else return 0;
}
```

</ul>

### 算法思想

<ul>

- 比较过程：
  - 从主串S的第一个字符开始
  - 与模式串T的第一个字符比较
  - 若相等：
    - 继续逐个比较后续字符
  - 若不相等：
    - 从主串的下一个字符重新开始
    - 与模式串比较

- 匹配结果：
  - 成功：
    - 当模式串T中每个字符都与主串S中连续字符序列相等
    - 返回模式串首字符在主串中的序号
  - 失败：
    - 返回值为零

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/54e4ba107cb0eeb37086c69a0ca3069646b67af9d59c2e4b38b72e9d968ba3a6.jpg)  

</ul>

#### 时间复杂度分析

<ul>

- 最坏时间复杂度：O(nm)
  - n：主串长度
  - m：模式串长度
- 示例分析：
  - 模式串：0000001
  - 主串：0000000000000000000000000000000000000000000001
  - 匹配过程：
    - 前6个字符均为0的比较
    - 指针i需回溯39次
    - 总比较次数：40×7=280次

</ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
