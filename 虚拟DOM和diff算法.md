### 虚拟DOM
虚拟DOM（Virtual DOM）是一种轻量级的JavaScript对象，它描述了真实DOM中的，节点信息和属性。

虚拟DOM可以在内存中操作，然后通过算法比较新旧的虚拟DOM的差异，最终只对发生变化的部分进行DOM操作，从而提高了性能。
### 虚拟dom的好处
1.保证性能下限。在不进行手动优化的情况下，提供过得去的性能。
虚拟dom，可以避免频繁的操作真实dom。因为真实dom操作非常昂贵，对性能有很大的影响。
页面渲染的流程：解析HTML，生成dom，生成cssom（CSS Object Model，css对象模型），layout（布局），paint（绘制），compiler。

下面对比一下，修改dom时，真实dom操作和虚拟dom的过程：
真实dom：生成html字符串，重建所有的dom元素
虚拟dom：生成VNode（virtual node，虚拟节点），DOMDiff，必要的dom更新

2.跨平台
虚拟dom本质上是js对象，它可以很方便的跨平台操作，比如服务端渲染，uniapp，浏览器，移动端等。
### vue中的虚拟DOM
vue中，每个组件都有自己的虚拟dom对象。

当组件数据发生变化时，vue会重新生成这个组件的虚拟dom对象。
并与旧的虚拟dom对象进行比较，找出需要更新的节点，并生成一个补丁（Patch）。
最后将这个补丁应用到真实的dom中，完成更新操作。
### diff算法的原理
新旧虚拟dom对比时：
1.首先，对比节点本身，判断是否为同一节点，如果不为相同节点，则删除该节点，重新创建节点进行替换

2.如果为相同节点，进行patchVnode，判断如何对该节点的子节点进行处理。先判断一方有子节点，一方没有子节点的情况（如果新的children没有子节点，将旧的子节点移除）

3.比较如果都有子节点，则进行updateChildren，判断如何对这些新老节点的子节点进行操作（diff核心）

4.匹配时，找到相同的子节点，递归比较子节点

在diff中，只对同层的子节点进行比较，放弃跨级的节点比较，使得时间复杂度从O(n3)降低到O(n)。
只有当新旧children都为多个子节点时，才需要用核心的diff算法进行同层级比较。

