### 内存泄漏
js里已经分配 内存地址的对象，但是由于长时间没有释放或者没办法清除，造成长期占用内存的现象。
会让内存资源大幅浪费，最终导致运行速度慢，甚至崩溃的情况。
### 为什么导致这种情况
垃圾回收机制
### 导致这种情况的因素
一些未声明直接赋值的变量
一些未清空的定时器
过度的闭包
一些引用元素没有被清除
