### CSS3基础

#### border-image属性

| 值                  | 说明                                                   |
| ------------------- | ------------------------------------------------------ |
| border-image-source | 边框图片的路径                                         |
| border-image-slice  | 图片边框向内偏移 num / % / fill                        |
| border-image-width  | 图片边框的宽度                                         |
| border-image-outset | 边框图像区域超出边框的量                               |
| border-image-repeat | 图像是否应该平铺(repeat)、铺满(round)或拉伸(stretch)。 |

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">

    <title>Document</title>

    <style>
        .box {
            margin: 50px auto;
            width: 300px;
            height: 300px;
            border: 1px solid;
            background-color: rgb(252, 225, 225);
            /* border-image-source  边框图片的路径                       */
            border-image-source: url(./img/border.png);
            /* border-image-slice   图片边框向内偏移 num / % / fill */
            border-image-slice: 30;
            /* border-image-width   图片边框的宽度*/
            border-image-width: 30px;
            /* border-image-outset  边框图像区域超出边框的量*/
            border-image-outset: 0px; ;
            /* border-image-repeat  图像是否应该平铺(repeat)、铺满(round)或拉伸(stretch)*/
            border-image-repeat: round;
            
            border-image: url(/i/border_image_button.png) 0 14 0 14 stretch
        }
    </style>
</head>

<body>
    <div class="box"></div>
</body>

</html>
```

### C3背景!background-size属性

| 值                   | 说明                                                         |
| -------------------- | ------------------------------------------------------------ |
| length（单位：像素） | 设置背景图片高度和宽度。第一个值设置宽度，第二个值设置的高度。如果只给出一个值，第二个是设置为"auto(自动)" |
| percentage（百分比） | 以父元素的百分比来设置背景图像的宽度和高度。。第一个值设置宽度，第二个值设置的高度。如果只给出一个值，第二个是设置为"auto(自动)" |
| cover                | 把背景图像扩展至足够大，以使背景图像完全覆盖背景区域。背景图像的某些部分也许无法显示在背景定位区域中。 |
| contain              | 把图像图像扩展至最大尺寸，以使其宽度和高度完全适应内容区域。 |

语法：

```
//background-size:100px;
//background-size:100%;
//background-size:cover;
background-size:contain;
```

#### background-origin/clip属性:

background-origin 属性规定 background-position 属性相对于什么位置来定位
 background-clip 属性规定背景的绘制区域

| 值          | background-origin值说明      | background-clip值说明 |
| ----------- | ---------------------------- | --------------------- |
| padding-box | 背景图像相对于内边距框来定位 | 背景被裁剪到内边距框  |
| border-box  | 背景图像相对于边框盒来定位   | 背景被裁剪到边框盒    |
| content-box | 背景图像相对于内容框来定位   | 背景被裁剪到内容框    |

### 高级选择器

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

### text文本超出部分隐藏显示省略号...

```css
overflow:hidden;
white-space:nowrap;不换行
text-overflow:ellipsis;省略号
```

### 水平垂直居中

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

### 2D,3D

```css
perspective:1000px;3D视距
保留3D
transform:translate3d(X轴,Y轴,Z轴);平移(单位为px像素)
transform:rotate3d(X deg,Y deg,Z deg);旋转(单位为deg角度)
transform-orgin: to left;操作原点
```

