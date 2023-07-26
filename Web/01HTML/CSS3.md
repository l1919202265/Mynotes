```css
p:first-of-type p标签父元素的第一个p元素

p:first-child p标签父元素下第一个子元素，并且是p标签

p:last-of-type p标签父元素的最后一个p元素

p:last-child p标签父元素下最后一个子元素，并且是p标签

p:nth-child（） p标签父元素下第几个子元素

p:nth-of-type() p标签下第几个p

h1:only-child h1父元素下只能有一个子元素，还要是h1元素
```



```css
伪类

标签内部之前
p::before{
    content:'哈哈哈';
    display:inlne-block;
}


标签内部之后
p::after{
    content:'哈哈哈';
    display:inlne-block;
}


```

## text文本超出部分隐藏显示省略号...

```css
overflow:hidden;
white-space:nowrap;不换行
text-overflow:ellipsis;省略号
```

## 水平垂直居中

```css
父元素
position:relative;
子元素
position:absolute;
top:50%;相对于父元素距离top50%
left:50%;相对于父元素距离left50%
transform:translate(-50%,-50%);
相对于自身左上角位移X轴左位移-50%，相对于自身位移Y轴-50%	X轴左负右正，Y轴上负下正

```

## 2D,3D

```css
perspective:1000px;3D视距
保留3D
transform:translate3d(X轴,Y轴,Z轴);平移(单位为px像素)
transform:rotate3d(X deg,Y deg,Z deg);旋转(单位为deg角度)
transform-orgin: to left;操作原点
```

