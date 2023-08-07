## Flex弹性布局

### 为什么会出现弹性布局

布局传统的解决方案,基于盒子模型,依赖display属性+position属性+float属性。他对于有些特殊布局非常不方便，比如，水平垂直居中就不容易实现（现有技术满足不了开发需求）

### Flex发展历史

2009年W3C提出概念，但是官方没有flex这个词。当时使用display:box;表示弹性布局

2011年浏览器厂商决定使用flexbox,来形容他的布局特点

2015年W3C正式将其修改为flexbox布局

2016年5月正式公布最新的稳定的flex布局规范标准,各大浏览器的支持越来越稳定

display:flex;

### flex定义

flex是flexible box的缩写,意为弹性布局,用来为盒状模型提供最大的灵活性

作用

> 它能够更高效方便的控制元素的对齐、排列
>
> 可以自动计算布局内元素的尺寸，无论这个元素的尺寸是固定的还是动态的
>
> 控制元素在页面的布局方向
>
> 按照不同于DOM所指定排序方式上对屏幕的元素重新排序

### 应用场景

使用现代浏览器中，史前浏览器不支持如Chrome4.0

有一定宽容度要求的设计中，因为弹性布局灵活度太高，很难100%换与阿奴设计稿，需要有一定的宽容度的设计稿

### Flex基本概念

采用flex布局的元素，称为flex容器（flex container）简称容器。他的所有子元素自动称为容器成员，称为fflex项目（flex item）简称项目

默认水平方向为主轴（main axis）

默认垂直方向为交叉轴、测轴（cross axis）

项目默认沿主轴排列

### Flex布局语法

语法：

想让谁称为flex布局的容器，就在钙元素上设置flex属性

> 块级元素display:flex;	/	display:webkit-flex;
>
> 行内元素display:inline-flex;

添加前缀 即浏览器的前缀

设为flex布局以后,flex item(项目)的float	clear和vertical-align的属性将失效,定位不失效

> 称为弹性布局后,自选箱马上变为行内块元素(不独占一行,默认水平方向排列)
>

### 容器上的属性-设置flex属性的元素

| **容器属性**    | **说明**                                                     |
| --------------- | ------------------------------------------------------------ |
| flex-direction  | 决定主轴的方向（即项目的排列方向） row （x轴为主轴） column（y轴为主轴） |
| flex-wrap       | 定义如果在一条轴线排不下，如何换行                           |
| flex-flow       | 复合属性：是flex-direction和flex-wrap属性的简写形式          |
| justify-content | 定义项目在主轴上的对齐方式                                   |
| align-items     | 定义项目在交叉轴、侧轴上如何对齐                             |
| align-content   | 定义多根轴线的对齐方式。如果项目只有一根轴线，该属性不起作用 |



#### flex-direction [决定主轴的方向]：

```css
决定主轴的方向（即项目的排列方向）
flex-direction: row | row-reverse | column | column-reverse;
属性值含义：
row（默认）、row-reverse：主轴为水平方向，起点在左端、右端
column 、column-reverse：主轴为垂直方向，起点在上沿、下沿
```



特点：

可以自动计算布局内元素的尺寸，无论这个元素的尺寸是固定的还是动态的

即：不论项目尺寸是多少，在不设置换行的情况下，会默认把所有的项目放在一行显示

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link rel="stylesheet" href="">
    <script src=""></script>

    <style>
        *{
            margin: 0;
            padding: 0;
        }
        ul{
            list-style: none;
            height: 500px;
            background-color: skyblue;
            display: flex;
            /* flex-direction: row; 默认沿x轴左右排列 */
            /* flex-direction: row-reverse  沿x轴倒序排列; */
            /* flex-direction: column  沿y轴从上到下排列; */
            /* 沿y轴从下到上排列 */
            flex-direction: column-reverse ;
        }
        li{
            width: 200px;
            height: 100px;
            margin: 20px;
            background-color: red;
        }
        ul>li:nth-of-type(2n){
            background-color: rgb(178, 231, 31);
        }
    </style>
</head>

<body>
    <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
        <li>5</li>
        <li>6</li>
    </ul>

</body>

</html>
```



#### flex-wrap  定义如果在一条轴线排不下，如何换行:

```css
默认情况下，项目都排在一条线（又称"轴线"）上。flex-wrap属性定义了如果一条轴线排不下，如何换行
flex-wrap: nowrap | wrap | wrap-reverse;
属性值含义
nowrap（默认）：不换行
wrap：换行，第一行在上方
wrap-reverse：换行，第一行在下方

```



#### flex-flow 主轴方向和换行属性复合写法:

```css
是复合属性：是flex-direction和flex-wrap的简写形式，默认值为row nowrap
flex-flow: <flex-direction> || <flex-wrap>;
flex-flow: column wrap; //表示 主轴是y轴 换行排列
属性值：取两个属性的值即可 ，属性值中间用空格隔开

```



**注意：**

使用复合写法和分开的写法，要复合团队开发习惯

不能因为方便而失去了代码的可读性



#### justify-content: 设置主轴元素的排列



```css
定义了项目在主轴上的对齐方式
justify-content: flex-start | flex-end | center | space-between | space-around | space-evenly;
属性值含义
flex-start（默认值）：左对齐
flex-end：右对齐
center： 居中
space-between：两端对齐，项目之间的间隔都相等
space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍
space-evenly:间距相等（均分）
```

```css
 ul{
            height: 500px;
            list-style: none;
            background-color: rgb(240, 126, 126);
            display: flex;
            justify-content: space-between;
        }
