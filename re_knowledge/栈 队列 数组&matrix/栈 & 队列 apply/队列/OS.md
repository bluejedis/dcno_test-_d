<div style="float: left; width: 64%; padding: 1%;">

## 队列在计算机系统中的应用  

<ul>

### 解决速度不匹配问题
> pro：缓冲区的逻辑结构（2009）  

* 主机与打印机速度不匹配示例：
  * 问题：主机输出速度远快于打印速度
  * 解决方案：
    * 设置打印数据缓冲区
    * 主机写入数据到缓冲区
    * 缓冲区满则主机暂停输出
    * 打印机按FIFO原则取出数据打印
    * 打印完成后向主机发出请求
  * 优点：
    * 保证打印数据正确性
    * 提高主机效率

### 解决资源竞争问题
> pro：多队列出队/入队操作的应用（2016）  

* CPU资源竞争示例：
  * 场景：多终端系统中多用户需求CPU资源
  * 处理方式：
    * 按时间顺序将请求排成队列
    * 分配CPU给队首用户使用
    * 程序结束或用完时间后出队
    * 继续分配CPU给新队首用户
  * 优点：
    * 满足所有用户请求
    * 确保CPU正常运行

</ul>

</div>
<div style="float: right; width: 26%; padding: 1%;">

</div>
<div style="clear: both;"></div>
