```css
position:relative;
```
```css
position:absolute;
```
relative:定位的方式为，相对于自己之前的默认的位置。

absolute:向上一层一层的找自己的父元素，然后看他们的position属性，谁的position属性不是static，他就以谁为标准偏移。
如果一直没有的话，就会找到body。body也不是的话，但是已经是最后一层了，所以他就只能以body的初始位置为基准了。

所有的块属性，position默认为static。