```



#### align-items: 设置侧轴元素的排列

```css
定义项目在交叉轴上对齐方式
align-items: flex-start | flex-end | center | baseline | stretch;
属性值：具体的对齐方式与交叉轴的方向有关，下面假设交叉轴从上到下
flex-start：交叉轴的起点对齐
flex-end：交叉轴的终点对齐
center：交叉轴的中点对齐
baseline: 项目的第一行文字的下基线对齐
stretch（默认值）：如果项目未设置高度或设为auto，将占满整个容器的高度
```



#### align-content: 设置侧轴上的子元素的排列方式(多行)

设置子项在侧轴上的排列方式并且只能用于子项出现换行的情况(多行)，在单行下是没有效果的。

```css
定义了多根轴线时项目在交叉轴的对齐方式
align-content: flex-start | flex-end | center | space-between | space-around | stretch;
```



| **属性值**        | **说明**                                                     |
| ----------------- | ------------------------------------------------------------ |
| flex-start        | 默认在侧轴的开始位置排列                                     |
| flex-end          | 在侧轴的尾部开始排列                                         |
| center            | 与侧轴的中间排列                                             |
| space-between     | 与交叉轴两端对齐，轴线之间的间隔平均分布                     |
| space-around      | 每根轴线两侧的间隔都相等。所以，轴线之间的间隔比轴线与边框的间隔大一倍。子项在侧轴平分剩余空间 |
| stretch（默认值） | 设置子项元素高度平分父元素高度，轴线占满整个交叉轴           |
| space-evenly;     | 平均分                                                       |

```css
/*利用justify-content、align-items两个属性可以比较简单的解决传统布局中垂直居中对齐的难题*/
```

#### align-content和align-items区别：

- align-items：适用于单行情况下，只有上对齐、下对齐、居中和拉伸
                          flex-start | flex-end | center | baseline | stretch;

- align-content： 适应于换行(多行)的情况下（单行情况下无效），可以设置上对齐、下对齐、居中、拉伸以及平均分配剩余空间等属性值。

                         flex-start | flex-end | center | space-between | space-around | stretch;  

- 总结就是单行找align-items 多行找align-content



### 项目上的属性——子元素的属性

| **容器属性** | **说明**                                                    |
| ------------ | ----------------------------------------------------------- |
| order        | 定义项目的排列顺序，数值越小排列越靠前，默认为0             |
| flex-grow    | 定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大   |
| flex-shrink  | 定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小 |
| flex-basis   | 定义在分配多余空间之前，项目占据的主轴空间                  |
| flex         | 是复合属性，代表flex-grow, flex-shrink 和 flex-basis的简写  |
| align-self   | 定义交叉轴上的对齐方式                                      |



#### order: 项目排列顺序

```css
定义项目的排列顺序。数值越小，排列越靠前，默认为0
order: int;
属性值
必须为 0 或者 正整数
负数的话
```



```css
 ul>li:nth-of-type(2){
            order: 1;
        }
```



#### flex-grow: 分配剩余空间

```css
定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。主要作用是：分配剩余空间的
flex-grow: <number>;
属性值
不能为负数，虽然可以设置为正小数值，一般不这么用

对剩余空间进行分配，
比如:
第一个li flex-grow:1;
第二个li flex-grow:2;
第三个li flex-grow:3;

表示：剩余空间分了1+2+3  6份
第一个li 占1份
第二个li 占2份
第三个li 占3份
```



#### flex-shrink: 空间不足项目缩小

```css
定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小。主要作用是做缩小空间用的  0 没有空间也不缩小
flex-shrink: <number>;
属性值
负值对该属性无效

如flex-shrink:3; 表示在空间不足的情况下，其他元素缩小1，该元素缩小3份
```



#### flex-basis: 放大缩小比例前生效的宽高 类似我们设置的宽高

```css
在flex-grow  和flex-shinrk属性起作用以前，定义每一个flex项目的默认大小，它的默认值为auto，即项目的本来大小。类似于width
flex-basis: auto || <length>;
属性值
length: 我们平常用的一些属性值，如 px、%、 rem等 
```



#### flex:放大缩小默认值复合写法

```css
是一个复合属性，代表flex-grow, flex-shrink 和 flex-basis的简写，后两个属性可选，默认值为0 1 auto
flex: auto | <'flex-grow'> [ <'flex-shrink'>  <'flex-basis'> ];
属性值
两个快捷值
flex：auto；代表 (1 1 auto)
flex：none；代表 (0 0 auto)
flex:1 存在剩余空间，就放大
```



#### align-self: 单个项目侧轴的属性

```css
交叉轴上的对齐方式，允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性
align-self: auto | flex-start | flex-end | center | baseline | stretch;
属性值
默认值为auto，表示继承父元素的align-items属性
可能取6个值，除了auto，其他都与align-items属性完全一致
```

如：让其中一个项目填充整个侧轴：

```css
ul>li:nth-of-type(1){
            margin: 10px ;
            /* height: auto;
            align-self: stretch; */
            align-self: flex-end;

        }
```



### 10、flex布局注意点

- flex-direction的改变，一些依赖于主轴定义的属性也跟着改变
  - justify-content
  
  - align-content
  
  - align-items
  
- 容器转为flex布局之后，项目不受float的影响
- flex-wrap的默认是nowrap，我们需要设置才会自动换行