<div style="float: left; width: 64%; padding: 1%;">

## 顺序存储结构  

### 队列的顺序存储  

#### 基本概念
* 队列的顺序实现特点：
  * 分配连续存储单元存放队列元素
  * 附设两个指针：
    * 队头指针front指向队头元素
    * 队尾指针rear指向队尾元素的下一个位置

#### 存储类型定义
* 队列的顺序存储类型：

```c
#define MaxSize 50              //定义队列中元素的最大个数
typedef struct{
    ElemType data[MaxSize];   //用数组存放队列元素
    int front,rear;           //队头指针和队尾指针
}SqQueue;
```


#### 基本操作特点
* 初始状态：
  * Q.front = Q.rear = 0
* 操作规则：
  * 进队操作：
    * 队不满时执行
    * 先送值到队尾元素
    * 再将队尾指针加1
  * 出队操作：
    * 队不空时执行
    * 先取队头元素值
    * 再将队头指针加1

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/e760968acf7af6ebf1dbb79c2ec260ef38948b9bfa862117879af3c154b72de2.jpg)  

### 循环队列  

#### 概念引入
* 解决顺序队列"假溢出"问题
* 将顺序队列视为环状空间
* 队首指针到MaxSize-1后自动转到0

> pro：特定条件下循环队列队头/队尾指针的初值（2011）  

#### 基本规则
* 初始状态：Q.front = Q.rear = 0
* 指针操作：
  * 队首指针进1：Q.front = (Q.front+1)%MaxSize
  * 队尾指针进1：Q.rear = (Q.rear+1)%MaxSize
  * 队列长度：(Q.rear+MaxSize-Q.front)%MaxSize

> pro：特定条件下循环队列队空/队满的判断条件（2014）  

#### 队空队满判断
* 判断方式：
  * 方式一：牺牲一个单元
    * 队满条件：(Q.rear+1)%MaxSize == Q.front
    * 队空条件：Q.front == Q.rear
    * 元素个数：(Q.rear-Q.front+MaxSize)%MaxSize
  * 方式二：增设size成员
    * 队空：Q.size == 0
    * 队满：Q.size == MaxSize
  * 方式三：增设tag成员
    * 删除成功置tag=0
    * 插入成功置tag=1

![](https://cdn-mineru.openxlab.org.cn/model-mineru/prod/3b778995860d2f05b33eca711357acb81d2a1bb530366b1912ac965859336dc2.jpg)  

#### 基本操作实现


- 初始化

```cpp
void InitQueue(SqQueue &Q){
    Q.rear=Q.front=0;   //初始化队首、队尾指针
}
```

- 判队空

```cpp
bool isEmpty(SqQueue Q){
    if(Q.rear==Q.front) //队空条件
        return true;
    else
        return false;
}
```

- 入队

```cpp
bool EnQueue(SqQueue &Q,ElemType x){
    if((Q.rear+1)%MaxSize==Q.front) //队满则报错
        return false;
    Q.data[Q.rear]=x;
    Q.rear=(Q.rear+1)%MaxSize;      //队尾指针加1取模
    return true;
}
```

- 出队

```cpp
bool DeQueue(SqQueue &Q,ElemType &x){
    if(Q.rear==Q.front)         //队空则报错
        return false;
    x=Q.data[Q.front];
    Q.front=(Q.front+1)%MaxSize; //队头指针加1取模
    return true;
}
```
</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
