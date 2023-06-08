BFC：Block Formatting Context，块级格式化上下文。
BFC可以理解为一个容器。
如果一个元素符合触发BFC的条件，则BFC中的元素布局不受外部影响。
### 创建BFC的方式
1.绝对定位元素（position为absolute或fixed）
2.行内块元素（display为inline-block）
3.overflow的值不为visible
### BFC特性及应用
1.避免外边距重叠
```html
<div class="container">
    <div class="cube"></div>
</div>
<div class="cube"></div>
```
```css
.cube{
    width: 100px;
    height: 100px;
    background-color:dodgerblue;
    margin: 100px;
}
.container{
    overflow: hidden;/* 这行不加的话，两个方块距离100px，加完距离200px */
}
```
2.清除浮动
```html
<div class="container">
	<div class="cube"></div>    
	<div class="cube"></div>
	<div class="cube"></div>
</div>
```
```css
.cube{
    width: 100px;
    height: 100px;
    background-color:dodgerblue;
    margin: 100px;
    float: left;
}
.container{
    overflow: hidden;/* 这行不加的话，container高度只有100px，没有完全覆盖 */
    
    background-color:grey;
    min-height: 100px;
}
```
3.阻止元素被浮动元素覆盖
（自适应两栏布局，左边宽度固定，右边宽度自适应）
```html
<div class="left"></div>    
<div class="right"></div>
```
```css
.left{
    width: 100px;
    height: 100px;
    background-color:dodgerblue;
    float: left;
}
.right{    
    overflow: hidden;/* 这行不加的话，左右元素会发生重叠 */
    
    height: 200px;
    background-color:red;
}
```
