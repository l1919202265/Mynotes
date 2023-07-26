## 消除所有默认边距

```css
*{
	margin:0;
	padding:0;
}
```

## 图片引入方法及调整位置

```css
background:url(./a/b/c.jpg) no-repeat x轴px y轴px;
	x轴向左负值 向右正值
	y轴向上负值 向下正值
	no-repeat;不平铺，不重复
background-size:cover&contain&50px,50%;


background-attachment{

​	设置背景图像是否固定或者随着页面的其余部分滚动。

​	scroll 背景图片随着页面的滚动而滚动，这是默认的。

​	fixed 背景图片不会随着页面的滚动而滚动。

​	local 背景图片会随着元素内容的滚动而滚动。

}

背景图片和背景颜色共存，背景颜色在下
```



```css
 background-color: rgba(r, g, b, a);背景透明度
```



## 文本调整

```css
em 1个em就是当前的字体大小，
text-indent:2em;缩进2个距离

text-align:元素对齐方式;
text-decoration:文本的装饰;
text-decoration:overline color;上划线
text-decoration:line-through color;中划线
text-decoration:underline color;下划线

a{
    text-decoration: none;取消a标签超链接下划线
}


letter-spacing: 10px;文字之间的距离
```

## 字体样式调整

```css
取值100-900,400是默认粗细
font-weight:加粗字体;
谷歌浏览器字体大小默认16px，最小12px
font-size:字体大小;
font-family:字体样式;
font-style:字体风格;
```

## 元素定位相对定位和绝对定位

```css
position:relative;相对定位
position:absolute;绝对定位
top:顶部;
bottom:底部;
left:左;
right:右;
```

## 选择器方式和优先级

```css
选择器选择方式
1、#id{
    
}
2、.类名{
    
}
3、标签{
    
}
选择器范围越小，优先级越高
id是唯一的，id名不能重复
id选择器>类名选择器>标签选择器
```

```css
标签的属性line-height的值等于当前标签的高度 文本就会垂直居中
line-height:;
```

```css
a:hover悬浮链接时的样式 生效

a:visied访问链接后的样式 生效

a:active未释放的样式 生效

a:link未单击访问链接的样式 生效
```

## 鼠标状态用法

```css

cursor{
    pointer	小手
	move	移动
	text	文本选中
    help	问号帮助
    crosshair	十字架	
    wait	等待，不允许用
}
```

```css
单行文字超出部分显示省略号...  
text-overflow: ellipsis;
overflow: hidden;
word-break: break-all;
white-space: nowrap;
```

```css
两行文字超出部分显示省略号...  
word-break: break-all;
overflow: hidden;
display: -webkit-box;
-webkit-line-clamp: 2;
-webkit-box-orient: vertical;
```

```css
无序列表
li{
    list-style:none;去除li圆点样式
    disc默认样式
    square正方形实心
    circle空心圆
    background:./a.jpg no-repeat;
    text-indent:40px;
    background-size:10px 10px;背景图片大小
    text-decoration:line-through;
    font-family:楷体;
}

```

```css
ol{
    list-style-image:url(./a.jpg);不可控，不用
}
```

```css
table{
    align:left、center、right;
    cellpadding:10;单元格内边距
    cellspacing:0;单元格和单元格边距
    border-collapse: collapse;清除边框重合，边框崩溃
}

表格的合并
1、行合并rowspan
	列合并colspan
2、把被合并的内容 删掉
以要和合并单元格 左上角的单元格为基础

先找到th的父元素 th父元素下面 的 第1个th
th:nth-of-type(1){
    background-color:#ce7d4d;th父元素的第一个，改变颜色
}
th:nth-of-type(2){
    background-color:#ce7d4d;
    父元素的第二个，改变颜色
}
th:nth-of-type(3){
    background-color:#ce7d4d;父元素的第三个，改变颜色
}


tr:nth-of-type(2n){
    background-color:#fff;父元素偶数个改变颜色
}
tr:nth-of-type(2n-1){
    background-color:#fff;父元素奇数个改变颜色
}
```

```css
outline:none;消除input选中边框
input::placeholder修改输入框提示内容样式
```

```css
交集选择器	既是...又是		标签.类名
h3.top{}

并集选择器	逗号隔开
p,h1,h2
.one,p,#test{}

后代选择器	h1 em{}

子代选择器	h1>em{}选择器>选择器

属性选择器	具备该属性即生效
[属性 值]{}
具备href属性
[href]{}
需要全部等于 才生效
[href='http://www.baidu.com']{}

属性以某某某开头
[href ^="www"]{}

属性只要包含某某某
[href *='com']{}

属性以某某某结尾
[href $='cn']{}
```

```html
/*#region*/折叠显示代码
/*#endregion*/
```

```css
border-top
border-top-style上边框样式
border-bottom
border-bottom-style下边框样式
border-left
border-left-style左边框样式
border-right
border-right-style右边框样式

边框样式
solid实线
dotted点状虚线
dashed线段类型的虚线
double双实线
```

```css
transparent透明色
```

```css
padding:10px 5px 15px 20px;
左上内边距是 10px
右上内边距是 5px
右下内边距是 15px
左下内边距是 20px
```

```css
margin:1px 1px 1px 1px;
上 右 下 左
margin: 10px 20px;
上下 左右
```



```css
边框圆角
border-radius:左上px 右上px 右下px 左下px;
border边框
border:1px solid red;1像素红色边框
```

```css
清除浮动四种方法
第一种 
给浮动元素的父元素设置一个固定的高

第二种
overflow:hidden;触发BFC机制，格式化内容，超出部分隐藏 给浮动元素的父元素设置overflow:hidden

overflow:scroll;超出部分滚动
clear:left或right或both;

第三种 伪类清除
.box::after{
    content:'';
    dispaly:block;
    clear:both;
}
第四种 
.clearFix{
    content:'';
    display:block;
    clear:both;
}
```

```css
定位
static 静态定位

relative 相对定位 参照物为自身 不脱离标准流

absolute 绝对定位 以离当前元素最近的加了定位的祖级元素为参照物，若没有以浏览器为标准 脱离标准流

fixed 固定定位 脱离标准流 不占实际位置 参照点当前屏幕的四条边框 默认位置为屏幕左上角

sticky 粘性定位 
粘性定位不生效的原因 
1、父元素不能使用overflow:hidden;
2、父元素的高度不能小于粘性定位的高度
3、
4、sticky仅在父元素内生效

选择器{
    position:static、relative、absolute、fixed;
    值：；
}


子绝absolute 父相relative
```

