# HTML

```html
<meta 源标签>
<h1>标题标签</h1>	h1-h6由大变小	逐渐递减
<p>段落标签</p>
<em>字体倾斜</em> <i></i>
<strong>字体加粗</strong> <b>字体加粗</b>
<hr>水平线
<br>换行
<span>相当于小括号，没有任何影响 不独占一行，没有自己的样式</span>
&nbsp;空格
```

```html
href
1、网络图片	只写网络地址
2、本地图片	./后退一步	../后退两步
target目标对象
_blank空的
a标签路径为空点击后页面刷新
<a href="#" target="_blank">超链接</a>
```

```html
<link rel="stylesheet" href="./路径">引入css

src	图片的路径
1、网络图片	只写网络地址
2、本地图片	./后退一步	../后退两步
alt图片加载失败显示的文字
<img src="./本地路径地址或网络地址" alt="图片加载失败的时候显示">
```

```html
快速生成5个h1标签
h1{我是第$个h1}*5
```

```html
无序列表
<ul>容器
    <li>无序列表</li>
    <li>无序列表</li>
</ul>
ul和li 搭配，ul内不可以放div,ui亲子级只能是li，li内可以放一切标签,ol同理
```

```html
有序列表
<ol>容器
    <li>有序列表</li>
</ol>
```

```html
自定义列表
<dl>容器
    <dt>名词1</dt>
    <dd>名词1解释</dd>
    <dd>名词2解释</dd>
</dl>
```

```html
表格
<table>容器
    <th>表头</th>
    <tr>行
        <td>列
        </td>
    </tr>
</table>
```

```html
<input type="text"> 单标签 表单输入框 不独占一行
<input type="password">
<input type="phone">
<input type="radio" name="">单选框 只能选择一个radio类型的表单 name一样
<input type="checkbox" checked="true&false">复选框 可以选择多个 checked true&false默认勾选 ckecked=""就可以了
<input type="file">上传文件
<input type="submit">提交
<button>按钮</button>
<input type="reset">重置 需要form表单容器包裹
<input type="image" src="./a.jpg">图像形式的按钮 不用！
placeholder提示信息
<label for="btn">
绑定文字
</label>
<input id="btn" type="check">
```

```html
<textarea readonly只读 cols="每行中的字符数" rows="显示的行数">文本内容</textarea>

<div contenteditable="true"></div>

<select>下拉菜单 
    <option>请选择</option>
    <option>第一个选项</option>
    <option>第二个选项</option>
</select>

<form action="./a.html" method="get"></form>

<button hidden>隐藏按钮</button>
<button disabled>无法点击按钮 禁用 </button>
```

```css
盒子模型
padding 内边距 + border边框 + margin外边距
```



# CSS

### 消除所有默认边距

```css
*{
	margin:0;
	padding:0;
}
```

### 图片引入方法及调整位置

```css
background:url(./a/b/c.jpg) no-repeat x轴px y轴px;
	x轴向左负值 向右正值
	y轴向上负值 向下正值
	no-repeat;不平铺，不重复
background-size:cover&contain&50px,50%;


background-attachment{

	设置背景图像是否固定或者随着页面的其余部分滚动。

	scroll 背景图片随着页面的滚动而滚动，这是默认的。

	fixed 背景图片不会随着页面的滚动而滚动。

	local 背景图片会随着元素内容的滚动而滚动。

}

背景图片和背景颜色共存，背景颜色在下
```

```css
background-color: rgba(r, g, b, a);背景透明度
background-color:rgba(255,255,255,.3);
```

### 文本调整

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

### 字体样式调整

```css
取值100-900,400是默认粗细
font-weight:加粗字体;
谷歌浏览器字体大小默认16px，最小12px
font-size:字体大小;
font-family:字体样式;
font-style:字体风格;
```

### 元素定位相对定位和绝对定位

```css
position:relative;相对定位
position:absolute;绝对定位
top:顶部;
bottom:底部;
left:左;
right:右;
```

### 选择器方式和优先级

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

### 鼠标状态用法

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

### 单行文字超出部分显示省略号...  

```css
text-overflow: ellipsis;
overflow: hidden;
word-break: break-all;
white-space: nowrap;
```

### 两行文字超出部分显示省略号...  

```css
word-break: break-all;
overflow: hidden;
display: -webkit-box;
-webkit-line-clamp: 2;
-webkit-box-orient: vertical;
```

```css
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
outline:none;消除input选中后的边框样式
input::placeholder输入框内提示内容文字样式
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

# HTML5

```html
新增元素
<header>头部</header>
<nav>导航 头部主体连接部分</nav>
<section></section>
<main>主体</main>
<article>正文</article>
<aside>侧边栏</aside>
<footer>底部</footer>




废除的元素
<big></big>

<center>居中</center>
text-alingn:center;代替

<font></font>

<strick>中划线</strick>
text-decoration:line-though;代替

<iframe>
    框架，网页嵌套 嵌套其他网站
</iframe>

<div contentediable></div>允许被编辑

document.designMode='on';允许页面被编辑

hidden 规定对元素进行隐藏

time 标签定义日期或时间

tabindex 规定元素的跌制顺序
```

# css3

### C3基础

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

### C3背景

#### !background-size属性

|          值          | 说明                                                         |
| :------------------: | ------------------------------------------------------------ |
| length（单位：像素） | 设置背景图片高度和宽度。第一个值设置宽度，第二个值设置的高度。如果只给出一个值，第二个是设置为"auto(自动)" |
| percentage（百分比） | 以父元素的百分比来设置背景图像的宽度和高度。。第一个值设置宽度，第二个值设置的高度。如果只给出一个值，第二个是设置为"auto(自动)" |
|        cover         | 把背景图像扩展至足够大，以使背景图像完全覆盖背景区域。背景图像的某些部分也许无法显示在背景定位区域中。 |
|       contain        | 把图像图像扩展至最大尺寸，以使其宽度和高度完全适应内容区域。 |

语法：

```css
background-size:100px;
background-size:100%;
background-size:cover;
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

# JavaScript

## 01运算符

##### 1、如果+号两边的内容都是number类型 则执行数学运算

##### 2、如果有任意一边是string类型 左右拼接

示例：

```javascript
var num1 = 5;
var num2 = 7;
var sum = num1 + num2;
console.log(sum);
console.log(typeof sum);

打印结果：
12
number
```

```javascript
var num1 = '5';
var num2 = 7;
var sum = num1 + num2;
console.log(sum);
console.log(typeof sum);

打印结果：
57
string
```

##### 3、执行数学运算的时候 false 0	非零的是true 1

```javascript
var num1 = true;
var num2 = 7;
var sum = num1 + num2;
console.log(sum);
console.log(typeof sum);

打印结果：
8
number
```

```javascript
var num1 = false;
var num2 = 7;
var sum = num1 + num2;
console.log(sum);
console.log(typeof sum);

打印结果：
7
number
```

##### 强制类型转换

```javascript
var num = '5.66';
num = parseInt(num);	//转换整数型
console.log(num);
console.log(typeof num);

num = parseFloat(num);	//转换小数


num = parseFloat(num).toFixed(2);	//保留小数点后两位	但类型会转换为string类型
num = parseFloat(num).toFixed(2)-0;	//减0后转换为number类型	隐式类型转换


console.log(num);
console.log(typeof num);


```

##### 隐式类型转换

减法

左右两边都是number 进行数学的减法

有任意一个不是number 隐式类型转换 自动的转为number('5') 然后进行运算 如果不能转为例如number('哈哈') 结果为NaN(not a number)	类型为number

```javascript
var num1 = 10;
var num2 = '3';
var sum = num1 - num2;
console.log(sum);
console.log(typeof sum);


打印结果:
7
number
```

```javascript
prompt	//接受的内容 全部都是string类型
var = prompmt("请输入数字");
var = prompmt("请输入数字")-0;	//转换为number类型
var = parseInt(prompmt("请输入数字"));	//转换为整数类型
```

## 02选择结构

### 逻辑运算符

```javascript
&		//and 多个条件同时满足 结果为true 结果是 0 false或者1 非零 true
&&		//短路and 判断 只有出现false不在向后比较 直接给结果 false
|		//依次比较直到 满足条件
||		//短路或
！		//取反
```

### if else

```javascript
if(条件){
    //条件为true
    //执行的代码
}
if(条件){
    //条件为true 执行的内容
}else{
    //条件为false 执行的内容
}


var scrore = prompt;
if(scoore > 600){
    conlsole.log("你可以上211");
}else{
    console.log("没学上")
}


var scrore = prompt('请输入您的高考成绩')-0;
if(scrore <=750 && scrore >0){
    alert('输入正确');
    if(scrore > 600){
    cnsole.log('您可以上985大学')
}else if(scrore > 550){
    cnosole.log('您可以上211大学')
}else if(scrore > 450){
    console.log('您可以上普通本科')
}else if(scrore > 200){
    console.log('您可以上专科学校')
}else{
    console.log('您听说过富士康吗？')
}

}else{
    alert('请输入正确的分数')
}
```

### if else加油案例

```javascript
var oilType = prompt('请输入您家汽油的型号：92或95');
    if (oilType == 92) {
        console.log('加的92汽油')
        var oilL = prompt('请输入92号汽油的升数');
        if (oilL >= 20) {
            var money = oilL * 5.9;
            console.log('您加的' + oilType + '号汽油,加了' + oilL + '升，一共' + money + '元');
        }
    } else if (oilType == 95) {
        console.log('加的95汽油')
    } else {
        console.log('请输入正确的汽油型号：92或95');
    }
```



### 变量名命名法则

```javascript
字母	数字	_	美元符号
驼峰命名法则	第一个单词字母小写 第二个单词字母大写 首字母大写

！不能以关键字声明变量
不能以数字开头
可以以下划线开头
可以以美元符号开头
```

### switch

```javascript
!important; 	没有break会导致case击穿，所有case都执行
switch(判断的值){
    case 选项1:
        满足选项1执行的代码;
        break;
    case 选项2:
        满足选项2执行的代码;
        break;
    case 选项3:
        满足选项3执行的代码;
        break;
    default:
        执行默认
}



var day = prompt('请输入周几(1-7)');
switch (day){
    case 1:
        console.log('今天才周一，好好工作');
        break;
    case 2:
        console.log('今天周二，好好工作');
    case 3:
        console.log('今天周三，好好工作');
    case 4:
        console.log('今天周四，好好工作');
    case 5:
        console.log('今天周五，好好工作');
    case 6:
        console.log('今天周六，好好工作');
    case 7:
        console.log('今天周日，好好工作');
}
```

### 三目运算符

```javascript
?	表达式true的结果
:	表达是false的结果
var day = 2;
//			  true/false
day = day > 7 ? 1 : day
```

## 03循环结构

### 循环的特点

##### 循环结构的组成：

循环的起始值 1

循环条件 <、<=、>、>=、=、==

自增量 ++

```javascript
//1、循环起始值 (循环的时候 从哪开始)
//2、循环条件 (判断循环的起始值 是否满足条件 满足就执行 不满足 终止循环)
//3、循环体 循环操作什么
//4、循环迭代 (循环的起始值 要变化)
for(var i = 1;i<=5; i++){
    console.log('跑' + i + '圈');
}
console.log(i)	// i = 6;
```

循环10以内偶数和

```javascript
var sum = 0;	//全局变量 总的和
for(var i = 2;i <= 10;i += 2){
    console.log(i);
    sum += i;
}
console.log(sum);
```

10以内奇数和

```javascript
var sum = 0;
for(var i = 1;i<=10;i += 2){
    console.log(i);
    sum += i;
}
console.log(sum);



var sum = 0;
for(var )
```

### continue和break

```javascript
//continue	跳出本次循环继续下次循环
//break	终止整个循环
    for (var i = 1; i <= 5; i++) {
        if (i == 3) {
            continue;
        }
        console.log(i);
    }
```

折纸珠峰

```javascript
var paper = 0.0001;
var peek = 8848;
for(var i = 1;i > 0; i++){
    paper *= 2;
    console.log(paper);
    if(paper > peek ){
        console.log('对折' + i + '次超过珠峰')
        break;
    }
}
```

### while

```javascript
//循环起始值
//循环条件
//循环体
//循环迭代

while(循环条件){
    //循环操作
    //迭代部分
}
```

## 04双重for循环

#### 时钟示例循环

```javascript
for(var i = 1;i<=12;i++){
    console.log(i+'时');
    for(j=0;j<=59;j++){
        console.log(i+'时'+ j + '分');
    }
}
```

#### 九九乘法表(正序)

```javascript
    for (i = 1; i <= 9; i++) {
        for (j = 1; j <= i; j++) {
            document.write(i + '*' + j + '=' + (i * j));
            document.write('&nbsp;&nbsp;&nbsp;');
        }

        document.write('<br>');
    }
```

#### 九九乘法表(倒序)

```javascript
    for (i = 9; i >= 1; i--) {
        for (j = 1; j <= i; j++) {
            document.write(i + '*' + j + '=' + (i * j));
            document.write('&nbsp;&nbsp;&nbsp;');
        }
        document.write('<br>');
    }
```

#### 判断一个整数是几位数

```javascript
var num = 19800;
for(var i = 1;i>0;i++){
    //取整
    num = parseInt(num / 10)
    if(num == 0){
       break
       }
}
sonsole.log('是' + i + '位数');
```

#### 判断一千以内的质数

```javascript
    for (i = 2; i < 1000; i++) {
        for (j = 2; j < 1000; j++) {
            if (i % j == 0) {
                break;
            }
        }
        if (i == j) {
            document.write(i + '是质数');
            document.write('<br>');
            console.log(i + '是质数');
        }

    }
```

## 数组

#### 数组去重

```javascript
    var arr = [91, 346, 4, 5, 7, 59, 7, 0, 34, 34, 5, 327, 348, 2, 346, 324, 2, 5, 5, 64, 6, , 5324, 2, 4114, 31, 5,];
    for (i = 0; i < arr.length; i++) {
        for (j = i + 1; j < arr.length; j++) {
            if (arr[i] == arr[j]) {
                arr.splice(j, 1);
                i--;
            }
        }
    }
    arr.sort(function (a, b) {
        return a - b;
    })
    document.write(arr);
```



#### for in和for of

```javascript
for in	//数组的下标
for(var i in arry){
    console.log(i);
    console.log(arry[i]);
}


for of//数组中的每一项
for(var item of arry){
    console.log(item);
}
```

#### 去除每一项放入新数组

```javascript
var arry = [1,2,[99,88]];
//undefined
console.log(arry[0].length);
//undefined
console.log(arry[1].length);
//2
console.log(arry[2].length);


var newArry = [];
for(var item of arry){
    if(item.length != undefined){
       console.log(item,'是一个数组');
        for(var item2 of item){
            console.log(item2);
            newArry.push(item2);
        }
        continue;
       }
}





for(var i=0){
    
}
```

#### `toFixed()`

 方法将字符串四舍五入为指定的小数位数。

```javascript
let num = 5.56789;
let n = num.toFixed();
```

## 05内置对象

### 冒泡排序

让一个数字和后面的数字进行一次的比较，如果发现前面的大于后面的，就把前面的和后面的进行位置互换，外层从0开始，内层从0+1开始

代码：

```javascript
var arr = [7,8,1,4,5,6,2,3,5];
for (var i=0 ;i<arr.length;i++){
        //8 //1
  for (var j =i+1;j<arr.length;j++){
    if (arr[i]>arr[j]){
      var c = arr[i];
      arr[i] = arr[j];
      arr[j] = c;
      // document.write(arr+'<br>');//可以看到每次的变化
    }
  }
}
document.write(arr);
```



### sort排序

二进制排序，以十位数排序，只能排序1-9，,10以内排序；

```javascript
arry.sort();
```

加强排序，a-b升序，b-a降序；a前面的数据，b后面的数据；

```javascript
arry.sort(function(a,b){

	return a-b;

})；
```

### 内置对象

数组本身就是一个对象

数组的属性，长度 length

### join()拼接

```javascript
join();
//数组名.join('');
join('定义的规则')
//通过一个分隔符 把数组的所有元素拼接称一个字符串
join('-') //11-22-33-44

join('***') //11***22***33***44

arry.join('-') //调用方法，不会改变原数组
```

### Math.random()生成随机数

```javascript
Math.random()	//生成随机数
console.log(Math.random());


var arr = [1,2,3,4,5,6,7,8];
//打乱数组
arr.sort(function(a,b){
    return Math.random()>0.5 ? b-a : a-b;
});
console.log(arr);
```

### push()末尾元素添加内容

```javascript
push()	//向数组的最后面机添加内容 会改变原数组
var arry = [22,33,44];
arry.push(11);
console.log(arry);	//11,22,33,44
```

### unshift()首位元素添加内容

```javascript
unshift()	//向数组的最前面添加内容 会改变数组
var arry = [22,33,44];
arry.unshift(77,55);
console.log(arry);
```

### pop()删除末尾元素

```javascript
pop()	//删除数组末尾元素 改变原数组 没有参数
var arry = [22,33,44];
arry.pop();
console.log(arry);	//
```

### shift()删除首位元素

```javascript
shift()	//删除数组第一个元素(下表为0)元素  会改变数组 没有参数
var arry = [22,33,44];
arry.shift();
console.log(arry);
```

### concat()合并数组

```javascript
concat()	//合并数组
//a.concat(b);	a数组 合并b数组 不改变原数组 被合并的数组在后面
var arr1 = [11,22,33];
var arr2 = [77,88,99];
console.log(srr1);
arr1.concat(arr2);
var arr3 = arr1.concat(arr1);	//合并后赋值arr3	改变原数组
consle.log(arr1);
```

### splice()删除数组元素

```javascript
splice(a,b，c)	//开始删除的下标 b删除的个数 c删除后插入的内容 会改变原数组
var a = [0,1,2,3,4,5];
a.splice(2,2);
console.log(a);
```

### reverse()数组反转

```javascript
reverse()	//数组反转	会改变原数组
//数组名.reverse();	反过来
var a = [11,22,33,44];
console.log(a);
a.reverse();
console.log(a);
```

### slice()数组查找

```javascript
slice(a,b)	//数组查找 从下标a开始查找到下标b处，(不包含b)	得到一个新数组 不改变原数组
//数组名.slice()
var arr = [1,2,3,4,5,6,7,8];
//arr.slice(a)	从下标a开始查找一直查找到最后 不会改变原数组
//如果arr.slice(0)	从下标为0的位置 一直查到数组结尾 整个的查了一遍 相当于拷贝了一个新数组
var newArr = arr.slice(3,5);
console.log(arr);
console.log(newArr);
```

### 判断出现次数

```javascript
var arr = ['b','a','c','a','g','j','a','c','b'];
//遍历 判断 如果满足 ++
//定义一个变量 用来接收 次数
var index = 0;
for(var i = 0;i < arr.length;i++){
    if('a' == arr[i]){
        index++;
    }
}
console.log(index);
```

#### for in

```javascript
for in	//找到的是下标	增强型for循环
    for(var i in arr){
        console.log(i);
        console.log(arr[i]);
        if('a' == arr[i]){
            index++;
        }
    }
```

#### for of

```javascript
for of	//直接找到每一项
for(var item of arr){
    console.log(item);
    if('a' == item){
        index++;
}
```

### 内置对象之：Date

```javascript
//date	时间对象 可以获取当前的最新时间
//2023-06-06 16:53
//年 月 日 时 分 秒 星期几
var time = new Date();
console.log(time);

//找年
var year = time.getFullYear();
console.log(year);
//找月
var month = time.getMonth() + 1;
console.log(month);
month = month < 10 ? ('0'+ month) : month;
//找日
var date = time.getDate;
date = date < 10 ? ('0' + date) : date;
console.log(date);
//时
var hour  = time.getHours();
hour = hour < 10 ? ('0' + hour) : hour;
console.log(hour);
//分钟
var minute = time.getMinutes();
minute = minute < 10 ? ('0' + minute) : minute;
console.log(minute);
//秒
var second = time.getSeconds();
second = second < 10 ? ('0' + second) : second;
console.log(second)
//星期几	星期的下标
var weekArry = ['星期日'，'星期一'，'星期一二'，'星期三'，'星期四'，'星期五'，'星期六'];
var day = weekArry[time.getDay()];
console.log(day); 



var timeStr = year + '-' + month + '-' + date ' ' +hour + ':' + minute + ':' + second + day;
document.write(timeStr);
```

### 定时器

```javascript
//var index = 0;
setInterval(function(){
    //index++;
    //document.write(index);
},1000)//1000毫秒
```

### 简易时钟

```javascript
    //1、找到标签名、id、类名
    var div = document.getElementsByTagName('div')[0];  //0为下标
    setInterval(function () {
        var time = new Date();

        //找年
        var year = time.getFullYear();

        //找月
        var month = time.getMonth() + 1;
        month = month < 10 ? ('0' + month) : month;

        //找日
        var date = time.getDate();
        date = date < 10 ? ('0' + date) : date;

        //时
        var hour = time.getHours();
        hour = hour < 10 ? ('0' + hour) : hour;

        //分钟
        var minute = time.getMinutes();
        minute = minute < 10 ? ('0' + minute) : minute;

        //秒
        var second = time.getSeconds();
        second = second < 10 ? ('0' + second) : second;

        //星期几	星期的下标
        var weekArry = ['星期日', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六'];
        var day = weekArry[time.getDay()];


        var timeStr;
        timeStr = year + '-' + month + '-' + date +
            '-' + hour + ':' + minute + ':' + second + day;
        div.innerHTML = timeStr;

    }, 1000)

```

0.1+0.2==0.3?

答案是不等的

结果为：0.30000000000000004

为什么?

```javascript
因为JavaScript的number类型为双精准度IEEE 754 64位浮点类型
第0位：符号位，0表示正数，1表示负数(s)
第1位到第11位：储存指数部分(e)
第12位到63位：储存小数部分(既有效数字)
即小数后面储存52位

十进制的0.1转换
为二进制数据的时候，是无限循环的，但是s都number类型只能保存小数点后面52位，不能无限的存储所以剩下的内容会采取类似四舍五入的方式丢弃，即0舍1入所以就造成了精度的丢失
```

### String对象的方法

```javascript
var str = 'nihaolaochen'
console.log(str)//string

var str1 = new String('nihaoxiaochen');
console.log(str1);//object
```



### length

```javascript
length	//字符串的长度【属性】
console.log(str.length);
```

### charAt(a)

```javascript
charAt(a);	//返回在指定位置的字符（注：字符串中的第一个字符的下标是0，a代表下标,可以根据字符串的下标 返回对应的字符） 取不到的时候输出空字符串
//使用数组方法下标取值	没有的下标返回undefined
console.log(charAt(a));
```



### concat(b)

```javascript
concat(b)	//连接字符串，b:被合并对象名，和+的作用一样，不改变原字符串
str.concat(str2);
str = str.concat(str2);
concat(b) = str
```



### replace()

```javascript
//replace 不改变原字符串
replace(/a/,'b');	//把匹配到的第一个a 替换成b
replace('a','b');	//把匹配到的第一个a 替换成b
replace(/a/g,'b');	//把匹配到的所有的a 全部替换成b
//g		global 全局
var str = 'nihaolaochen';
var str = '你是个sb吗，会不会玩，cnm'
str = str.replce(/o/,'*');
str = str.replace('o','*');
str = str.replace(/o/g,'*');
str = str.replace(/sb/g,'**');
str = str.replace(/cnm/g,'***');
```



### split()

```javascript
split('')		//把对象根据引号内的规则分割成数组
var str = 'ni-hao-shi-jie';
var arry = str.split('-');
console.log(str);
```

### indexOf('字符')

```javascript
indexOf('字符')	//根据字符找到所在的下标位置(只返回第一个下标)；如果找不到，返回-1；
var str = 'nihaolaochen';	//str.indexOf('字符') 根据字符 返回第一个匹配到的下标
console.log('str.indexOf('o')');	//	4
console.log('str.indexOf('w')');	//	-1	-1说明当前字符串 没有要查找的内容
```

### lastIndexOf()

```javascript
lastIndexOf()	//返回一个指定的字符串值最后出现的下标位置
var str = '123.haha.aa.jpg'
console.log(str.lastIndexOf('.'));
```

### 查看字符c在字符串中的所有下标

```javascript
var str = 'abcdcfcc';
var indexArry = [];
for(var i = 0;i < str1.length;i++){
    console.log(str1.charAt(i));
    if('c' == str1.charAt(i)){
        indexArry.push(i)
    }
}
console.log(indexArry);



var str = 'abcdcfcc';
var arry = str1.split();
console.log(arry);
var indexArry = [];
for(var i = 0;i<arry.length;i++){
    if('c' == arry[i]){
        indexArry.push(i)
    }
}
console.log(indexArry);
```

### toLowerCase();

```javascript
toLowerCase();	//将字符串字母转为小写 LAOCHEN → laochen
var str = 'laoChEn'
str = str.toLowerCase();
console.log(str);
```

### toUpperCase();

```javascript
toUpperCase();	//不改变原数组 将字符串字母转为大写 laochen → LAOCHEN		LAOchen → LAOCHEN
var str = 'laochen'
str = str.toUpperCase();
console.log(str);
```

### 截取字符串的三种方法

```javascript
//对象名.substr(a,b);第一个值开始的下标位置，第二个值截取的长度	包含开始的下标	//只写一个截取到最后
var str = '你好世界我爱你';
console.log(str.substr(2));	//世界我爱你
console.log(str.substr(2,4));	//世界我爱
```

```javascript
//对象名.substring(a,b);第一个值开始的下标位置，第二个结束的下标(不包含b);	//只写一个值截取到最后
var str = '你好世界我爱你';
//	2开始的下标
//	4结束的下标 不包含结束的这一个位置
console.log(str.substring(2,4));	//世界
```

```javascript
//对象名.slice(a,b);第一个值:最开始的下标位置，第二个结束的下标(不含b)	只写一个a的时候，从a开始，一直代截取最后(使用于上面三个)
var str = '你好世界我爱你'；
//	2开始的下标
//	4结束的下标 不包含结束的这一个位置
console.log(str.slice(2,4));//世界
```

##### 数组中包含a或者A的个数

```javascript
var arr = ['America','Greece','Britain','Canada','China','Egypt'];
var num = 0;	//计数器
for(var i = 0;i < arr.length;i++){
    if(arr[i].indexOf('a') != -1 || arr[i].indexOf('A') != -1){
        num++
    }
}
console.log(num);
```

##### 练习单词首字母变大写

```javascript
var str = 'border-left-color';
var strArry = str.split('-');
console.log(strArry);
for(var i = 0;i < strArry.length;i++){
    //console.log(strArry[i]);
    //strArry[i].substr(0,1).toUpperCase()
  //console.log(strArry[i].substr(0,1).toUpperCase());
    strArry[i] = strArry[i].substr(0,1).toUpperCase() + strArry[i].substr(1);
}
console.log(strArry);
str = strArry.join('');
console.log(str);
```

##### 找文件类型

```javascript
var str ='aa.bb.cc.avi';
//找到最后一个	下标
//截取	最后一个下标 +1 截取
var index = str.lastIndexOf('.');
console.log(index);
var type = str.slice(index + 1);
console.log(type);



var str ='aa.bb.cc.avi';
str1 = str.lastIndexOf('.')
str2 = str1.substring(str1+1);
console.log(str2);
```

### Math对象

```javascript
ceil()	//对数进行上舍入	不改变原数据	数轴上最靠近右边的整数
Math.ceil(25.6);返回 26
Math.ceil(-25.5);返回-25
var num = -8.1;
num = Math.ceil(num);
console.log(num);	//-8

floor()	//对数进行下舍入	向下取值	取数轴上最靠近当前数左边的整数	不改变原始数据
Math.floor(25.5);返回 25
Math.floor(-26);返回 -26
var num = -8.9；
num = Math.floor(num);
console.log(num);	//-9

round()	//把数四舍五入为最接近的数
//正数:四舍五入
//负数：小数部分<=0.5时，相近整数更靠近右侧，所以取值右侧的整数，即原负数的整数部分不变。
//网上有人称五舍六入是不准确的！！！
Math.round(25.5);返回 26
Math.round(-25.5);返回 -26
var num = 23.2;
num = Math.round(num);
console.log(num);	//23

var num = 23.51;
num = Math.round(num);
console.log(num);	//24


Math.abs();	//求绝对值
var num = -23;
num = Math.abs(num);
console.log(num);


andom()	//返回0.0-0.1之间的随机数
Math.random();	//例如0.6273608814137365
var num = Math.random();
console.log(num);


//生成5个1=10之间的随机数
var arry = [];
for(var i = 0;i<5;i++){
    var num = Math.random()*10;
    num = Math.round(num);
    if(num < 1){
       num +=1;
       }
    arry.push(num);
}
console.log(arry);
```

#### 判断用户名输入是否正确

```html
用户名：<input type="text">
    <br>
    <button onclick="register()">注册</button>



<script>
    //函数	不会自动执行 调用的时候 才执行
    function register(){
        alert('点击注册了');
        //1、找到input框
        //2、当前input.value
        var ipt = document.getElementsByTagName('inpupt')[0];
        var name = ipt.value;
        console.log(name);
        if(name.length == 0){
           alert('用户名不能为空');
           }else if(name.length > 6){
                    alert('用户名不能大于6位数');
                    }else{
                        alert('注册成功');
                        ipt.value = '';
                    }
    }
</script>
```

#### filter过滤器

```javascript
//arry要过滤的数组
//item要过滤数组中的每一项
//return后面跟要过滤满足的条件 即满足条件的内容过滤出来 生成一个新的数组
//newArry代表过滤后生成新的数组
var newArry = arry.filter(function(item){
                          return item < 30;
                          });
```

```javascript
var arry = [17,22,35,28,29,45,50];
var ages = arry.filter(function(){
    return item < 30;
});
console.log(ages);
```

```javascript
//去假值
//只要使用Boolean() 强转 结果为false的都是假值
//null undefined '' 0 NaN false	都是假值
//var bool = Boolean(udefined);
//console.log(bool);


var arry = [null,undefined,true,false,NaN'haha','nihao',0,18];
var val = arry.filter(function(item){
    return Boolean(item);
})
console.log(val);
```

#### find

```javascript
//查找符合条件的第一个值
数组名.find(function(item){
    return item>条件
})
得到的结果，是满足条件的第一个值，如果数组种的没有任何值满足条件，则返回undefined


var num = arr.find
```

#### findIndex 返回第一个满足条件元素的下标

如果数组中的某一个元素满足条件，则返回第一个满足条件元素的下标，如果任意元素都不满足条件，则返回-1

```javascript
    var arry = [55, 66, 77];
    var val = arry.findIndex(function (item) {
        return item > 60;
    })

    console.log(val);  //1  因为66是第一个满足条件的元素 下标1 

-------------------------------------------------------------------

    var arry = [55, 66, 77];
    var val = arry.findIndex(function (item) {
        return item > 80;
    })

    console.log(val);//-1 因为没有任何一个元素满足大于80的条件
```

#### includes 判断是否包含元素

结果是true 和false

```javascript
    var arry = [55, 66, 77, 88, 99];
    var result = arry.includes(66);
    console.log(result);//true  数组中有包含的66的元素
		
		---------------------------------------------------------------------------
      
    var arry = [55, 66, 77, 88, 99];
    var result = arry.includes(55, 1); //从arry数组的查找55 从下标为1的位置向后查
    console.log(result);//false
```

### every

判断数组中的元素是否都满足函数规则

```javascript
   let numbers = [100, 200, 300, 400];

   let result = numbers.every(function (item) {
        return item > 100;
    });

   console.log(result); // false 因为 数组中的第一项不满足  >100
	-----------------------------------------------------------------------
     
    let numbers = [100, 200, 300, 400];

    let result = numbers.every(function (item) {
        return item >= 100;
    });

    console.log(result); //true  全部满足
```

## 06函数

函数数程序的基本单元，是完成任务的代码语句块

##### 函数分类：

1、系统函数

2、自定义函数

##### 函数的特征：

1、可实现一定的功能

2、可以返回一个结果

3、可以有参数



###### 函数不会立即执行，调用才会执行

```javascript
<button onclick="函数名()"></button>
```

调用函数的方法

函数变();

##### 系统函数

```javascript
parseInt();	//取整 省略小数点后面的内容 取整数
parseFloat();	//保留小数
isNaN();		//判断是否为一个数字 内存中的值 是否是一个数字

```

##### 自定义函数

```javascript
//具名无参函数	-----------
function 函数名(){
    js执行内容
}
//调用的：
//函数名()
//事件名 = '函数名()'

```

##### 参数

##### 实参

```javascript
函数的参数是按照顺序一一对应的
如果形参没有值，结果及时undefined
```



```javascript
//带参函数	----------
//写函数的时候 声明的参数	形参
//调用函数的时候 传递的参数 实参
<button onclick="fn(prompt('请输入')-0)"></button>

function fn(num){	//num形参	声名函数的时候
for(var i= 1;i<=num;i++){
    document.write(i+'老陈你好<br>');
}    
}

fn(3);	//3实参	调用的时候
```

```javascript
function fn(metal){
    document.write(metal+'狗狗');
}
fn('黄金');
```

```javascript
<button onclick="fn(prompt('请输入您的姓名'))"></button>

<script>
    function fn(name_){
    var num = Math.round(Math.random() * 10);
    if(num < 3){
       alert('大气，牛逼，富贵');
       }else if(num<7){
                alert('有磅礴之气，何愁博不得历史年荣华');
                }
    else{
        alert('虎豹之驹，虽未成纹，亦有食牛之气');
    }
}
</script>
```

#### 具名函数

```javascript
//具名函数
function fn(){
    console.log('具名函数');
}
```



#### 匿名函数

没有函数名的函数

```javascript
//匿名函数 
var fn= function(){
     console.log('匿名函数');
 }
fn();//调用

var add = function(a,b){
    console.log(a + b);
}
add(3,5);
```

#### 自执行函数

```javascript
//声明后立马调用
//好处:声明重复的变量 单独成立一作用域 在内部声明的变量 局部变量 变量名重复不影响
//防止同名变量被污染	下面变量的值覆盖上面变量的值
(function (){
    console.log('自执行函数');
})();

(function (){
    console.log('自执行函数');
}());
```

#### 显示学员信息

```javascript
<button onclick="add(prompt('请输入学员姓名'))">添加学员信息</button>
<br>
<button>显示学员信息</button>


<script>
var students = [];
function add(name){
    if(name.length == 0){
       alert('用户名不能为空，添加失败');
       }else{
           students.push(name);
           alert('添加成功');
       }
}


var show = function (){
    if(students.length == 0){
       aleret('暂时没有学员信息，无法正常显示');
       }else{
           for(var item of students){
               document.write(item+'<br>')
           }
       }
}
</script>
```

#### 函数返回值

```javascript
//return	调用函数的返回值
//函数作用域内 return 后面的内容不再执行
//函数执行到return就结束了
function fn(){
    return 5;
}
var num = fn();
console.log(num);



function bigest(a,b,c){
    //var big = (a > b ? a : b) > c ? (a > b ? a : b) : c;
    //return big
    return (a > b ? a : b) > c ? (a > b ? a : b) : c;
}
var da = bigest(3,2,8);
console.log(da);
```

调用函数加不加括号的区别

```javascript
//加括号 得到函数的返回值	才是调用函数
//不加括号 得到的是函数本身
var fn = function(){
    return 5;
}
console.log(fn);	//函数执行体本身
console.log(fn());	//5	
```

# 函数下

### 作用域

1、全局作用域

```javascript
var num = 10;
num = 10;
//不写var的时候 声明变量 默认全局变量
function fn(){
    console.log('函数内调用num:'+num);
}
fn();
console.log(num);
```

2、函数（局部）作用域

```javascript
//函数内部声明的变量 作用域：声明变量的函数内
//离当前变量 向上最近的大括号内
function fn(){
    var num =10;
    console.log('函数内调用的：'+num);
}
fn();
console.log(num);//num is not defined num这个变量找不到 意思 还没有声明

 

var num = 99;
function fn(){
    num = 10;//不加var默认全局变量	全局变量修改
    console.log('函数内调用：' + num);
}
console.log(num);//99
fn();//10
console.log(num);//10
```

### 1、代码的检查装载阶段（预编译阶段）

```javascript
//此阶段进行变量和函数的声明，但是不对变量进行赋值，变量的默认值为undefined

//大白话，就是将所有的声明（此时可理解为变量声明），都提升到最当前作用域最上面的位置，!!!有变量名，但是没有值!!!，就叫只声明不赋值，所以默认值undefined

//对变量进行提升 提升到当前作用域的最前面 只声明 不赋值
//函数 具名函数 对函数 进行提升 提升到当前作用域的最前面 整个提升 包含函数内的内容

//预编译阶段	把所有的变量	提升到最前面	只声明	不赋值


//ES6不存在变量提升
```

```javascript
//var num;

console.log(num);//undefined
var num = 18;





//函数和变量名在进行预编译阶段 进行提升的时候 变量在最前面 函数在下面
/*var num;
function fn(){
    console.log(num);//undefined
}*/

fn();
var num = 5;
function fn(){
    console.log(num);
}
```



### 2、代码的执行阶段

```javascript
//此阶段对变量进行赋值核函数的声明

//大白话：搞完步骤1以后，会对变量进行赋值。并从上向下执行

//对变量 进行一一赋值
```

```javascript
var a = 100;//全局
function fn(){
    var b = 2*a;
    var a = 200;
    var c = a / 2;
    alert(b);
    alert(c);
}
fn();
```

### 作用域链

一般情况下，变量取值是到创建这个变量的函数的作用域中取值。

但是如果在当前作用域中没有查到值，就会向上级作用域去查，直到查到全局作用域

这么一个查找过程形成的链条就叫做作用域链	

```javascript
        var x = 10;
        function f1() {
            var x = 11;
            function f2() {
                var x = 12;
                function f3() {
                    console.log(x);
                }
                f3()
            }
            f2()
        }
        f1(); //12
```

### 闭包

```javascript
function zs(){
    var ring = '祖母绿宝石戒指'
    return function (){
        return ring;
    }

}
var xpt_ = zs();
console.log(xpt_);
var ring _ = xpt();
console.log)(ring_);
```

### 闭包的优缺点

```javascript
function fn(){
    vae num = 0;
    return function(){
        num++;
        console.log(num);
    }
}
var fn1 = fn();
fn1();//1
var num =10;
fn1();//2
fn1();//3

var fn2 = fn();
fn2()；//1
fn2();//2
fn2();//3



//js垃圾回收机制	GC
//全局变量	永远在 页面关闭 变量回收
//局部变量	用完就回收
//函数	用完就回收	函数正在被人用的时候	不能回收
//内存泄露
```

## 07BOM

BOM:Browser Object Model(浏览器对象模型)

提供了独立与内容与浏览器窗口进行交互的对象

| 对象名称                     | 说明                                                         |
| ---------------------------- | ------------------------------------------------------------ |
| window                       | 窗口对象，可以用来控制当前窗口，或打开新的窗口。顶层对象，js中，最高的对象就是window |
| screen                       | 屏幕对象，获取屏幕相关信息                                   |
| navigator                    | 浏览器对象，通过这个对象可以判定用户所使用的浏览器           |
| history                      | 地址对象，可以用来前进，或后退一个页面                       |
| location                     | 地址对象，可以用来获取当前URL的信息                          |
| JavaScript计时事件           | 在一个设定的时间间隔之后来执行的代码，而不是在函数在被调用立即执行 |
| localStorage\|SessionStorage | 存储对象，可以用来存储数据和cookie向上，区别是它是为了更大容量存储设计的，在使用上也更加方便 |

#### window对象

```javascript
//window js中所有对象的父亲 是window 一切对象和属性的顶层
// window.open('http://www.baidu.com','_blank');//新窗口打开

  window.open('http://www.baidu.com','_self');//当前窗口打开 _self 新的页面覆盖当前页面 不写 打开一个新的页面
  window.close()//关闭
```

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <button onclick="close_()">点击关闭当前页面</button>
    <button onclick="open_()">打开百度</button>

</body>

</html>

<script>
    // window 
    // es5   window 是所有对象的爹  window 是js的顶层对象

    // var num = 5;
    // console.log(window.num);

    // window.alert(num);

    // function fn() {
    //     console.log('hahah');
    // }
    // window.fn();

    // console.log(window);


    //  window.close(); 关闭当前页面
    // window.open('要前往的页面路径'); 注意 参数是string类型

    function close_() {
        window.close();
    }


    function open_() {
        // window.open('http://www.baidu.com');
        window.open('./1.初识bom.html');
    }
</script>
```

#### screen对象

```html
    // screen（屏幕）对象  属性 方法 
    // height width  整个屏幕的宽高
    // availHeight  availWidth  有效的宽高 指代的 浏览器的宽高 宽是整个屏幕 高不包含下方的 tab栏
    // colorDepth 30 24 电脑屏幕决定的 屏幕深度  色彩深度  一个物理像素 包含 30种色彩


    console.log(screen);
```

#### navigator获取用户设备信息



```javascript
    // console.log(window.navigator.userAgent);
    //navigator.userAgent 可以获取到用户的设备  设备信息 设备版本
//根据navigator.userAgent 判断用户设备	Chrome Firefox chrome firefox toLowerCase
    var version_ = navigator.userAgent.toLowerCase(); //用户的设备信息
    console.log(version_);
    if (version_.indexOf('chrome') != -1) {
        alert('谷歌浏览器')
    } else {
        alert('其他浏览器')
    }

```

#### history对象

完成页面的前进跳转

history.forward();前进

history.back();后退

history.go(1)  前进一个页面

history.go(-1) 后退一个页面

```javascript
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <button onclick="forward_()">前进</button>
    <button onclick="back_()">后退</button>
    <a href="./index2.html">index1</a>
</body>

<script>
    function back_(){
        window.history.back();
    }

    function forward_(){
        window.history.forward();
    }
</script>
</html>
```

#### location对象

window.location.href = ""不赋值，获取地址

window.location.href = "地址";重定向到该地址

window.location.reload();刷新页面

```javascript

//获取URL地址
console.log(window.location.href);
location.href 赋值重定向到赋值地址 不赋值获取文件路径

    window.location.href = 'http:www.baidu.com';//重定向到百度


//reload刷新页面
window.location.reload();
```



### javascript弹窗

| 弹窗   | 语法             | 说明                                                         |
| ------ | ---------------- | ------------------------------------------------------------ |
| 警告框 | window.alert()   | 用于确保用户可以得到某些信息                                 |
| 确认框 | window.confirm() | 用于验证是否接受用户操作                                     |
| 提示框 | window.prompt    | 用于提示用户在进入页面前输入某个值,a:提示信息,b:默认值【非必填项】 |

```javascript
function delete(){
    var result = confirm('确定删除吗');
    
    //true或false
    console.log(result);
}
```



### setInterval计时器

```javascript
setInterval(function (){
    函数执行的内容
},间隔的时间)

var sum = 0;
setInterval(function (){
    sum++;
    console.log(sum);
},1000)



function 函数名(){
    函数体
}
setInterval(函数名,1000);//1000毫秒

var sum = 0;
function fn(){
    sum++;
    console.log(sum);
}
setInterval(fn,1000)



var 计时器名字 = setInterval(fn,1000)
clearInterval(计时器名字)
```

```html

<button onclick="start()">开始</button>
<button onclick="pause()">暂停</button>
<button onclick="end()">结束</button>
<script>
var timer;
var num = 0;
    function start(){
        clearInterval(timer);//防抖
        timer = setInterval(function (){
            num++;
            console.log(num);
        },1000)
    }
    function pause(){
        clearInterval(timer);
    }
    function end(){
        //清除计时器
        clearInterval(timer)
        //num 恢复0
        num = 0;
    }
</script>

```

### setTimeout定时器

```javascript
setTimeout(function (){
    执行的内容
},间隔时间)

clearTimeout(定时器名字)//清除定时器
```

无效页面返回

<a href="./error.html">百度**泄密小*妻*激*视频</a>//html第一个页面

<p>无效页面<span></span>秒后返回页面
</p>//html第二个页面
<script>
    var span = document.getElementsByTagname('span');
        var num = 5;
    var timer = setInterval(function(){
        num--;
        span.innerHTML = num;
        if(num == 0){
           clearInterval(timer);
            history.back();
           }
    },1000)
</script>



五一倒计时

```javascript
var div = document.getElementsByTagName('div')[0];
function distance(){
    var afterDate = new Date(2023,4,1);
    var nowTime = newDate();
    var distanceTime = afterTime - nowTime;
    //天
    var day =        parInt(distanceTime/1000/60/60/24);
    day = day>9?day:'0'+day
    //小时
    var day =        parInt(distanceTime/1000/60/60%24);
    h = h>9?h:'0'+h;
    //分钟
        var day =        parInt(distanceTime/1000/60%60);
    m = m>9?m:'0'+m;
    //秒
            var day =        parInt(distanceTime/1000%60);
    s = s>9?s:'0'+s;
    
    //模版字符串
    `原样输出${变量名}`
    var str = `距离2023年五一劳动节还有${day}天${h}时${m}分${s}秒`
    div.innerHTML = str
    if(day = 0 && m == 0 && h == 0 && s == 0){
       claearInterval(timer);
        div.innerHTML = '欢度五一假期'
       }
}

var timer = setInterval(distance,1000)
```



定时器弹出小广告

```html
<style>
    div{
        width:100%;
        height:100%;
        background-color:gray;
        position:absolute;
        top:0;
        left:0;
    }
    .ad{
        position:absolute;
        z-index:1;
        
    }
</style>
<body>
    <img src="./a/b/bj.jpg" alt="">
    //广告
     <img class="ad" src="./a/b/ad.jpg" alt="">
    //<div class="mask"></div>
</body>
<script>
    setTimeout(function (){
           //createElement创造元素
var maskDiv = document.createElement('div');
    maskDiv.className = 'mask'
    //maskDiv.id = 'maskId'
    //maskDiv.innerHTML = '哈哈哈我是JavaScript造出来的'
    //找到body	把造出来的div	追加到body中
    var body = document.getElemnetByTagName('body')[0];
        
        //appendChild追加子元素 父元素.appendChild(子元素);
    body.appendChild(maskDiv);
    //创造img	追加类名 添加src
    var addImg = document.createElement('img');
    addImg.className = 'ad';
    addImg.src = './img/ad.jpg';
    body.appendChild(addImg);
        //点击img的时候 删除
        addImg.onclick = function (){
           //移除子元素 父元素.removeChild(子元素); body.removeChild(addImg);
            body.removeChild(maskDiv);
        }
    },3000)
 
</script>
```

## 08DOM

DOM:document object modle	文档对象模型

dom查找html页document.body面元素

| 语法                                    | 说明                                |
| --------------------------------------- | ----------------------------------- |
| document.getElementById('Id名')         | 通过id属性获取对象                  |
| document.getElementsByTagName('标签名') | 通过标签名获取对象 返回值是一个数组 |
| document.getElementsByClassName('类名') | 通过class属性获取对象               |
| document.querySelector();               | 找到第一个类名、标签、id元素        |
| document.querySelectorAll();            | 找到所有类名，标签名元素            |

```html
<body>
<button></button>
<button class="btn"></button>
<button class="btn"></button>
<button id="btn"></button>
</body>
<script>
    //标签名查找	返回值	是数组
    var buttons = docuemnt.getElementsByTagName('button');
    buttons[0].onclick = function(){
        alert('第一个button被点中了')；
    }
    console.log(buttons);
    
    
    
    //通过类名查找	得到的是一个数组
    var  btns = document.getElementsByClassName('btn');
    btns[1].onclick = function (){
        alert('类名为btn的第二个被点中了');
    }
    console.log(btns[1]);
    
    
    //通过id查找
    var btnId_ = document.getElementById("btnId")
    btnId_.onclick = function (){
        alert('id为btnId的被选中');
    }
    
    //通过id也可以选中		！！！慎用 不是每个浏览器都支持
    btnId.onclick = function (){
        alert('id为btnId的被选中');
    }
    
    
    
    //找到页面中第一个类名是btn的元素
    var btn = document.querySelector('.btn')
     //找到页面中第一个id名是btn的元素
    var btn = document.querySelector('.btn')
     //找到页面中第一个标签名是button的元素
    var btn = document.querySelector('button')

    //找到页面所有的button标签元素	返回的是数组类型
        var btns = documentgetElementsByTagName('button')
    var btns = document.querySelectorAll('butotn')
</script>
```

### DOM操作HTML

| 语法                           |               说明               |
| ------------------------------ | :------------------------------: |
| document.write()               | 改变HTML输出流，整个页面进行重绘 |
| 操作对象.innerHTML=新的HTML    |           改变HTML内容           |
| 操作对象.attribute=新属性值    |           改变HTML属性           |
| 操作对象.style.property=新样式 |        改变操作样式的属性        |
| 操作对象.innerText=文本内容    |         在标签内插入文本         |

document.write();修改的是整个document的文档，所以添加后会覆盖整个的页面

```html
<html>
    <style>
        div{
            bacground-color:red;
        }
    </style>
    <div class="haha">老陈你好</div>
    <img src="./a/b/c.jpg">
</html>
<script>
var div = document.querySelector('div');
    
div.innerHTML = '鬼吹灯';
    
div.innerHTML = '<h1>死鬼吹灯</h1>';//插入标签和文本
    
div.innerText = '死鬼吹灯';//插入文本
    
div.className = 'hehe'
    
div.style.height = '300px'
    
div.style.backgroundColor = 'orange';
    
    var img_ = document.querySelector("img");
    
img_.src = './a/b/c/d.jpg';

//元素.style.属性 = '值';
</script>
```

```javascript
var changePic = document.getElementById('changePic');
changePic.onclick = function (){
    changePic.src = './a/b/c.jpg'
    changePic.style.width = '122px';
    changePic.style.height = '131px';
 //this 元素绑定事件的函数内 this就指向 绑定事件的当前元素
    this.src = './a/b/c.jpg';
    this.style.width = '122px';
    this.style.height = '131px';
}
```

### DOM节点之间的关系

在整个html文档中，每个元素都是为一个节点

HTML DOM将HTML文档比作树结构。这种结构被称为节点树

可以方便JS通过dom操作找到每一个节点

节点和节点之间父子关系，上下级关系，我们称之为节点的直接的关系

节点关系的好处，页面的任意一个节点，都可以通过节点关系来找到页面的任意另外的元素

### 节点属性

|     属性名称     | 描述                                                       |
| :--------------: | ---------------------------------------------------------- |
|    parentNode    | 返回节点的父亲点                                           |
|    childNodes    | 返回所有节点，包含元素节点和文本节点，换行等               |
|     children     | 返回子节点集合，只返回元素节点【标签】                     |
|    firstChild    | 返回节点的第一个子节点，最普遍的用法是访问该元素的文本节点 |
|    lastChild     | 返回节点的最后一个子节点                                   |
|   nextSibling    | 下一个节点                                                 |
| previousSibling  | 上一个节点                                                 |
| getAttributeNode | 获取属性节点                                               |

```html
<html>
	<ul class="brother">
    	<li>刘备</li>
        <li>关羽</li>
        <li>张飞</li>
        <li>赵云</li>
	</ul>
</html>
<script>
    //类名为brother的ul
    var ul_ = document.querySelector('.brother');
    
    //父节点parentNode
    console.log(ul_.parentNode);
    
    //所有的子节点 childNodes 包含换行、注释等等
    console.log(ul_.childNodes);
    
    //第一个子节点的下一个的下一个
  console.log(ul_firstChild.nextSibling.nextSibling.nextSibling);
    
    //最后一个子节点的上一个的上一个
    console.log(ul_lastChild.previousSibling.previousSibling);
    
    //最后一个子节点的上一个节点的第一个子节点的值
    console.log(ul_.lastChild.previousSibling.firstChild.nodeValue);
    
    //children 节点下的所有的子节点
    console.log(ul_.children);
</script>
```



### Element属性

加了element的属性，只返回元素节点，不再包含文本换行等文本节点

|        属性名称        | 描述                           |
| :--------------------: | ------------------------------ |
|   firstElementChild    | 返回节点的第一个子节点【元素】 |
|    lastElementChild    | 返回节点的最后一个元素子节点   |
|   nextElementSibling   | 下一个元素节点                 |
| previousElementSibling | 上一个元素节点                 |

```html
<html>
	<ul class="brother">
    	<li>刘备</li>
        <li>关羽</li>
        <li>张飞</li>
        <li>赵云</li>
	</ul>
</html>
<script>
   //元素的第一个元素子节点 
    console.log(ul_.firstElementChild);
    
    //元素第一个子节点的下一个元素节点
    console.log(ul_.firstElementChild.nextElementSibling);
    
    //元素最后一个子节点元素
    console.log(ul_lastElementChild);
    
    //元素最后一个子节点的第一个子节点的值
    console.log(ul_.firstElementChild.firstChild.nodeValue);
</script>
```

### 节点信息

| 节点信息  | 解释                                       |
| :-------: | ------------------------------------------ |
| nodeName  | 获取节点的名称，比如获取节点是什么标签     |
| nodeValue | 节点值，比如获取p标签包裹的内容            |
| nodeType  | 节点类型，有不同的数值，对应不同的节点类型 |

|   节点类型    | NodeType值 |
| :-----------: | :--------: |
|  元素element  |     1      |
| 属性attribute |     2      |
|   文本text    |     3      |
| 注释comments  |     8      |
| 文档document  |     9      |

### 操作节点属性

```html
<html>
    <img src="./a/b/c.jpg">
</html>
<script>
    var img = document.querySelector('img');
     
    //setAttribute(属性，值) 设置节点属性
   //设置图片路径属性
    img.setAttribute('src','./a/b/c.jpg');
    //设置类名属性
    img.setAttribute('class','a b');
    
    
    
    //getAttribute获取节点属性
    //获取图片路径src属性
    var src = img.getAttribute('src');
    //获取类名属性
    var className = img.getAttribute('class');
    
    
    
    //removeAttribute删除节点属性
    img.removeAttribute('src');
</script>
```

### 排他法(TAB切换)

```html
<style>
    *{
        margin:0;
        padding:0;
    }
    .header{
        width:80%;
        height:50px;
        margin:auto;
        background-color:green;
    }
    .header>a{
        text-decoration:none;
        float:left;
        text-align:center;
        line-height:50px;
        color:gray;
    }
    .header>a:nth-of-type(1){
        background-color:skyblue;
    }
    .header>a:nth-of-type(2){
        background-color:orange;
    }
    .active{
        color:red;
        font-size:35px;
        font-weight:600;
        
    }
</style>
<html>
    <div class="header">
        <a href="#" class="active">我是蓝色部分</a>
        <a href="#">我是橙色部分</a>
    </div>
    <div>
        <div class="color"></div>
        <div class="color"></div>
    </div>
</html>
<script>
    var links = document.getElementsByTagName('a');
    for(var i=0;i<links.length;i++){
        links[i].setAttribute('index',i);
        links[i].onclick = function (){
            var ind = this.getAttribute('index');
            for(var j = 0;j < links.length;j++){
                //弊端如果有多个类名，会删除所有类名，添加会覆盖原类名
                //使用 操作对象[i].classlist.remove('active');
                //使用 操作对象[ind].classlist.add('active');
                links[j].className = ''
                links[ind].className = 'active';
            }
            for(var k = 0;k < divs.length;k++){
                divs[k].style.display = 'none';
                divs[ind].style.display = 'block';
            } 
        }
    }
</script>
```

### DOM2

| 名称                              | 描述                                           |
| --------------------------------- | ---------------------------------------------- |
| document.createElement("元素名"); | 创建元素节点                                   |
| document.createTextNode("文本");  | 创建文本节点                                   |
| A.appendChild(B);                 | 把B节点追加至A节点的末尾，A节点就是父节点      |
| parent.insertBefore(A,B);         | 把A节点插入到B节点之前。parent插入元素的父元素 |
| a.cloneNode(deep);                | 复制某个指定的节点：a表示被复制的节点          |

克隆节点：a.cloneNode(deep);

a表示要复制的节点

deep:默认false浅复制：只复制当前节点对象本身

deep:true深复制：复制当前节点以及所有后代节点对象

#### appendChild追加，createElement创建元素

```javascript
var div_ = document.createElement('div');
//添加类名
div_className = 'b';
var box = document.querySelector('box');
//创建的元素追加插入到某个元素中
box.appendChild(div_);
```

#### 创建文本节点

```javascript
//创建文本节点
var text = document.createTextNode('哈哈哈');
//创建的元素追加插入到某个元素中
div_.appendChild(text);
```

#### 追加到某节点之前

```html
<script>
//插队 插入元素
//父元素 box
//要插入的：div_
//被插入的：<div class="a"></div>
//父元素.insertBefore(a,b);	a要插入的节点 b被插入的节点
var adDiv = document.querySelector('.a');
box.insertBefore(div_,aDiv);
</script>

<html>
    <body>
        <ul class="list">
            <li>刘备</li>
            <li>关羽</li>
            <li>张飞</li>
        </ul>
    </body>
</html>
<script>
    var li4 = createElement('li');
    li4.innerHTML = '赵云';
    var list = document.querySelector('.list');
    var bInsert = document.getElementsByTagName('li')[0];
    list.insertBefore(li4,bInsert);
 list.insertBefore(li4,list.firstElementChild);    
</script>




```

#### 克隆节点

```javascript
//var b = a.cloneNode();括号内不写默认 false浅拷贝
var b = a.cloneNode(true);b 就是a节点拷贝过来的 带上子子孙孙
var b = a.cloneNode(false);b就是a节点拷贝过来的 只拷贝最外层的节点 a
```



### 删除和替换节点

| 名称                                 | 描述                         |
| ------------------------------------ | ---------------------------- |
| 父节点.removeChild(子节点)           | 删除指定的节点               |
| 父节点.replaceChild(newNode,oldNode) | 用其他的节点替换成指定的节点 |

#### removeChild&replaceChild(删除和替换节点)

```html
<html>
    <body>
        <img src="./a/b/c.jpg" onclick="removeImg()" alt="">
    </body>
</html>
<script>
function removeImg(){
    var img = document.querySelector('img');
    img.parentNode.removeChild(img);
    }
    
    
    
    function removeImg(){
    var p = document.createElement('p');
    p.innerHTML = '松下问童子'
    var img = document.querySelector('img');
    img.parentNode.replaceChild(p,img)
    }
</script>
```



### this指向有哪些(目前所学)面试题重点

  1、在普通函数中 			  this指向window

  2、在自执行函数中 		  this指向window

  3、在计时器中				  this指向window

  4、在定时器中 				 this指向window

  5、在事件调用函数中 	  this指向当前事件的调用者

  6、在对象的方法中 		  this指向当前对象

  7、在构造函数中使用this，this指向当前构造函数创建的实例。（new 构造函数得到的对象）

  8、在构造函数的原型对象中，this依然指向当前构造函数的实例对象

### 基础事件

| 名称        | 描述                         |
| ----------- | ---------------------------- |
| onclick     | 当用户单击对象调用是调用事件 |
| onmouseover | 鼠标移到某元素之上           |
| onmouseout  | 鼠标从某元素移开             |
| onmousedown | 鼠标按钮被按下               |

```html
<html>
    <p onclick="del(this)">删除</p>
</html>
<script>
function del(that){
    //console.log(that.parentNode.parentNode);
    //父节点.removeChild('被删除的节点');
    var ul = that.parentNode.parentNode;
    ul.parentNode.removeChild(ul);
}
</script>
```

### 通过DOM操作style属性

```html
<html>
    <head>
    <style>
        div{
            width:400px;
            border:2px solid gray;
        }
    </style>
    </head>
    <body>
        <div class="box" style="height:200px;"></div>
    </body>
</html>
<script>
    //dom js 设置 css样式 style样式
    //操作的dom对象.style.属性 = '值';
    var box = document.querySelector('.box');
    box.style.backgroundColor = 'orange';
    
    //获取属性值
   //元素.style.属性	只能获取行内样式和js设置生成的样式	内联的和外联的获取不到
    console.log(box.style.height);//200px
    console.log(box.style.backgroundColor);//orange
    console.log(box.style.width);//为空 获取不到
    //style.属性 只能获取标签内的样式行内样式	内联外联获取不到
    
    
    
    
    //可以获取一切style样式属性的值
    
    //方法一document.defaultView.getComputedStyle(元素,null).属性;    //defaultView	默认视图
    
    //方法二
    //window.getComputedStyle(元素,null).属性;

    var w = document.defaultView.getComputedStyle(box).width;
    console.log(w);//400px
     var h = document.defaultView.getComputedStyle(box).height;
    console.log(h);//200px
    
    //computed 计算属性 [vue]
    var color_ = window.getComputedStyle(box).backgroundColor;
    console.log(color_);//拿到的颜色是rgb类型
</script>
```

### className属性

```html
<html>
    <body>
        <div>哈哈哈，我是div，整类名的</div>
    </body>
</html>
<script>



    //1、添加一个类名 js添加的类名 会覆盖 html 中设置的类名
    var div = document.querySelector('div');
    div.className = 'a21';//覆盖原设置的类名
    
//2、添加多个类名 覆盖html中的类名    
div.className = 'a1 a2';//添加多个类名覆盖原类名
    
//3、同是我保留 js设置的类名 和htm 的类名 
    div.className += ' a1'
    div.id = 'ids';//添加id
    console.log(div.className);//获取类名
</script>

```

### HTML中元素属性

| 属性         | 说明                                                         |
| ------------ | ------------------------------------------------------------ |
| offsetLeft   | 返回当前元素左边界到它上级元素的左边界距离，只读属性         |
| offsetTop    | 返回当前元素上边界到它上级元素的上边界的距离，只读属性       |
| offsetHeight | 返回元素的高度，包含边框                                     |
| offsetWidth  | 返回元素的宽度，包含边框                                     |
| offsetParent | 返回元素的偏移容器，即当前容器距离最近的带定位属性的父元素，如果没有返回body |
| scrollTop    | 返回匹配元素的滚动条的垂直位置                               |
| scrollLeft   | 返回匹配元素的滚动条的水平位置                               |
| clientWidth  | 返回元素的可见宽度，不包含边框                               |
| clientHeight | 返回元素的可见高度，不包含边框                               |

```html
<html>
    <head>
        <style>
            *{
                margin:0;
                padding:0;
            }
            .main{
                width:70%;
                margin:auto;
            }
            .main>img{
                width:100%;
            }
            /*广告和叉号*/
            .adv{
                position:absoute;
                top:50px;
                left:50px;
            }
            .close{
                position:absolute;
                top:60px;
                left:145px;
            }
        </style>
    </head>
    <body>
         <img src="./a/b/c.jpg" alt="" class="adv">
         <img src="./a/b/c.jpg" alt="" class="close" onclick="advClose">
        <div class="main">
        <img src="./a/b/c.jpg" alt="">
        </div>
    </body>
</html>
<script>

    function advClose(){
            var adv = document.querySelector('.adv');
        var close_ = document.querySelector('.close');
        adv.parentNode.removeChild(adv);
        close_.parentNode.removeChild(close_);
    }
    //页面加载完成就执行
    
    
    var closeTop;//叉号距离父元素上边的距离
    var closeLeft;//叉号距离父元素左边的距离
    var advTop;//广告距离父元素上边的距离
    var advLeft;//广告距离父元素左边的距离
    window.onload = function(){
        var domClose = document.querySelector('.close');
        closeTop = domClose.offsetTop;
        closeLeft = domClose.offsetLeft;
    }
    window.onscroll = function(){
        var scrolTop = document.documentElement.scrollTop;
        //设置adv的定位值
        var domAdv = document.querySelector('.adv');
        domAdv.style.top = scrollTop + advTop + 'px';
        var domClose = document.querySelector('.close');
        domClose.style.top = scrollTop + closeTop + 'px'
    }
</script>
```

#### 放大镜

```html
<html>

<head>
    <style>
        * {
            margin: 0;
            padding: 0;
        }

        .list {
            width: 640px;
            height: 340px;
            border: 2px solid gray;
        }

        li {
            width: 200px;
            height: 100px;
            background-color: orange;
            list-style: none;
            float: left;
            margin-left: 10px;
            margin-top: 10px;
            text-align: center;
            line-height: 100px;
            font-size: 30px;
            color: white;
        }

        .active {
            width: 400px;
            height: 200px;
            position: absolute;
            top: 50%;
            left: 50%;
            transform: translate(-50%, -50%);
            text-align: center;
            line-height: 200px;
        }

        .mb {
            width: 640px;
            height: 340px;
            background-color: rgba(61, 61, 61, .7);
            position: absolute;
            top: 0;
            left: 0;
        }
    </style>
</head>

<body>
    <ul class="list">
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
        <li>5</li>
        <li>6</li>
        <li>7</li>
        <li>8</li>
        <li>9</li>
    </ul>
</body>

</html>
<script>
    var list = document.getElementsByClassName('list')[0].children;
    for (var li of list) {
        li.onclick = function () {
            var bigLi = this.cloneNode(true);
            //创建蒙版
            var mb = document.createElement('div');
            mb.className = 'mb';
            
            bigLi.className = 'active';
            mb.appendChild(bigLi); document.querySelector('body').appendChild(mb);
            mb.onclick = function () {

                //事件流的冒泡型	要 阻止冒泡
                this.parentNode.removeChild(this);
            }
        }
    }
</script>
```



### 元素属性的应用：

语法标准浏览器

```javascript
document.documentElement.scrollTop;
document.documentElement.scrollLeft;
```

谷歌浏览器

```javascript
document.body.scrollTop;	//废除
document.body.scrollLeft;
```

兼容写法

```javascript
var sTop = document.documentElement.scrollTop||document.body.scrollTop;
```

offsetParent:

返回距离当前元素最近的具有定位属性的元素

如果没有，则返回body

## 09事件

## JavaScript事件

###### 事件是文档或者浏览器窗口中发生的，特定的交互瞬间

典型事例：

页面加载完毕，触发load事件

浏览器窗口放大或缩小，触发resize事件

用户单击元素，触达click事件

绑定事件的方法

```html
<html>
    <body>
        <button onclick="fn1()">普通绑定</button>
        <button>事件绑定</button>
        <button>事件监听</button>
    </body>
</html>
<script>
    function fn1(){
        alert('普通绑定');
    }
    var btns = document.getElementsByTagName('button');
    btns[1].onclick = function (){
        alert('事件绑定');
    }
   
    
    btns[2].addEventListener('click',function (){
        alert('添加事件监听');
    }，false);
    //false 冒泡型事件 不写默认false
    //true	捕获型事件 
</script>
```

###### 普通事件和事件监听的区别

```html
<html>
    <body>
        <button onclick="fn1()">普通绑定</button>
        <button>事件监听</button>
    </body>
</html>
<script>
    //普通事件 如果同时绑定多个相同事件 只执行最后绑定的事件
  var btns = document.getElementsByTagName('button'); 
    btns[0].onclick = function (){
        alert('弹框一');
    }
    btns[0].onclick = function (){
        alert('弹框二');
    }
    
    //事件绑定监听 如果同时绑定多个事件 就会按照代码的前后顺序 全部执行
    btns[1].addEvenListener('click',function (){
        alert('事件绑定一');
    })
     btns[1].addEvenListener('click',function (){
        alert('事件绑定二');
    })
     btns[1].addEvenListener('click',function (){
        alert('事件绑定三');
    })
        
</script>
```

### 事件流

//所有事件默认都是冒泡型

//捕获型事件流 只有在addEventListener事件监听第三个参数为true的时候才会触发

嵌套的父子元素 上级和下级 都绑定了相同事件

#### 10秒钟倒计时

```html
<html>
    <head>
        <style>
            *{
                margin:0;
                padding:0;
            }
            span{
                color:red;
            }
        </style>
    </head>
    <body>
        <span>10</span>
        <br>
         <button>开始</button>
         <button>暂停</button>
        <button>重置</button>
    </body>
</html>
<script>
    var span=document.quetySelector('span');
    var btns=document.getElementsTagName('button');
    btns[0].onclick=function(){
        clearInterval(timer);
        timer=setInterval(function(){
            num--;
            if(num<=0){
                num=0;
                cleaerInterval(timer);
            }
            span.innerHTML=num;
        },1000)
    }
    btns[1].onclick=function(){
        clearInterval(timer);
    }
    btns[2].addEventListener('click',function(){
        span.innerHTML=10;
        num=10
        clearInterval(timer);
    });
</script>
```

| 事件名       | 描述                             |
| ------------ | -------------------------------- |
| onclick      | 鼠标 点击某个对象 单击           |
| ondbclick    | 鼠标双击某个对象                 |
| onmouseover  | 鼠标被移到某元素之上【伤及子孙】 |
| onmouseout   | 鼠标从某元素移开【伤及子孙】     |
| onmousedown  | 某个鼠标按键被按下               |
| onmouseup    | 某个鼠标按键被松开               |
| onmousemove  | 鼠标被移动                       |
| onmouseenter | 鼠标从元素移入【不伤及子孙】     |
| onmouseleave | 鼠标从元素移出【不伤及子孙】     |

```javascript
onmouseover、onmouseout:鼠标移动到自身时候会触发事件，同时移动到其子元素也会出发事件
onmouseenter、onmouseleave:鼠标移动到自身时会触发事件，但是移动到其子元素不会触发事件
```

```html
<html>
    <head>
        <style>
            .a{
                width:80%;
                height:600px;
                background-color:orange;
                overflow:hidden;
            }
            .b{
                width:60%:
                height:300px;
                margin:auto;
                margin-top:150px;
                background-color:white;
            }
        </style>
    </head>
    <body>
        <div class="a">
            <div class="b"></div>
        </div>
    </body>
</html>
<script>
    var a = document.querySelector('.a');
    var b = document.querySelector('.b');

    // a.onclick = function () {
    //     alert('单击')
    // }
    // a.ondblclick = function () {
    //     alert("双击")
    // }

    // a.addEventListener('dblclick', function () {
    //     alert('事件监听双击')
    // })

    // 伤及无辜  3个0  三菱  日本

    // a.onmouseover = function () {
    //     console.log('a鼠标移入了,over');
    // }
    // a.onmouseout = function () {
    //     console.log('a鼠标离开了 out');
    // }

    // a.onmouseenter = function () {
    //     console.log('a鼠标移入 enter');
    // }

    // a.onmouseleave = function () {
    //     console.log('a鼠标移入 leave');
    // }



    a.onmousedown = function () {
        console.log('a鼠标按下了');
    }

    a.onmouseup = function () {
        console.log('鼠标抬起来');
    }

    a.onmousemove = function () {
        console.log('鼠标移动');
    }
</script>
```

### 表单事件

| 事件名   | 描述                           |
| -------- | ------------------------------ |
| onfocus  | 元素获得交点                   |
| onblur   | 元素失去焦点                   |
| onchange | 用户改变域的内容               |
| onreset  | 表单重置时触发【绑定在form上】 |
| onsubmit | 表单提交时触发【绑定在form上】 |
| oninput  | 用户输入时                     |

```html
<html>
    <head>
        <style>
        	
        </style>
    </head>
    <body>
            <!-- <form action="" onreset="reset_()" onsubmit="sub_()"> -->
    <input type="text" autofocus>
    <div></div>
    <input type="reset" value="重置">
    <input type="submit" value="提交">
    <!-- </form>  -->
    </body>
</html>
<script>

    var ipt = document.querySelector('input');
    var div = document.querySelector('div');
    // ipt.onfocus = function () {
    //     console.log('focus获取焦点');
    // }

    // ipt.onchange = function () {
    //     console.log('change触发');
    // }


    // ipt.onblur = function () {
    //     console.log('失去焦点');
    // }


    ipt.oninput = function () {
        // console.log('输入时出发');
        var val = ipt.value;
        div.innerHTML = val;
    }

    function reset_() {
        console.log('重置了');
    }

    function sub_() {
        console.log('提交');
    }

</script>
```

### 键盘事件

| 事件名     | 描述                                   |
| ---------- | -------------------------------------- |
| onkeydown  | 某个键盘的按键被按下                   |
| onkeypress | 某个键盘的按键被按下并释放一个键时发生 |
| onkeyup    | 某个键盘的按键被松开                   |

键盘事件的事件的次序：onkeydown、onkeypress、onkeyup

```html
<html>
    <head>
        <style>
            div{
                width:400px;
                height:200px;
                border:2px solid gray;
            }
        </style>
    </head>
    <body>
        <div contenteditable></div>
    </body>
</html>
<script>
	var div_ =document.querySelector('div');
    div_onkeydown=function(){
        console.log('键盘被按下了');
    }
    div_.onkeypress=function(){
        console.log('按下抬起的一瞬间');
    }
    div_onkeyup=function(){
        console.log('键盘松开了');
    }
</script>
```

### UI事件

| 事件名   | 描述                     |
| -------- | ------------------------ |
| onload   | 某个页面或图像被完成加载 |
| onresize | 窗口或框架被调整尺寸     |
| onscroll | 当文档被滚动时发生的事件 |

```html
<html>
    <head>
        <style>
            div{
                width:80%;
                margin:auto;
                background-color:orange;
                overflow:hidden;
            }
            h1{
                background-color:white;
                width:50%;
                margin:10px auto;
            }
        </style>
    </head>
    <body>
        <div></div>
    </body>
</html>
<script>
    window.onload=function(){
        console.log('页面加载完成');
    }
	window.onscroll=function(){
        var top = document.documetElement.scrollTop;
        console.log(top);
    }
    window.onresize=function(){
        console.log('页面大小重置');
    }
</script>
```

### 微博评论减字功能

```html
<html>
    <head>
        <style>
        	
        </style>
    </head>
    <body>
        <textarea id="txt" cols="30" rows="10" maxlength="10"></textarea>
        <br>
        <span>你还可以输入40个字</span>
    </body>
</html>
<script>
	var txt = document.getElementById('txt');
    var span = document.getquerySelector('span');
    txt.onkeyup=function(){
        var len=txt.getAttribute('maxlength');
        console.log('length');
        span.innerHTML=`你还可以输入${len-txt.value.length}个字符`
    }
</script>
```

### 制作表单用户名输入

```html
<html>
    <head>
        <style>
        	
        </style>
    </head>
    <body>
        用户名<input type="text">
        <span></span>
    </body>
</html>
<script>
	var ipt==document.querySelector('input');
    var span = document.querySelector('span');
    ipt.onfocus=function(){
        this.style.color='red'
        span.innerHTML='用户名6-12位'
    }
    ipt.addEventListener('blur',function(){
        var len = this.value.length;
        if(len>=6&&len<=12){
           span.innerHTML='用户名正确';
            span.style.color='green';
           }else{
               span.innerHTML='格式错误，用户名6-12位';
               span.style.color='red';
           }
    })
</script>
```

### JavaScript事件二

### 键盘事件对象

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        div {
            width: 400px;
            height: 200px;
            border: 1px solid gray;
        }
    </style>
</head>

<body>
    <div contenteditable="""true"></div>
</body>

</html>
<script>
    var div = document.getElementsByTagName('div')[0];
    div.onkeyup = function (e) {
        e = e || window.event;
        console.log(e);
        console.log(e.key);
        console.log(e.keyCode);
        if (e.key == 'Enter') {
            alert('发送了');
        }
        if (e.key == 'Enter' && e.ctrlKey) {
            alert('又发送了');
        }
    }
</script>
```

### event对象

用来获取事件的详细信息：鼠标位置、键盘按键

就是一个js对象，里面包含了事件的详细具体信息

获取even对象（兼容性写法）

#### 语法

```javascript
oEvent=e||window.event;//兼容ie
```

示例：

### event对象放在事件处理函数中

```javascript
document.onclick=function(e){
    oEvent(oEvent.clientX+','+oEvent.clientY);
}
```

### 查看event对象：

```html
<html>
    <head>
        <style>
        	
        </style>
    </head>
    <body>
        <div></div>
    </body>
</html>
<script>
	var div=document.querySelector('div');
    div.onclick=function(e){
        console.log(e);//打印事件对象
    }
</script>
```

```html
<html>
    <head>
        <style>
        	
        </style>
    </head>
    <body>
        <button>点击</button>
    </body>
</html>
<script>
	var btn=document.getElementsByTagName('button');
    btn[0].onclick=function(){
        //e:谷歌浏览器 e就指代当前事件
        //ie8及以下 不支持e window。event
        e=e||window.event;
        console.log(e);
    }
</script>
```

| 属性          | 描述                                                         |
| ------------- | ------------------------------------------------------------ |
| altKey        | 返回当事件被触发时“ALT”是否被按下                            |
| button        | 返回当事件被触发时，哪个鼠标按钮被点击。0左键 1中间键 2右键  |
| clientX       | 返回当事件被触发时鼠标指针相对于浏览器页面（或客户区）的水平坐标客户区指的浏览器的有效区域【dom左】 |
| clientY       | 返回当事件被触发时鼠标指针相对于浏览器页面（或客户区）的垂直坐标客户区指的浏览器的有效区域【dom上】 |
| ctrlKey       | 返回当事件被触发时，“CTRL”键是否被按下                       |
| metaKey       | 返回当事件被触发时，“meta”键是否被按下。window键，command键  |
| relatedTarget | 返回与事件的目标节点相关的节点。                             |
| screenX       | 返回当某个事件被触发时，鼠标指针的水平坐标。鼠标想丢与显示器屏幕的X轴的位置 |
| screenY       | 返回当某个事件被触发时，鼠标指针的垂直坐标。鼠标相对于显示器的Y轴的位置 |
| shiftKey      | 返回当事件被触发时，“SHIFT”键是否被按下                      |
| pageX         | 返回的值：当前点击的点，距离整个页面最左边的距离             |
| pageY         | 返回的值：当前点击的点，距离整个页面最上面边的距离【e.clientY+scrollTop】 |

```javascript
clientX&clientY点击位置距离浏览器dom区域 left和top的距离

offsetX&offsetY点击位置 距离点击元素的X和Y的距离

screenX&screnY距离整个屏幕	left和top的距离

pageX&pageY距离整个页面和上面滚动后的距离
```

### 键盘按键事件

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        div {
            width: 400px;
            height: 200px;
            border: 1px solid gray;
        }
    </style>
</head>

<body>
    <div contenteditable="""true"></div>
</body>

</html>
<script>
    var div = document.getElementsByTagName('div')[0];
    div.onkeyup = function (e) {
        e = e || window.event;
        console.log(e);
        console.log(e.key);
        console.log(e.keyCode);
        if (e.key == 'Enter') {
            alert('发送了');
        }
        if (e.key == 'Enter' && e.ctrlKey) {
            alert('又发送了');
        }
    }
</script>
```

### 阻止冒泡

语法：

```
非ie:event.stopPropagation();
兼容ie:cancelBubble=true;
```

### 右键事件

```javascript
document.oncontextmenu=function(){
	alert('右键');
}
```

### 阻止默认事件

```javascript
document.oncontextmenu=function(){
    e.preventDefault();//非ie
    e.returnValue=false;//兼容ie
	alert('右键');
     //1、e.preventDefault();//非ie
    //2、e.returnValue=false;//兼容ie
    
    //3、之间在事件执行函数的最后return false;
    return false;
}
```

### 自定义菜单

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>右击菜单</title>
    <style>
        * {
            margin: 0;
            padding: 0;
        }

        #menu {
            width: 200px;
            height: 310px;
            background-color: antiquewhite;
            display: none;
            border-radius: 10px;
            position: absolute;
        }

        #menu>li {
            line-height: 30px;
            list-style: none;
            margin: 10px auto;
            padding: 5px 20px;
            border-radius: 10px;
        }
    </style>
</head>

<body>
    <ul id="menu">
        <li>添加图标</li>
        <li>添加小组件</li>
        <li>随机壁纸</li>
        <li>下载壁纸</li>
        <li>编辑主页</li>
        <li>搜索图标</li>
    </ul>
</body>

</html>
<script>
    var menu = document.getElementById('menu');

    document.oncontextmenu = function (e) {
        e.preventDefault();
        menu.style.display = 'block';

        //鼠标指针相对于dom的点击坐标X轴
        var clickLeft = e.clientX;
        //鼠标指针相对于dom的点击坐标Y轴
        var clickTop = e.clientY;

        var marginLeft = clickLeft + 200;
        var marginTop = clickTop + 310;
        console.log(marginLeft, marginTop);


        var clientWidth = document.documentElement.clientWidth;
        var clientHeight = document.documentElement.clientHeight;

        var left = marginLeft > clientWidth ? clientWidth - 220 : clickLeft + 20;
        var top = marginTop > clientHeight ? clientHeight - 330 : clickTop + 20;


        menu.style.left = left + 'px';
        menu.style.top = top + 'px';


        //浏览器DOM区域的宽
        //document.documentElement.clientWidth
        //window.innerWidth

        //浏览器DOM区域的高
        //document.documentElement.clientHeight
        //window.innerHeight

        // 事件对象的宽
        // 对象.offsetWidth包含边框

        // 对象的高
        // 对象.offsetHeight包含边框
    }
    menu.onclick = function () {
        window.event ? event.cancelBubble = true : event.stopPropagation();
    }
    document.onclick = function () {
        menu.style.display = 'none';
    }
    menu.onmouseenter = function () {
        var li = menu.children;
        var str;
        for (i = 0; i < li.length; i++) {
            var str = '#';
            for (j = 0; j < 6; j++) {
                str += (parseInt(Math.random() * 16).toString(16));
            }
            li[i].style.backgroundColor = str;
        }
    }
</script>
```

### 防抖节流

### 防抖：

>      连着点了好多次，我们想要点击停止后间隔一定的时间 执行一次
>
>      一些频繁触发的事件，我们不想让它频繁执行，比如 keyup scroll resize mousemove
>
>      不想让它如此频繁，执行停止后间隔一定的时间执行 就用防抖
>
>      应用场景： 比如搜索框联想
>
>      总结：防止点击多次后重复叠加，每次点击都清空，只执行最后一次

### 节流


>     不论执行的频率有多高 ，我们总是让间隔一定的时间执行一次
>
>      一些频繁触发的事件，我们想让它频繁执行，但不想那么的频繁，节制一点
>
>     比如 keyup scroll resize mousemove
>
>     不想让它如此频繁，执行停止后间隔一定的时间执行 就用防抖
>
>     应用场景： 比如拖拽内容
>
>     总结：防止点击频率过高，限制执行频率，每间隔一段后执行一次


### 使用lodash库完成防抖节流

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <button>点击防抖</button>
    <button>点击节流</button>
</body>

</html>
<!-- 1.引入lodash库 -->
<script src="./lib/lodash.js"></script>

<script>
    var btn = document.querySelectorAll('button');
    // 防抖 debounce  去抖动
  
   // 2. 使用_.debounce 防抖函数
    btn[0].onclick = _.debounce(function () {
        console.log('执行了');
    }, 1000)


    // 节流 throttle
  
    //3. 使用_.throttle 节流函数
    btn[1].onclick = _.throttle(function () {
        console.log('节流执行了');
    }, 1000)


</script>
```

## 10正则表达式

语法：

```javascript
//构造函数：
var reg=new RegExp(pattern),modifiers;
如：
				 //校验规则//修饰符
var reg=new RegExp('[a-z]*','g');
var str='hello';
console.log(reg.test(str));



//字面量：
var reg=/pattern/modifiers;

如：
var str='hello';
var reg=/[a-z]/i;
console.log(reg.test(str));
```

### 修饰符：

| 修饰符 | 描述                                                   |
| ------ | ------------------------------------------------------ |
| i      | 执行对大小写不敏感的匹配                               |
| g      | 执行全局匹配(查找所有匹配而非在找到第一个匹配后停止)。 |
| m      | 执行多行匹配                                           |

### 常用的表达式

| 表达式 | 描述                                                         |
| ------ | ------------------------------------------------------------ |
| [a-z]  | 查找任何从小写a到小写z的字符 -表示区间                       |
| [A-Z]  | 查找任何从大写A到大写Z的字符                                 |
| [0-9]  | 查找任何从0至9的数字                                         |
| [abc]  | 查找括号内的任意一个字符                                     |
| [^abc] | 查找除了括号内的任意字符。除了abc如果还有其他任意字符为true，否则false |

### 常用的元字符(特殊字符)

| 字符 | 描述                     |
| ---- | ------------------------ |
| \w   | 匹配数字、字母、下划线   |
| \W   | 匹配非数字、字母、下划线 |
| \d   | 匹配数字                 |
| \D   | 匹配非数字               |
| \s   | 匹配空白字符(空格、换行) |
| \S   | 匹配非空白字符           |
| \n   | 匹配换行符               |

### 常用的限定字符

| 字符  | 描述                         |
| ----- | ---------------------------- |
| *     | 匹配前面的子表达式零次或多次 |
| +     | 匹配前面的子表达式一次或多次 |
| ?     | 匹配前面的子表达式零次或一次 |
| {n}   | 匹配确定的n次                |
| {n,}  | 至少匹配n次                  |
| {n,m} | 最少匹配n次且最多匹配m次     |
| ^     | 以某某开头                   |
| $     | 以某某结尾                   |
| \     | 转义字符                     |

*零次或者多次

```js
var str = 'abcd';

//var reg = /[a-z]*/;// a-z 出现0 次 或者多次
var reg = /\w*/;// 字母｜数字｜下划线 出现0 次 或者多次
console.log(reg.test(str));  //true
```
+一次或者多次

```js
var str = 'abcd';
// var reg = /[0-9]+/;// 0-9 出现1次 或者多次
var reg = /\d+/;// 数字出现 1次 或者多次
console.log(reg.test(str));  //false
```
？0次或者1次


```js
   var str = '12';
   var reg = /^\d?$/;// 以数字开始结束  数字出先0次或者1次
   console.log(reg.test(str));  //false
var str = '1';

var reg = /^\d?$/;// 以数字开始结束  数字出先0次或者1次
console.log(reg.test(str));  //true
```
{n},固定的n次 ，要和开始结束结合使用

```js
  // var str = 'a';//false
    var str = 'ab';//true
    var str = 'abc';//false

    var reg = /^\w{2}$/;//字母数字下划线 从开始到结束 只能出现2次
    console.log(reg.test(str));
```
{n,}  至少匹配n 次

```js
var str = 'a';//false
// var str = 'ab';//true
// var str = 'abc';//true

// var reg = /^\w{2,}$/;//至少出现两次
var reg = /\w{2,}/;//至少出现两次
console.log(reg.test(str));
```
{n,m}  最少匹配 n 次且最多匹配 m 次



```js
 var str = 'a';//false
    // var str = 'ab';//true
    // var str = 'abc';//true
    // var str = 'abcd';//false
var reg = /^\w{2,3}$/;//至少出现两次，最多出现3次
console.log(reg.test(str));
```
\  转义字符

```js
// var str = 'a.com';//true
var str = 'acom';//false
var reg = /\./;// 转义 判断是否包含 .
console.log(reg.test(str));
```
```js
  var phone =13140172111;
    // var reg = /^1[3-9][0-9]{9}$/;
    var reg = /^1[3-9][0-9]{9}$/;
    console.log(reg.test(phone));
```

匹配以a开头，以d结尾：

```js
var str = 'abcd';
var reg = /^[a]\w*[d]$/;
console.log(reg.test(str));
```


### 正则表达式方法

检测一个字符串是否与正则相匹配
reg.test(string)           返回值为布尔值 true匹配，false不匹配
reg.exec(string)          匹配成功返回数组，并确定其位置，否则返回null 

                                      只返回匹配到的第一个内容  包含 查找的值 对应的下标



示例：

```js
var str="abc";
var reg=/[a-z]/;   var reg=/[A-Z]/;
console.log(reg.test(str));  
console.log(reg.exec(str));

```



### String对象中可以支持正则表达式的方法

| 方法    | 描述                                                         |
| :------ | ------------------------------------------------------------ |
| search  | 检索与正则表达式相匹配的值。查找不到返回-1，查到返回第一个匹配到的下标 |
| match   | 检索一个或多个正则表达式的匹配，如果没有找到任何匹配的文本，返回null。否则它将返回一个数组(依赖于是否有全局标识 g) |
| replace | 替换与正则表达式匹配的子串 返回一个新的字符串                |
| split   | 把字符串分割为字符串，返回一个字符串数组                     |

```js
 var str = 'hello WorLd';
    var reg = /[A-Z]/;
    console.log(str.search(reg));//6 下标
```

```js
 var str = 'hello WorLd';
    var reg = /[A-Z]/g;
    console.log(str.match(reg));//[W,L] 是否返回数组 取决于正则是否加了g
```

```JS
 var str = 'helloWorLd';
    var reg = /[A-Z]/;
    console.log(str.split(reg));//["hello", "or", "d"]
```

```js
  var str = 'helloWorLd';
    var reg = /[A-Z]/;

    console.log(str.replace(reg,'*'));//hello*orLd
```

### 正则验证

验证26个英文字母组成的字符串
验证由数字和26个英文字母组成的字符串
验证由数字、字母、下划线组成的字符串
验证汉字   var reg=/^[\u4e00-\u9fa5]+$/



```js
  // 验证26个英文字母组成的字符串
    var str = 'jdjEEdjowdl';
    var reg = /^[a-zA-Z]+$/g
    console.log(reg.test(str));

    // 验证由数字和26个英文字母组成的字符串
    var str1 = 'jdjd98765EEdjowdl';
    var reg1 = /^[0-9a-zA-Z]+$/
    console.log(reg1.test(str1));

    // 验证由数字、字母、下划线组成的字符串
    var str2 = 'jd_jEEdjo_wdl';
    var reg2 = /\w/
    console.log(reg2.test(str2));

    // 验证汉字    var reg = /^[\u4e00-\u9fa5]+$/
    var str3 = '老陈你好';
    var reg3 = /^[\u4e00-\u9fa5]+$/g;
    console.log(reg3.test(str3));
```



### 使用正则验证空格、手机号及邮箱

**需求说明:**
使用正则验证如下需求
首尾有空格的字符串（分别验证清除前面、后面、前后以及所有空格的方法）
验证手机号码
验证邮箱

清除空格：

```js
  // 首尾有空格的字符串（分别验证清除前面、后面、前后以及所有空格的方法）
    //为了演示看起来直观，我们把清除替换成*

    var  str = '  nihao  hehe  shijie  llala  ';

    // 清除前面
    // var reg = /^\s+/;

    //清除后面
    // var reg = /\s+$/;

    //清除前面和后面
    // var reg = /^\s|\s$/g;

    //清除全部
    var reg = /\s+/g;
    
    console.log(str);
    console.log(str.replace(reg,'*'));
```



验证手机号码:

```js
  //验证手机号
    var phone = 13140172555;
    var reg = /^1[3-9][0-9]{9}$/;  //此时的{9}限制的是前面[0-9]这个字表达式
    console.log(reg.test(phone));
```

邮箱正则：

```js
 //验证邮箱
    var email = '4732chenfuuo_@qq.com';
    // var email = '4732chenfuuo_@qq.com.cn';
    var reg = /^\w+@\w+(\.[a-z]{2,3}){1,2}$/

```

### 符串中的数字加上中括号

需求说明
使用正则给如下字符串中的数字加上中括号
var str='abc345efg';


```
  var str='abc345efg';
  document.write(str.replace(/(\d)/g,'[$1]'));
```

正则在线测试工具: https://regexr-cn.com/

正则练习: https://codejiaonang.com/

## 11同步异步

### 单线程

单线程就是：指一次只能完成一件任务。如果有多个任务，就必须排队，前面一个任务完成，再执行后面一个任务，以此类推。

js语言最大的特点既是单线程

同步任务执行完以后 才会执行异步任务

异步任务：定时器 计时器 事件 ajax nodejs的fs读写

```js
//同步任务从上往下执行
//异步任务 看谁执行的快 谁快谁先执行
//如果异步任务执行的时间相同 按照先后顺序 前面的先执行 后面的后执行

//如果 时间不同 耗费时间短的先执行 耗费时间长的后执行
console.log(1);
console.log(2);
setTimeout(function(){
    console.log(3);
},1000)
setInterval(function(){
    console.log(4)
},3000)
console.log(5);
console.log(6);
//1,2,5,6,3,4
```

```js
    var li = document.getElementsByTagName('li');
    for (var i = 0; i < li.length; i++) {
        //同步
        li[i].onclick = function () {
            console.log('for内部的' + i);//异步
        }
    }
    console.log('外部的' + i);
```

### 为什么js是单线程

JavaScript语言的一大特点就是单线程，也就是说，同一个时间只能做一件事。那么为什么JavaScript不能有多个线程呢？这样能提高效率啊

JavaScript的单线程，与它的用途有关。作为浏览器脚本语言，JavaScript的主要用途是与用户互动，以及操作DOM。这决定了它只能是单线程，否则会带来很复杂的同步问题。比如，假定JavaScript同时有两个线程，一个线程在某个DOM节点添加内容，另一个线程删除了这个节点，这时浏览器应该以哪个线程为准？

所以为了避免复杂性，从一诞生，JavaScript就是单线程，这已经成了这门语言的核心特征，将来也不会改变。

### 任务队列(task queue)

单线程就意味着，所有任务需要排队前一个任务结束，才会执行后一个任务。如果一个任务耗时很长，后一个任务就不得不一直等着。

```js
  function f1() {
        for (var i = 0; i <= 999; i++) {
            console.log('f1');
        }
    }

    function f2(){
        console.log('f2');
    }
    f1();
    f2();
```

此时，f1函数非常耗时，因为js是单线程的，只能等f1执行完以后，才能执行f2

如果排队是因为计算量大，CPU忙不过来，倒也算了，但是很多时候CPU是闲着的，因为IO设备（输入输出设备/用户的读写操作）很慢（比如Ajax操作从网络读取数据），不得不等着结果出来，再往下执行。

JavaScript语言的设计者意识到，这时主线程完全可以不管IO设备，挂起处于等待中的任务，先运行排在后面的任务。等到IO设备返回了结果，再回过头，把挂起的任务继续执行下去。

> 超时结账，只有一个收银，大家都在排队，
>
> 突然发现，有一个人口袋里偷了一瓶茅台，他还不承认，非说是自己的随身带的酒，不是偷的
>
> 结账出现了问题，怎么快速解决？让他去一边，先让后面的人结账，后面的人结完账了，再来处理这个出问题的人
>
> 来到一旁的人，就是进入了任务队列

### 同步任务&异步任务

所有的任务可以分为两种

一种是同步任务（synchronous）
另一种是异步任务（asychronous）

同步任务指的是：在主线程上排队执行的任务，只有前一个任务执行完毕，才能执行后一个任务

异步任务指的是：不进入主线程，而进入任务队列（task queue）的任务
只有任务队列通知主线程，某个异步任务可以执行了，该任务才会进入主线程执行

### 灵魂三连问

问：js为什么需要异步?

答：如果JS中不存在异步,只能自上而下执行（js是单线程的语言）,万一上一行解析时间很长,那么下面的代码就 会被阻塞。

对于用户而言,阻塞就意味着"卡死",这样就导致了很差的用户体验。 



问： js单线程又是如何实现异步的呢?
答：通过事件循环(event loop)实现'异步'。 

​                                        

问： 异步任务有哪些呢？ 

答：定时器、计时器、 事件、 Ajax操作、NodeJS中的fs文件读写 等。

### Event Loop事件循环

事件循环：只要主线程空（代表同步任务执行完了），就回去读取任务队列，这都是JavaScript的运行机制，整个过程会不断重复



假定：异步任务执行时出现一个同步任务，当前异步执行完后立刻执行同步任务	———————！！！————没有这种可能

### 代码分析

```js
    console.log('000');

    setTimeout(function(){
        console.log('111');
    },1000)

    setTimeout(function(){
        console.log('222');
    },500)
    
    setTimeout(function(){
        console.log('333');
    },0)

    console.log('444');
```


### js执行机制总结:

js是一个单线程的语言，把所有的任务分类为同步任务和异步任务

在执行的时候首先判断js代码是同步还是异步，同步就进入主线程，异步就进入任务队列Event queue

同步任务进入主线程后一直执行（从上往下），直到主线程空闲时（表示同步任务执行完毕），此时才会去任务队列Event queue中查看是否有可执行的异步任务，如果有就将任务队列中的异步任务推入主线程中进行执行

异步任务执行的时候，如果执行的时间一样，从任务队列里面从上往下执行

如果时间不一样，时间短的先执行

## 12Ajax

ajax是一种在无需重新加载整个网页的情况下，能够更新部分网页的技术

前后台建立连接，把前台请求发送给后台。把后台的相应拿个前台

简单说：大白话：就是没用Ajax网页，你点一个按钮就要刷新一下页面，尽管新页面上只有一行字和当前页面不一样，但你还是要无聊的等待页面刷新

用了Ajax之后，你点击，然后页面上的一行字就变化了，页面本身不用刷。

Ajax只是一种技术，不是某种具体的东西

### 创建Ajax步骤

1、创建Ajax对象

2、连接到服务器

3、发送请求

4、接受返回值

语法：

非IE6语法：

```js
var oAjax=new XMLHttpRequest();
```

老版本IE5和IE6语法：

```js
var oAjax=new ActiveXObject("Microsoft.XMLHTTP");
```

创建Ajax对象

```html
<html>
    <head>
        <style>
        	
        </style>
    </head>
    <body>
        <button onclick="send()">发送请求</button>
    </body>
</html>
<script>
	function(){
        //1、创建Ajax对象
        //第一种写法
        var oAjax=new XMLHttpRuquest()||new ActiveXObject('Microsoft.XMLHTTP');
        //第二种写法
        if(window.XMLHttpRequest){
           var oAjax=new XMLHttpRequest();//firfox chrome等浏览器
           }else{
               var oAjax=new ActiveXObject('Microsoft.XMLHTTP');//ie5 ie6浏览器
           }
    }
</script>
```

连接到服务器

语法：

open(方式，后台地址(文件名)，同步异步)

参数一：post/get(网络请求的方式);

参数二：请求的文件名(后台地址);

参数三：同步(false)	异步(true)	默认异步

```js
oAjax.open("get","abc.txt","true");
Apache、IIS、Nginx等大多数web服务器，都不允许静态文件响应POST请求
```

```html
<html>
    <head>
        <style>
        	
        </style>
    </head>
    <body>
        <button onclick="send()">发送请求</button>
    </body>
</html>
<script>
	function send(){
        //1、创建Ajax对象
        var ajax_=new XMLHttpRequest()||new ActiveXobject('Microsoft.XMLHTTP');
    //2、建立连接open（请求方式、文件地址、同步/异步）
    ajax_.open('get','url','true');
            }
</script>
```

请求方式：

get、post、put、delete

### get和post请求的区别：

|                      | **GET**                                                      | **POST**                                                     |
| -------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| **缓存**             | **能被缓存**                                                 | **不能缓存**                                                 |
| **历史**             | **参数保留在浏览器历史中**                                   | **参数不会保存在浏览器历史中**                               |
| **对数据长度的限制** | **当发送数据时，GET 方法向 URL 添加数据；URL 的长度是受限制的（URL 的最大长度IE是 2048 个字符,chrome 最大长度8182个字符）** | **无限制**                                                   |
| **对数据类型的限制** | **只允许 ASCII 字符**                                        | **没有限制，也允许二进制数据**                               |
| **安全性**           | **与 POST 相比，GET 的安全性较差，因为所发送的数据是 URL 的一部分** | **POST 比 GET 更安全，因为参数不会被保存在浏览器历史或 web 服务器日志中** |
| **可见性**           | **数据参数在 URL 中对所有人都是可见的**                      | **数据不会显示在 URL 中**                                    |



**GET请求：**
```
get查询信息的时候	请求参数放在了URL路径中	缓存 不安全	用于数据不敏感的时候

post提交信息 更安全一些	数据放在请求体中	没有长度限制	跟安全	不能缓存
```

### 请求状态码 readyState：

从 0 到 4 发生变化
0: 请求未初始化（还没有调用到open方法）
1: 服务器连接已建立（已调用send方法，正在发生请求）
2: 请求已接收（send方法完成，已接收到全部请求内容）
3: 请求处理中（解析响应内容）
4: 请求已完成，且响应已就绪

### 响应状态码 status：

200："OK"

404：未找到页面	路径错误

403：请求成功 服务器拒绝响应 没有权限

5**：服务器内部错误，（检查拼接的参数对不对）

500： 服务器内部错误

### JSON语法规则

数据在 名称/值在对中

### json字符串转为对象

```js
//1、eval('('+json名称+')')；
//2、JSON.parse(json名称)
```

### json 对象转为字符串

```js
//JSON.stringify(对象)	对象转为字符串
```

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <button onclick="send()">发送请求</button>
</body>

</html>
<script>
    function send() {
        //1、创建Ajax对象
        var ajax_txt = new XMLHttpRequest() || new ActiveXObject('Microsoft.XMLHTTP');
        // console.log(ajax_txt.readyState);//0: 请求未初始化（还没有调用到open方法）
        // 2、建立连接
        // 语法：ajaxObject.open('a','b','c');
        // a：请求方式 get查询 post提交 put修改时 delete删除
        // b：请求的路径 接口    'www.chenfuguo.cn/data/goods.json'
        // c：同步或异步   异步true    同步false   默认异步false
        ajax_txt.open('get', './01.txt', 'true');

        // 3、发送请求
        //发送请求的时候
        //get用来请求数据,请求参数拼接在了请求路径的后面，http://*********?参数=值&参数2=值
        //post请求参数放在了send中
        ajax_txt.send();

        // 4、开始接受响应数据
        ajax_txt.onreadystatechange = function () {
            if (ajax_txt.readyState == 4) {
                //status状态码  ==200为成功
                if (ajax_txt.status == 200) {
                    console.log(ajax_txt.responseText);
                } else {
                    console.log('请求失败');
                }
            }
        }
    }

</script>
```

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>

<body>
    <button onclick="send()">发送请求</button>
</body>

</html>
<script>
    function send() {
        //1、创建Ajax对象
        var ajax_txt = new XMLHttpRequest() || new ActiveXObject('Microsoft.XMLHTTP');
        // console.log(ajax_txt.readyState);//0: 请求未初始化（还没有调用到open方法）
        // 2、建立连接
        // 语法：ajaxObject.open('a','b','c');
        // a：请求方式 get查询 post提交 put修改时 delete删除
        // b：请求的路径 接口    'www.chenfuguo.cn/data/goods.json'
        // c：同步或异步   异步true    同步false   默认异步false
        ajax_txt.open('get', './01.txt', 'true');

        // 3、发送请求
        //发送请求的时候
        //get请求参数放在接口路径中
        //post请求参数放在send中
        ajax_txt.send();

        // 4、开始接受响应数据
        ajax_txt.onreadystatechange = function () {
            if (ajax_txt.readyState == 4) {
                //status状态码  ==200为成功
                if (ajax_txt.status == 200) {
                    console.log(ajax_txt.responseText);
                } else {
                    console.log('请求失败');
                }
            }
        }
    }

</script>
```

## 13跨域

CORS是一个W3C标准，全称是：跨域资源共享。它允许浏览器向跨源服务器，发出XMLHttpRequest，从而克服Ajax只能同源使用的限制

跨域，指的是浏览器不能执行其他网站的脚本，简单的理解就是因为JavaScript同源策略的限制，a.com域名下的js无法操作b.com或是c.a.com域名下的对象

例子：比如淘宝网不能请求京东的数据

### 产生跨域的原因：

由于浏览器的同源策略造成的

同源策略，它是由Netscape提出的一个著名的安全策略，现在所有支持JavaScript的浏览器都会使用这个策略。

同源策略：

生活中，社会能够安定的运行，有一个前提，大家都默认遵守一个约定：每个人都只能自由的出入自己的家，拿取自己家的东西。而如果大家都不遵循这种协定，你可以随便拿别人家的东西，别人也可以随便的出入你的家，这样社会就乱套了。此处大家都遵守的各用各家的东西，久啊叫做同源策略。

同源策略大白话：

> 生活中，社会能够安定的运行，有一个前提，大家都默认遵守一个协定：每个人只能自由的出入自己的家，拿取自己家的东西。而如果大家都不遵循这种协定，你可以随便去拿别人家的东西，别人也可以随便的出入你的家，这样社会就乱套了。此处大家都遵循的各用各家的东西，就叫做同源策略

#### 所谓同源是指：

<font color=red>

同域名：

同协议：http，https

同端口：
</font>

### 跨域的限制

随着互联网的发展，同源策略越来越严格。目前，如果非同源，共有三种行为受到限制。

1、无法读取非同源网页的Cookie、LocalStorage和IndexedDB。【缓存数据】

2、无法接触非同源网页的DOM。

3、无法向非同源地址发送AJax请求（可以发送，但浏览器会拒绝响应）

### 后台加入响应头解决跨域：

```java
response.setHeader("Access-Control-Allow-Origin", "*");//响应头。
```
“*”表示所有的域都可以接受
CORS 需要浏览器和服务器同时支持。目前，所有浏览器都支持该功能。


### AJax跨域请求【代理服务器】解决跨域

代理服务器

由于在工作中需要使用AJax请求其他域名下的资源，但是会出现拒绝访问的情况，这是因为基于安全的考虑，AJax只能访问本地同域的资源，而不能跨域访问

可以让服务器去别的网站获取内容然后返回页面

大白话：我们要租房子，房源被中介垄断了，我们无法直接找到房东。我们先找到中介，中介和房东谈具体事宜，谈好以后把每个月多少钱的信息告诉我们

### 使用jsonp可以完成跨域

jsonp	借助的是	src可以跨域，src本身就是访问外部资源

jsonp只能完成get请求，不能使用post方法

因为get请求方式把请求参数放在了URL地址中，后台解析jsonp是通过URL的callback参数进行判断的，所以支持get请求



### jsonp实现的思路：

全称是JSON with Padding，请求时通过创建一个script，在script中发出请求

通过这种变通的方式让请求资源可以跨域

它不是一个官方协议，是一个约定，约定请求的参数里面如果包含指定的参数（默认是callback）,说明是一个json请求，服务器发现是jsonp请求，就会吧返回对象变成js代码

JS代码势函数调用的形式，他的函数名是callback的值，他的函数的参数就是愿挨需要返回的结果

后台会把函数调用，重新返回给前端

```html
<script>
function getData(val){
    console.log(val)
}
</script>
<script src="http://localhost:3003/jsonp?callback=getData"></script>
```

```html
<html>
    <head>
        <style>
        	
        </style>
    </head>
    <body>
        <button onclick="getData()">点击获取json数据</button>
    </body>
</html>
<script>	
function test(val){
    console.log(val)
    var script_=document.createElement('script');
    script_.src='http://localhost:3003/jsonp?callback=test';
    document.body.appendChild(script);
}
</script>
```



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>模拟jsonp</title>
</head>
<body>
   <script>
    //    调用后台函数
       function fn(value){
           console.log(value);
       }
   </script>
   <!-- 
       通过script的src属性进行跨域
       传递的参数默认是callback
       后台看到callback就能够判断出来是一个jsonp请求
       会根据callback的值，自动生成函数，函数名就是callback的值
       后台把数据，作为参数传递给函数作为值
    -->
   <script src="./testJs.js?callback=fn"></script>
</body>
</html>
```

```js

// testjs.js就是我们模拟的后台
// 后台能判断出来是否是jsonp请求
// 如果是，就会生成一个函数的调用，而函数名，就是前端提交上来的callback的值在假如我们要给前端返回一个数据



var data = {
    "name":"张三",
    age : 20,
    address:"郑州"
}

// 在后台生成了函数的调用，把数据以参数的形式，进行传递
// 后台会把这个函数的调用，重新返回给前端
fn(data);

```

## 14Cookie

Cookie用于存储页面的用户信息

常见例子：自动登录、记住用户名或密码

#### 会话

一次会话，就像一次谈话

一次会话包含多次请求和响应

http是无状态的协议

一次会话：浏览器第一次给服务器资源发送请求，会话建立，知道一方断开为止

#### 会话的功能

共享数据

在一次会话的多次请求间共享数据

我们之前学习了http协议，http协议无状态的，每次浏览器发送请求，服务器给出相应，不同的请求响应之间，相互独立，是没有关系的，无法进行数据的共享和交换

、

想要不同请求响应之间可以进行数据的交换，这就用到了会话技术。比如我们点击淘宝买东西，买不同的东西加入购物车，最终我们去购物车结算的时候，算的是这全部的商品，每点击添加一个商品完成了一次请求响应，最终这么多请求相应的数据一起结算，这就是使用了会话技术

#### 共享数据的方式

1、客户端会话技术：Cookie	client客户端	浏览器

把共享的数据存储在客户端（浏览器）

cs	client——>server 客户端

bs	browser——>server	浏览器

2、服务器端会话技术：Session	server  服务器

把共享的数据存储在服务器端

##### 1、Cookie概念：

将数据存在客户端【浏览器】的一门会话技术

### 2、Cookie会话技术的过程

客户端发送请求，服务器响应数据

客户端把响应得到的数据存储在浏览器端

第二次请求的时候，浏览器携带存储的数据继续请求



#### Cookie实现原理

实现原理：基于请求头cookie和响应头setcookie实现

当客户端发送请求以后

服务器把cookie数据以响应头的方式返回给客户端类型：set-cookie：名=值

当客户端看到set-cookie的响应头，自动把数据保存到客户端

客户端下次请求的时候，自动携带保存的数据请求，并把数据放入cookie：名=值，的请求头里面【可通过抓包工具进行查看】

#### Cookie的特点和作用

特点：

1、cookie存储数据在客户端浏览器。数据存储在服务器端，安全等级高。数据cookie存储在浏览器端，安全等级低，容易被篡改，但是访问速度快

2、浏览器对于单个cookie的大小有限制（4kb）同一个域名下的总cookie数量也有限制（20个）

3、cookie存储默认有效时间20分钟，默认页面关闭，cookie就消失了

作用：

1、cookie一般用与存出少量的不爱敏感的数据

2、在不等于的情况下，服务器对客户端的身份识别

比如：设置搜索提示框

#### 5、Cookie特性

1、同一个网站中所有页面共享一套cookie，cookie是按照域名进行存储的

2、数量、大小有限4-10k

3、过期时间，因为存储的空间太小了，所以到期就把数据给清理掉了

4、每次会随着HTTP请求发送给服务器，每次请求都要携带的信息（最典型的就是身份认证的信息）就特别适合放在cookie中，其他类型的数据就不合适了

### 使用JavaScript操作cookie

1、创建cookie

语法：

```js
document.cookie="名字=值";
document.cookie="key=val";


//cookie存值的时候 如果域名一样 则下面的发改上面的值
document.cookie='username=老陈';
document.cookie='username=老李';
document.cookie='password=123456';
document.cookie='isrember='true;
```

### 封装Cookie

```html
<script>
//增 删 改 查

/*删除cookie	设置过期期间
通过expires=时间对象
document.cookie='name=value;expires='+时间对象*/
var time=new Date()
//+1代表一天后过期，如果想立马删除，可以设置-1
time.setDate(time.getDate()+1)
document.cookie='username=老欧阳;expires='+time;
document.cookie='username=老欧阳;expires=${time}';



//查找cookie	根据键名找到对应的值

//找到所有的cookie
var cookies=document.cookie;
console.log(cookies);
</script> 
    



//函数增删改查cookie封装
<script>
    //添加cookie
    function addCookie(key, val, expires) {
        var date = new Date();
        date.setDate(date.getDate() + expires)
        document.cookie = `${key}=${val};expires=${date}`
    }
    //删除cookie
    function removeCookie(key) {
        this.addCookie(key, '', -1)
    }
    //清空cookie
    function clearCookie(key) {
        var cookies = document.cookie;
        cookies = cookies.split('; ')
        // console.log(cookies)
        for (var item of cookies) {
            itemcookie = item.split('=')
            // console.log(cookies);
            // console.log(cookies[0]);
            removeCookie(itemcookie[0])
        }
    }
    //查找cookie
    function searchCookie(key) {
        var cookies = document.cookie;
        cookies = cookies.split('; ');
        // console.log(cookies);
        for (var item of cookies) {
            itemcookie = item.split('=');
            // console.log(itemcookie[0])
            if (itemcookie[0] == key) {
                console.log(itemcookie[0]);
            }
        }
    }
</script>
<script>
    addCookie('name1', '一');
    addCookie('name2', '二');
    addCookie('name3', '三');
    // removeCookie('name')
    // clearCookie();
    searchCookie('name3');
</script>
```

### storage本地存储

#### cookie和storage对比的缺点

##### Cookie

只能存储4KB

浪费宽带，每次会随着HTTP请求发送给服务器

操作数据很繁琐，没有方便的API

存储默认20分钟，页面关闭就消失

#### Storage本地存储（H5新增特性）

大小最小5MB，可以申请更大的空间

不会随HTTP请求发送给服务器

非常容易操作

移动端普及高

LocalStorage与sessionStorage两种

localStorage只要不删除，永久删除

sessionStorage 页面关闭 立即消失

#### LocalStorage本地存储

为永久性保存数据，不会随着浏览器的关闭而消失，可以在同域名跨页访问

按域名进行存储，不会和其他域名冲突

键值对存储：key/value

#### localStorage存储数据

LocalStorage永久存储 不会携带http请求中 大小为5MB 方便的api setItem getItem removeItem clear()

语法:

```js
LocalStorage.setItem(key,value);
```

value是字符串类型 如果想存储对象 对象转为字符串

```js
//设置storage
//LocalStorage.setItem(key,value)
LocalStorage.setItem('username','您古拉斯赵四')；
```

LocalStorage 获取数据

```js
//localStorage.getItem('key')
var name_=localStorage.getItem('name')
console.log(name_);
```

LocalStorage删除数据

```js
localStorage.removeItem('name1')
```

LocalStorage清空数据

```js
localStorage.clear();
```

#### sessionStorage

暂时性存储	无痕模式	页面关闭 	数据消失

不会携带在http中

大小最小5MB

方便的api setItem getItem removeItem clear()


sessionStorage存储数据

```js
sessionStorage。setItem('type','无痕');
```

sessionStorage 获取数据

```js
//sessionStorage.getItem('key')
var name_=sessionStorage.getItem('name')
console.log(name_);
```

sessionStorage删除数据

```js
sessionStorage.removeItem('name1')
```

sessionStorage清空数据

```js
sessionStorage.clear();
```



length获取LocalStorage一共有多少条数据

```js
//length获取LocalStorage的长度
console.log(localStorage.length)	//2
```

配合key(index)方法可以实现遍历LocalStorage数据的方法

```js
//LocalStorage以键值对的方式存在
//localStorage.key(0);
console.log(localStorage.key(0));//username
```

遍历localStorage

```js
//遍历获取信息
for(var i=0; i<localStorage.length; i++){
    var k_= localStorage.key(i)
    var value = localStorage.getItem(_k);
    console.log(k_+":"+value)
}
```

### LocalStorage同源事件

当同源的LocalStorage有更改以后，会触发这个事件

#### 使用cookie记住密码



## 15封装

### 基于Object的方式创建对象

创建对象：

```js
var 对象名称=new Object();
```

```js
var user = new Object();
//对象  属性  死的	方法  活的
//属性是特征		方法是功能
//对象.属性=值;
user.name="张三";
user.pwd="123456";
user.show=function(){
    document.write(this.name+"-this.pwd");
}
user.show();


var str='haha'
var str2='haha'
console.log(str===str2);//true

var obj=new Object();
var obj2=new Object();
console.log(obj===obj2);//false

```

### 对象字面量

对象定义的一种简写形式

简化创建包含大量属性的对象的过程

在为函数传递大量可选参数时，可考虑使用对象字面量

```js
var user={
    name:"张三",
    pwd:"123456",
    show:function(){
      document.write(this.name+"-"+this.pwd);
    }
}
user.show();

var result='name';
console.log(user[result]);//张三	=>user.name
//result为字符串不能.出来
```

### 在为函数传递大量可选参数时，可考虑使用对象字面量：

```js
//Object.assign(被合并的内容,合并的内容)
//Object.assign(a,b)
//如果a的属性名和b的属性名一样 则b的该属性的值 覆盖a的属性的值
//如果 a的属性的值 b中没有 则保留a的属性 和值
//同时保留不同的属性

var obj={
    a:'1',
    b:'2',
    c:'3',
    f:'4'
}
var obj2={
    a:'111',
    b:'222',
    c:'333',
    d:'444'
}

Object.assign(obj,obj2);
console.log(obj,obj2);
```

### 工厂模式

软件工程领域的一种设计模式

抽象了创建对象的过程

通过函数封装创建对象的细节，就是把创建对象的过程封装在了函数中

大白话：

毕业两年，码农张收收三小两口无法忍受挤公交，凌晨起床抢火车票的痛苦，遂计划买车。逛了对家4s店，最终定下本田飞度的轿车。4s店接受订单后，向工厂说明车型，工厂随后进行汽车制造，运输到4s店后再到了小两口的手上，小两口终于成了有车一族。

4s销售模式即典型的简单工厂模式。

工厂模式的要点在于：当你需要什么，只需要传入一个正确的参数，就可以获取你所需要的对象，而无需知道其创建细节。

```js
function create_user(name,age,address,job){
    var user=new Object();
    user.name=name,
    user.age=age,
    user.address=address,
    user.job=job,
    user.show=function(){
    var str=`姓名${this.name}<br>年龄${this.age}<br>地址${this.address}<br>职业${this.job}`
    document.write(str);
    }
    return user;
}
var user1=create_user('马保国',68,'伦敦','传武骗子');
var user2=create_user('聂枭',48,'犄角旮旯','成功学骗子');
user1.show();
user2.show();
```

### 工程模式的弊端：

1、看不出内在联系

JavaScript还提供了一个instanceof运算符，

验证原型对象与实例对象之间的关系console.log(user1 instanceof createUser);

通过instanceof查看user1和create_user的关系；

```js
//instanceof	看当前对象是否 被 某某造出来
//a instanceof b	a是否由b创造出来的对象 结果 true false

console.log(user1 instanceof createUser);//false
```

2、不变的内容(属性、方法)重复调用浪费资源

### 构造函数

解决工厂模式的问题，js提供了一个构造函数模式。构造函数一般以大写字母开头，构造函数也是函数，只不过可以用来创建对象，内部使用this变量。对构造函数使用new运算符，就能生成实例，并且this变量会绑定在实例对象上

在构造函数中使用this，this指向当前创建的实例。（new 构造函数得到的对象）	普通函数的this指向window

```js
//构造函数和普通函数的区别
//约定	构造函数	函数名	首字母大写
//普通函数	首字母小写

//调用的时候	普通函数	函数名()
//构造函数	new 构造函数名()	得到一个新的对象

//普通函数	this指向window
//构造函数	内部的this	动态的	永远指向	new 构造函数	得到的实例对象

function CreateUser(name_,age_.address_){
    //构造函数	内部的this	动态的	永远指向	new 构造函数	得到的实例对象
    this.name=name_;
    this.age=age_;
    this.address=address_;
    
    this.show=function (){
        var str=`姓名${this.name}<br>年龄${this.age}<br>地址${this.address}`
    }
}

var user1=new CreateUser('马保国','69','伦敦');
console.log('user1');
console.log(user1 instanceof CreateUser)

//查看由谁创造出的
console.log(user1.constructor);
```

### 原型prototype

每个构造函数都有一个prototype(原型)属性

是一个指针，指向一个对象

原型对象上面的属性和方法，会自动的被实例对象拿来使用，可以直接拿来使用，所以说可以把一些不变的属性和方法放在原型对象上面，然后拿来使用

```js
//构造函数原型对象的方法和属性  直接被构造函数的实例对象使用
function CreateUser(){}
    CreateUser.prototype.name='老陈';
    CreateUser.prototype.show=function (){
        console.log('构造函数原型对象(爷爷)的方法');
        console.log(this);
    }
var user1=new CreateUser();
console.log(user1.name);//老陈
user1.show();//构造函数原型对象(爷爷)的方法
console.log(user1);//原型对象中的this，此时指向user1
//在构造函数中以及在原型对象的方法中，this依然指向构造函数的实例对象
```



### this指向有哪些(目前所学)面试题重点

  1、在普通函数中 			  this指向window

  2、在自执行函数中 		  this指向window

  3、在计时器中				  this指向window

  4、在定时器中 				 this指向window

  5、在事件调用函数中 	  this指向当前事件的调用者

  6、在对象的方法中 		  this指向当前对象

  7、在构造函数中使用this，this指向当前构造函数创建的实例。（new 构造函数得到的对象）

  8、在构造函数的原型对象中，this依然指向当前构造函数的实例对象




### instanceof和typeof的区别
instance的意思是实例，因此可以知道instanceof的作用就是判断该对象是谁的实例，返回结果是true或false，我们也就知道了instanceof是对象运算符

typeof运算符返回一个字符串，用来检测变量的数据类型。当操作类型是一个基本类型（例如字符串、数字、或布尔值）时，它可以很好的工作。
但当检查对象类型时，它只会返回object，而无法区分不同的对象类型

```js
console.log(typeof "hello");  // 输出 "string"
console.log(typeof 5);        // 输出 "number"
console.log(typeof true);     // 输出 "boolean"

var myObject = {};    
console.log(typeof myObject); // 输出 "object"

var arry = [1, 2, 3];
console.log(typeof arry);     // 输出 "object"

var date = new Date();
console.log(typeof date);     // 输出 "object"
```

然而，instanceof运算符检查对象是否是特定类的实例，它在检查对象类型方面更加有用。他可以用于检查

```js
let myArray=[1,2,3];
console.log(myArray instanceof Array);//输出 true
console.log(myArray instanceof Object);//输出	true

let myDate=new Date();
console.log(myDate instanceof Date);//输出	true
console.log(myDate instanceof Object);//输出	true
```

因此，typeof用于检查基本类型和对象类型的共同点，而instanceof用于检查对象类型的身份，检查对象是否是特定的实例

总之typeof和instanceof都是用来判断变量类型的，区别在于

1、typeof判断所有变量的类型，返回值number、string、boolean、function、object、undefined。

2、typeof对于丰富的对象实例，例如数组、日期只能返回object，导致有时候得不到真实的数据类型。

3、instanceof用来判断对象，代码形式（obj1 instanceof obj2）（判断obj1是否为obj2的实例），obj2必须为对象，否则会报错。用来精准的判断，对象是否有某构造函数创造出来的，返回的是布尔值(亲子鉴定)



### constructor

用来查找当前对象的构造函数(找爸爸)

## 16继承

一个对象去通过另一个对象，拥有自己没有的方法和属性，这个过程我们称之为继承

大白话：

张三跟着张三丰学习太极剑，张三继承张三丰的太极剑。继承以后张三拥有太极剑技能张三丰依然拥有本身的技能

### 原型链继承

对象.prototype=new 被继承的对象;

```js
function GaoBW(){
    this.car='兰博基尼';
    this.house='温哥华山庄别墅1001号'
}
function Father(name,age){
    this.name=name;
    this.age=age;
}
Father.prototype=new GaoBW();
var son=new Father('李四',18);
console.log(son.name);
console.log(son.age);
console.log(son.car);
console.log(son.house)

//弊端：存在继承紊乱，son通过Father创建出来的。但是继承过后，会发现，son的构造函数，不在Father，而是GaoBW
console.log(son.constructor)//结果是GaoBW，发现自己的亲爹不再是亲爹

//因此需要手动修改继承链
Father.prototype.consttructor=Father
console.log(son.constructor)//此时为Father
```

### 原型链继承-直接继承prototype

由于GaoBW对象中，不变的属性都可以直接写入GaoBW.prototype。所以，可以让Father()跳过GaoBW，直接继承GaoBW.prototype

```js
function GaoBW(){}

GaoBW.prototype.house='温哥华山庄别墅1001号';
GaoBW.prototype.car='兰博基尼';

function Father(name,age){
    this.name=name;
    this.age=age;
}
//不再继承GaoBW 直接继承GaoBW的原型对象 少了一个new的过程
//依然存在继承紊乱
Father.prototype=GaoBW.prototype;
//手动修改继承链
Father.prototype.constructor=Father;
console.log(son.constructor)//Father

var son=new Father('李四',18);
console.log(son.name);
console.log(son.age);
console.log(son.car);
console.log(son.house)

//另一个弊端
Father.prototype.car='五菱宏光';
var GaoBW=new GaoBW();
console.log(GaoBW.car);//五菱宏光;
```

优点：效率比较高（不用执行和GaoBW的实例了）

缺点：1、依然会产生继承链紊乱，需要手动修改继承链

			2、因为Father的原型对象指向了GaoBW的原型对象，所以Father修改原型对象的值，GaoBW原型对象的值也被修改了，这样就等于继承别人的财富，还随意的更改别人的内容，太霸道，不合理

### 利用空对象继承

```js
function GaoBW(){}

GaoBW.prototype.house='温哥华山庄别墅1001号';
GaoBW.prototype.car='兰博基尼';

function Null(){}

Null.prototype=GaoBW.prototype;

function Father(name,age){
    this.name=name;
    this.age=age;
}

var son=new Father('李四',18);
console.log(son.name);
console.log(son.age);
console.log(son.car);
console.log(son.house)

Father.prototype=new Null();
Father.prototype.constructor=Father;

Father.prototype.car='五菱宏光';
var GaoBW=new GaoBW();
console.log(GaoBW.car);//兰博基尼
```

### 把继承的过程封装为函数

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <script>
        function GaoBW(){}
        GaoBW.prototype.car = '兰博基尼';
        GaoBW.prototype.house = '温哥华山庄别墅1001号';

        function Fater(n,a){
            this.a=a;
            this.n=n;
        }
        // 封装函数
        function extence(parent,child){
            function F(){}
            F.prototype= parent.prototype;
            child.prototype = new F();
            child.prototype.constructor = child;
        }
        
        extence(GaoBW,Fater);
     
        var tc_ = new Fater('tc',20);
        console.log(tc_.car,tc_.house)

        Fater.prototype.car = '五菱';
        var gao_ = new GaoBW();
        console.log(gao_.car);//兰博基尼
 
    </script>
</body>
</html>
```



### 构造函数的绑定

即在子类型构造函数的内部调用父类型构造函数

通过call()或apply()方法

构造函数实现对实例属性的继承，完成不了对父类原型对象的继承

### call

语法：

a.call(b,agr1,agr2);

表示b继承a	agr1,agr2是a的参数

```js
        function Father(car,house){
            this.car=car;
            this.house = house;
        }

        function Son(name,age){
            this.name=name;
            this.age = age;
            //son 继承 father
            //a.call(b，ag1,ag2);
            //表示b继承a,ag1，ag2是a的参数
            Father.call(this,'汤臣一品','大众捷达');
        }
        var son_ = new Son('小宝',20);
        console.log(son.house);
        console.log(son.car);
```

### apply:

语法：

a.apply(b，[ag1,ag2]);

表示b继承a,ag1，ag2是a的参数

```js
        function Father(car,house){
            this.car=car;
            this.house = house;
        }

        function Son(name,age){
            this.name=name;
            this.age = age;
            //son 继承 father
            //a.call(b，ag1,ag2);
            //表示b继承a,ag1，ag2是a的参数
            Father.apply(this,['汤臣一品','大众捷达']);
        }
        var son_ = new Son('小宝',20);
        console.log(son.house);
        console.log(son.car);
```

### 组合继承

构造函数继承，只能继承构造函数内部的属性方法，无法继承其原型对象的属性方法

```js
    function Father(house, car) {
        this.car_ = car;
        this.house_ = house;
    }

    Father.prototype.say = function(){
        console.log('我是祖宗');
    }

    function Son(n,a){
        this.name = n;
        this.age = a;
        // Father.call(this,'汤臣一品','劳斯莱斯');
        Father.apply(this,['汤臣一品','哈罗单车']);
    }


    var xw = new Son('小王',30);
    console.log(xw.car_,xw.house_,xw.name,xw.age);
    console.log(xw.constructor);

    xw.say();// 无法显示  
```

也叫伪经典继承
将原型链继承和构造函数继承组合在一块
原型链实现对原型属性和方法的继承
借用构造函数实现对实例属性的继承

```js
    function Father(house, car) {
        this.car_ = car;
        this.house_ = house;
    }

    Father.prototype.say = function(){
        console.log('我是祖宗');
    }

    function Son(n,a){
        this.name = n;
        this.age = a;
        // Father.call(this,'汤臣一品','劳斯莱斯');
        Father.apply(this,['汤臣一品','哈罗单车']);
    }

    Son.prototype = new Father();// 把子类原型指向父类，即可继承父类的原型对象的属性方法
    Son.prototype.constructor = Son;//手动更改原型对象

    var xw = new Son('小王',30);
    console.log(xw.car_,xw.house_,xw.name,xw.age);

    console.log(xw.constructor);// Son

    xw.say();// 我是祖宗
```

### 原型链

```js
        function Person(){

        }

        Person.prototype.sayname=function(){
            console.log('我是person原型对象的sayname')
        } 

        Object.prototype.sayname = function(){
            console.log('我是object原型对象的sayname')
        } 

        var p1 = new Person();

        p1.sayname = function(){
            console.log('我是person实例对象对象的sayname')
        }

        p1.sayname();
```

大白话：



> 就是你有个对象，你丈母娘问你要20W彩礼，你自己拿不出来你没有（对象本身没有属性），丈母娘让你问你爸爸（原型对象）要，如果你爸爸也没有，你爸爸就得问你爸爸的爸爸也就是你爷爷要（原型对象的原型对象，这里的第一个原型对象实质上成了一个实例对象，因为你爸爸在你爷爷那里永远是儿子），如果你爷爷也没有就继续往上要……如此反复，实在拿不出来(null)，丈母娘大手一挥，拿不出来就不嫁了（直到为null时停止）；

### 三个面试题：

1、js实现继承的几种方法

2、call 和apply的区别

3、谈谈你对原型链的理解

# 音视频&less&git

## 音视频

```html
<--! 视频 -->
<video src="./video/a.mp4" controls></video>
```

```html
<--! 音频 -->
<audio src="./audio/a.mp3" controls loop></audio>
```

| 属性     | 值       | 说明                                                         |
| -------- | -------- | ------------------------------------------------------------ |
| controls | controls | 如果出现该属性,则向用户显示控件,比如播放按钮                 |
| autoplay | autoplay | 如果出现该属性,则音频在就绪后马上播放[自动播放]              |
| loop     | loop     | 如果出现该属性,则当音频结束时重新开始播放[循环播放]          |
| preload  | preload  | 如果出现该属性,则音频在页面加载时进行加载,并预备播放[预加载] |

设置autoplay在谷歌被禁用了,如果真的遇到了奇葩用户,有奇葩的想法,就不!! 非得在谷歌中完成这样的设置,那也没办法,那就设置吧

#### 设置方法:

旧版的浏览器会有一下操作

1:地址栏访问:chrome://flags

2:搜索栏搜索:Autoplay policy

把[Default]修改为[No user gesture is required]即可!

如果这样还不可以,那么恭喜你,你的浏览器是新的版本,这些功能已经不存在了



### 4、常见媒体音频格式和浏览器的支持

常见的音频格式
.mp3、.ogg

|            | **IE9** | **Firefox3.5** | **Opera10.5** | **Chrome3.0** | **Safari3.0** |
| ---------- | ------- | -------------- | ------------- | ------------- | ------------- |
| Ogg Vorbis |         | **√**          | **√**         | **√**         |               |
| MP3        | **√**   | √              |               | **√**         | **√**         |
| Wav        |         | **√**          | **√**         |               | **√**         |



实际开发过程中,为了保证不同浏览器都能正常的展示音频,会更改不同的多种格式,audio标签允许多个source元素

source可链接不同的音频文件

```html
<h2>在html5中播放音频:</h2>
<audio controls="controls">
	<source src="video/song.ogg">
    <source src="video/song.mp3">
    您的浏览器不支持audio元素播放的音频
</audio>
```



### 视频播放

语法:

```html
<video src="视频路径"></video>
```

| 属性         | 值         | 说明                                                         |
| ------------ | ---------- | ------------------------------------------------------------ |
| controls     | controls   | 如果出现该属性,则向用户显示空控件,比如播放按钮               |
| autoplay     | autoplay   | 如果出现该属性,则视频子啊就绪后马上播放[自动播放]            |
| loop         | loop       | 如果出现该属性,则当视频在结束时重新开始播放[循环播放]        |
| preload      | auto       | 如果出现该属性,则视频在页面预加载时进行加载,并预备播放[预加载] |
| width/height | length(px) | 设置视频播放器的宽度/高度                                    |
| muted        | muted      | 静音播放                                                     |

```html
<video src="./video/video.webm" controls width="300px" height="100px">
不支持当前格式
</video>
```

## less&sass

新建less文件,编写less,保存后会自动生成css文件,然后引入less生成的css,如果修改less的样式,css也会更改

示例1

```less
//定义变量
@width:10px;
@height:@width+10px;

//引用
#header{
    width:@width;
    height:@height;
}

//编译为
#header{
    width:10px;
    height:20px;
}
```

示例2

```html
<html>
    <head>
    </head>
    <body>
        <ul>
            <li>li-1</li>
            <li>li-2</li>
            <li>li-3</li>
        </ul>
    </body>
</html>
<script>
	
</script>
```

```less
            *{
                margin:0;
                padding:0;
            }
            //声明变量
            @liHeight:50px;
            @liBgc:orange;
@liStyle{
    height:@liHeight;
    background-color:@liHeight;
}
            li{
                margin:10px auto;
            }
            li:nth-of-type(1){
                width:200px;
                height:@liHeiht;
                background-color:@liBgc;
                //以上样式等同于以下	less引入
                .liStyle();
            }
            li:nth-of-type(2){
                width:300px;
                height:@liHeiht;
                background-color:@liBgc
            }
            li:nth-of-type(3){
                width:400px;
                height:@liHeiht;
                background-color:@liBgc
            }
```

示例3

```html
<html>
    <head>
    </head>
    <body>
        <div class="box1">
            <div class="box2">
            	
            </div>
            <p></p>
        </div>
    </body>
</html>
<script>
	
</script>
```

```less
//双斜杠注释不会被编译到css中

/*
	多行注释会被编译到css中
*/

            *{
                margin:0;
                padding:0;
            }
            .box1{
                width:400px;
                height:200px;
                background-color:orange;
                /*box1下子元素 box2元素*/
                .box2{
                    width:200px;
                    height:100px;
                    background-color:skyblue;
                }
                p{
                    width:300x;
                    height:100px;
                    background-color:pink;
                }
            }

//less	不同层级嵌套	编译到css中	是后代选择器书写形式
```

示例4

```less
//传统的css写法
ul>li>a{
    color:red;
}
//使用less后的写法
ul{
    li{
        a{
            color:red;
        }
    }
}
```

### less语法:

变量

@变量名:值;

```less
@width:10px;
@height:@width+10x;

#header{
    width:@width;
    height:@height;
}
```

编译为:

```css
#header{
    width:10px;
    height:20px;
}
```

例子:

less文件:

```less
//定义变量
@col:red;
@sty:dashed;
@width:300px;
@height:50px;

ul{
    wdith:@width;
    height:@height;
    border:1px solid @col;
}
```

在开发过程中,ui会给我们一个页面的设计稿,每个页面都会有一个主题风格.可以把风格中常用的属性值,设为变量,方便后期重复使用



### 混合(Mixins)

混合(Mixin)是一种将一组属性从一个规则包含(或混入)到另一个规则集的方法

### 混合变量

例

```less
div{
    width:@width;
    height:@height;
    border:1px solid red;
}
li{
    border:1px solid red;
}
ul{
    border:1px solid red;
}
```

使用混合,我们可以把同样的样式抽取过来:

```less
.border{
    border:1px solid red;
}
div{
    width:@width;
    height:@height;
    .border;
}
li{
    .border;
}
ul{
    .border;
}
```

### 带参混合

比如刚才的例子,当前div,li和ul 都需要一个像素的实线边框,但是我们想让每个边框的颜色不同

此时可以把颜色作为一个参数传入

```less
//把color变量作为参数传入
.border(@color){
    border:1px solid @color;
}
div{
	width:@width;
    height:@height;
    //传入参数
    .border(red)
}
li{
    .border(green);
}
ul{
	.border(pink)    
}
```

注意

在less中如果调用的方法有参数,单数使用的时候没有传参,会报错

解决方法:

1:传参

2:给函数设置默认值



```less
//把color变量作为参数传入,同时设置默认值
.border(@color:yellow){
    border:1px solid @color;
}
div{
    width:@width;
    height:@height;
    //传入参数
    .border(red)
}
li{
    .border(green);
}
ul{
    .border;
}
```

给函数设置多个默认值:

```less
//把color变量作为参数传入,同时设置默认值
.border(@color:yellow,@wt:1px){
    border:@wt solid @color;
}
div{
    width:@width;
    height:@height;
    //传入参数
    .border(red,10px)
}
li{
    .border(green,3px)
}
ul{
    .border;
}
```

### 匹配模式

相当于js中的if,但是又不完全是

满足条件才能匹配



举例子:画三角形

```less
//画三角形传统方法
div{
    width:0px;
    height:0px;
    border-style:solid;
    border-width:50px;
    border-color:red transparent transparent transparent;
}
```

此时我们画一个向下的三角形,但是三角形上下左右不同的样式,传统的模式,需要写多个相同的代码

此时,我们就可以用匹配模式,根据传入的值的不同,编写不同样式的三角形

```less
.snajiao(top,@w_,@c_){
    border-width:@w_;
    border-style:solid;
    border-color:transparent transparent @c_ transparent;
}
.sanjiao(left,@w_,@c_){
    border-width:@w_;
    border-style:solid;
    border-color:transparent transparent transparent @c_;
}


.sanjiao(right,@w_,@c_){
    border-width:@w_;
    border-style:solid;
    border-color:transparent transparent @c_ transparent;
}
div{
    width:0;
    height:0;
    .sanjiao(right,50px,red)
}
```

此时我们发现,如果我们需要多次调用,那么就需要在每次调用的时填写

width:0;height:0;

为了解决这个问题,我们使用@_

@_指代当前方法内的内容 每次调用的时候都会带上

```less
.sanjiao(top,@w_,@c_){
    border-width:@w_;
    border-style:solid;
    border-color:transparent transparent @c_ transparent;
}

.sanjiao(left,@w_,@c_){
    border-width:@w_;
    border-style:solid;
    border-color:transparent @c_ transparent transparent;
}
.sanjiao(bottom,@w_,@c_){
    border-width:@w_;
    border-style:solid;
    border-color:transparent transparent @c_ transparent;
}
//@_指代当前方法内的内容 每次调用的时候都会带上
@sanjiao(@_,@w_,@c){
    width:0;
    height:0;
}
div{
    .sanjiao(bottom,100px,red)
}
```

使用场景:

设置定位:

```less
.r(r){
    position:relative;
}
.f(a){
    position:absolute;
}
.f(f){
    position:fixed;
}


ul{
    li{
        a{
            .f(a);
            top:100px;
            left:300px;
        }
    }
}
```

### 运算

在less中,任何数组,颜色或者变量都可以参与运算,运算应该被包裹在括号中,例如:+-*/给宽度增加200px

```less
//运算
@test_width:500px;
//width:(@wid/500);
div{
    width:(@test_width+200);
    height:300px;
    background_color:rgb(155,116,116);
}
```

### 嵌套规则

&:代表上一层选择器

```less
ul{
    li{
        a{
            color:green;
            //&代表上级元素
            //当前表示选中了a
            &:hover{
                color:red:
            }
        }
    }
}
```

场景二,在less中只想选中子元素

html:

```html
<div>
    <li><a href="#">我是div的孙子a</a></li>
    <a href="#">我是div的儿子a</a>
</div>
```

```less
div{
    &>a{
        color:red;
    }
}
```

@arguments包含了所有传进来的参数

如果你不想单独处理每一个参数的话就可以这样写:

```less
.border_arg(@w_,@style,@color_){
    border:@arguments;
}
div{
    .border_arg(10px,solid red)
}
```

js中也有一个arguments对象,使用arguments.length来确定传递给每个函数参数的个数,然后使用

arguments对象来处理每个参数

```js
var a=function(a,b){
	console.log(arguments);
}
a(3,5);
```

arguments是个数组类型的是对象,类型不是数组,是Object对象类型

```js
console.log(arguments instanceof Array)//false
consoleo.log(arguments instanceof Object)//true
```

调用混合模式中添加!important后,css所有的属性值后面都会添加,提高权重

### sass

sass和less一样,也是一种css预处理器

文件类名.scss

```scss
//使用变量
$width:300px;
$height:150px;
$color:red;

div{
    width:$width;
    height:$height;
    background-color:$color;
}
ul{
    li{
        width:($width/3);
        height:($height/3);
        background-color:$color;
        margin:10px 0;
    }
}
```

编译为css

```css
div {
  width: 300px;
  height: 150px;
  background-color: red;
}

ul li {
  width: 100px;
  height: 50px;
  background-color: red;
  margin: 10px 0;
}

```



```scss
//编译前
$heighlight-color:#F90;
$heighligth-border:3px solid $heighlight-color;
div{
    width:400px;
    height:200px;
    //border:1px solid $heighlight-color;
    border:$heighlight-border;
}

//编译后
div{
    width:400px;
    height:200px;
    border:3px solid #F90;
}
```

sass和less的区别

### 相同点:

1:他们都是css预处理器,优化了普通的css,增加了变量,混合模式,匹配模式等方法,使的css的书写更为简单

### 不同点:

1:文件了类型的不同,sass的文件类型是scss,lessd的文件类型是.less

2:声明变量的方式不同,less声明变量使用@变量名,sass声明变量使用$变量名

3:less编译为css文件后,会生成一个和less文件同名的css文件

sass编译为css文件后,会生成和sass文件同名的css文件,同时还会生成一个压缩文件,即和sass同名.min.css



## Git

```css
git --version
git init
git status
git log
git relog
git branch
git branch -r
git branch -d
git branch master
git add .
git commit -m 'first commit'
git reset --hard HEAD^
git reset --hard 33d9d598d
git remote add origin https://....
git remote remove origin https://.
git push -u origin master
git push orgin master
git push
git clone https://.......
git switch master
git checkout master
git checkout -b dev
git merge dev
git pull origin master

https://github.com/cfg1573/test2302NB

```



### Git 常用命令

### 仓库

```css
# 在当前目录新建一个Git代码库
$ git init

# 新建一个目录，将其初始化为Git代码库
$ git init [project-name]

# 下载一个项目和它的整个代码历史
$ git clone [url]
```

### 配置

```css
# 显示当前的Git配置
$ git config --list

# 编辑Git配置文件
$ git config -e [--global]

# 设置提交代码时的用户信息
$ git config [--global] user.name "[name]"
$ git config [--global] user.email "[email address]"
```

### 增加/删除文件

```css
# 添加指定文件到暂存区
$ git add [file1] [file2] ...

# 添加指定目录到暂存区，包括子目录
$ git add [dir]

# 添加当前目录的所有文件到暂存区
$ git add .

# 添加每个变化前，都会要求确认
# 对于同一个文件的多处变化，可以实现分次提交
$ git add -p

# 删除工作区文件，并且将这次删除放入暂存区
$ git rm [file1] [file2] ...

# 停止追踪指定文件，但该文件会保留在工作区
$ git rm --cached [file]

# 改名文件，并且将这个改名放入暂存区
$ git mv [file-original] [file-renamed]
```

### 代码提交

```css
# 提交暂存区到仓库区
$ git commit -m [message]

# 提交暂存区的指定文件到仓库区
$ git commit [file1] [file2] ... -m [message]

# 提交工作区自上次commit之后的变化，直接到仓库区
$ git commit -a

# 提交时显示所有diff信息
$ git commit -v

# 使用一次新的commit，替代上一次提交
# 如果代码没有任何新变化，则用来改写上一次commit的提交信息
$ git commit --amend -m [message]

# 重做上一次commit，并包括指定文件的新变化
$ git commit --amend [file1] [file2] ...
```

### 分支

```css
# 列出所有本地分支
$ git branch

# 列出所有远程分支
$ git branch -r

# 列出所有本地分支和远程分支
$ git branch -a

# 新建一个分支，但依然停留在当前分支
$ git branch [branch-name]

# 新建一个分支，并切换到该分支
$ git checkout -b [branch]

# 新建一个分支，指向指定commit
$ git branch [branch] [commit]

# 新建一个分支，与指定的远程分支建立追踪关系
$ git branch --track [branch] [remote-branch]

# 切换到指定分支，并更新工作区
$ git checkout [branch-name]

# 切换到上一个分支
$ git checkout -

# 建立追踪关系，在现有分支与指定的远程分支之间
$ git branch --set-upstream [branch] [remote-branch]

# 合并指定分支到当前分支
$ git merge [branch]

# 选择一个commit，合并进当前分支
$ git cherry-pick [commit]

# 删除分支
$ git branch -d [branch-name]

# 删除远程分支
$ git push origin --delete [branch-name]
$ git branch -dr [remote/branch]
```

### 标签

```css
# 列出所有tag
$ git tag

# 新建一个tag在当前commit
$ git tag [tag]

# 新建一个tag在指定commit
$ git tag [tag] [commit]

# 删除本地tag
$ git tag -d [tag]

# 删除远程tag
$ git push origin :refs/tags/[tagName]

# 查看tag信息
$ git show [tag]

# 提交指定tag
$ git push [remote] [tag]

# 提交所有tag
$ git push [remote] --tags

# 新建一个分支，指向某个tag
$ git checkout -b [branch] [tag]
```

### 查看信息

```css
# 显示有变更的文件
$ git status

# 显示当前分支的版本历史
$ git log

# 显示commit历史，以及每次commit发生变更的文件
$ git log --stat

# 搜索提交历史，根据关键词
$ git log -S [keyword]

# 显示某个commit之后的所有变动，每个commit占据一行
$ git log [tag] HEAD --pretty=format:%s

# 显示某个commit之后的所有变动，其"提交说明"必须符合搜索条件
$ git log [tag] HEAD --grep feature

# 显示某个文件的版本历史，包括文件改名
$ git log --follow [file]
$ git whatchanged [file]

# 显示指定文件相关的每一次diff
$ git log -p [file]

# 显示过去5次提交
$ git log -5 --pretty --oneline

# 显示所有提交过的用户，按提交次数排序
$ git shortlog -sn

# 显示指定文件是什么人在什么时间修改过
$ git blame [file]

# 显示暂存区和工作区的差异
$ git diff

# 显示暂存区和上一个commit的差异
$ git diff --cached [file]

# 显示工作区与当前分支最新commit之间的差异
$ git diff HEAD

# 显示两次提交之间的差异
$ git diff [first-branch]...[second-branch]

# 显示今天你写了多少行代码
$ git diff --shortstat "@{0 day ago}"

# 显示某次提交的元数据和内容变化
$ git show [commit]

# 显示某次提交发生变化的文件
$ git show --name-only [commit]

# 显示某次提交时，某个文件的内容
$ git show [commit]:[filename]

# 显示当前分支的最近几次提交
$ git reflog
```

### 远程同步

```css
# 下载远程仓库的所有变动
$ git fetch [remote]

# 显示所有远程仓库
$ git remote -v

# 显示某个远程仓库的信息
$ git remote show [remote]

# 增加一个新的远程仓库，并命名
$ git remote add [shortname] [url]

# 取回远程仓库的变化，并与本地分支合并
$ git pull [remote] [branch]

# 上传本地指定分支到远程仓库
$ git push [remote] [branch]

# 强行推送当前分支到远程仓库，即使有冲突
$ git push [remote] --force

# 推送所有分支到远程仓库
$ git push [remote] --all
```

### 撤销

```css
# 恢复暂存区的指定文件到工作区
$ git checkout [file]

# 恢复某个commit的指定文件到暂存区和工作区
$ git checkout [commit] [file]

# 恢复暂存区的所有文件到工作区
$ git checkout .

# 重置暂存区的指定文件，与上一次commit保持一致，但工作区不变
$ git reset [file]

# 重置暂存区与工作区，与上一次commit保持一致
$ git reset --hard

# 重置当前分支的指针为指定commit，同时重置暂存区，但工作区不变
$ git reset [commit]

# 重置当前分支的HEAD为指定commit，同时重置暂存区和工作区，与指定commit一致
$ git reset --hard [commit]

# 重置当前HEAD为指定commit，但保持暂存区和工作区不变
$ git reset --keep [commit]

# 新建一个commit，用来撤销指定commit
# 后者的所有变化都将被前者抵消，并且应用到当前分支
$ git revert [commit]

暂时将未提交的变化移除，稍后再移入
$ git stash
$ git stash pop
```

### 其他

```css
# 生成一个可供发布的压缩包
$ git archive
```



Git是目前世界上最先进的分布式版本控制系统(没有之一)

Git有什么特点简单来说就是:高端大气上档次!

###  版本管理工具的分类

#### 1:svn(集中式)

集中式版本控制系统,版本库是集中存放在中央服务器的.而干活的时候,用的都是自己的电脑,所以要先从中央服务器取得最新的版本,然后开始干活,干完活了,再把自己的活推给中央服务器,中央服务器就好比是一个图书馆,你要改一本书,必须先从图书馆借出来,然后回到家自己改,改完了,再放回图书馆

#### 2:git(分布式)

分布式版本控制系统根本没有中央服务器,每个人的电脑上都是一个完整的版本库,这样,你工作的时候,就不需要联网了,因为版本库就在你自己的电脑上

和集中式版本控制系统相比,分布式版本控制系统的安全性要高很多,因为每个人的电脑里都有完整的版本库,某一个人的电脑坏掉了不要紧,随便从其他人那里复制一个就可以了,而集中式版本控制系统的中央服务器要是出了问题,所有人都没法干活了

在实际使用分布式版本控制系统的时候,奇石很少在两人之间的电脑上推送版本库的修改,因为可能你们俩不在一个局域网内,两台电脑互相访问不了,也可能今天你的同事病了,他的电脑压根开不了机,依次分布式版本控制系统通常也有一台充当服务器的电脑,但这个服务器的作用仅仅是用来方便交换大家的修改,没有他大家也一样干活,只是交换修改不方便而已

###### 控制台输入:git --version,显示安装的git版本号



### 1:创建本地版本库

Git操作



第一种创建git的方法

1:打开资源管理器,进入需要创建git仓库的目录下,在上方地址栏中输入cmd,打开命令提示符,输入git init	//初始化git,生成git可以管理的仓库

瞬间Git就把仓库建好了,而且告诉你是一个空的仓库(empty Git repository),当前目录下多了一个.git的目录,这个目录就是Git来跟踪管理版本库的,没事千万不要手动修改这个目录里面的文件.不然改乱了.就把Git仓库给破坏了,如果没有看见这个文件夹,因为.git文件夹是隐藏的文件夹,可以通过查看,勾选隐藏的项目勾选出来



第二种创建git的方法:

在需要创建git的版本库的文件夹下

按shift键后右键

点击 在此处打开Powershell窗口

输入git init命令,同样可以创建git版本库



第三种方法:

在vscode的文件下,右键,在集成终端中打开,输入git init即可



### 常规开发项目

创建项目,正常的代码

代码 一定要放到git仓库下,因为这是一个 Git仓库,放到其他地方Git再厉害也找不到这个文件

### 提交到本地仓库

第一步:git status	检查版本库的状态

第二步,用命令git add<file>告诉git,把文件添加到仓库

git add .	提交全部<注意!!!	git 空格 add 空格 点>

第三步:用命令git commit -m '提交说明'	告诉git,把文件提交到仓库

第四步:提交时,会提示配置用户

git config --global user.name 'username'	//username是你的git账号

git config --global user.email 'email'	//email是你的git邮箱

如果提示让输入用户名,接下来输入命令:

```css
git config --global user.name li_magisk				   //回车
git config --global user.email l1919202265@gmail.com	//回车
```

工作区有一个隐藏目录.git,这个不算工作区,而是Git的版本库

git的版本库里面存了很多东西,其中最重要的就是stage(或者叫index)的暂存区,还有Git为我们自动创建的第一个分支master,以及指向master的第一个指针叫HEAD

### 5:初始化一个Git仓库,使用git init命令

添加文件到Git仓库,分两步:

1:使用命令git add<file>,注意,可反复多次使用,添加多个文件;

2:使用命令git commit -m 'message'	完成

### 6:版本回退

金庸群侠传

存档

你不断对文件进行修改，然后不断提交修改到版本库里，就好比玩RPG游戏时，每通过一关就会自动把游戏状态存盘，如果某一关没过去，你还可以选择读取前一关的状态。有些时候，在打Boss之前，你会手动存盘，以便万一打Boss失败了，可以从最近的地方重新开始。Git也是一样，每当你觉得文件修改到一定程度的时候，就可以“保存一个快照”，这个快照在Git中被称为commit。一旦你把文件改乱了，或者误删了文件，还可以从最近的一个commit恢复，然后继续工作，而不是把几个月的工作成果全部丢失。

当然了，在实际工作中，我们脑子里怎么可能记得一个几千行的文件每次都改了什么内容，不然要版本控制系统干什么。版本控制系统肯定有某个命令可以告诉我们历史记录，在Git中，我们用`git log`命令查看：

```css
git log		//git提交日志
git relog	//git每一次提交的日志信息
```



#### 在Git中,我们用git log命令查看,提交的历史记录

### 7:回退

现在我们启动时光穿梭机,准备把index.html回退到上一个版本,也就是第三次添加10个li标签的那个版本,怎么做呢?

首先,Git必须知道当前版本是哪个版本,在Git中,用HEAD表示当前版本,也就是最新的提交`6d20e733...`(注意我的提交的ID和你的肯定不一样的),上一个版本就是HEAD^,上上个版本就是HEAD^^,当然我们往上100个版本写100个^比较容易数不过来,所以些好吃呢个HEAD~100

现在,我们要把当前版本 第四次添加类名four的divb标签 回退到上一个版本 第三次添加10个li标签,就可以使用git reset命令

```css
git reset --hard HEAD^
```

代码也会跟着自动的更新,会回退到第三次状态时的代码

### 8:后悔药

会的版本过分了,后悔了,只要上面的命令行窗口还没有关掉,你就可以顺着往上找找,找到那个某个版本的commit id是33d9d598d123bb1327ba2abd9b73b725000abd9c,于是就可以指定回到未来的某个版本:

```css
git reset --hard 33d9d598d
```

版本号没必要写全,前几位就可以了,Git会自动去找,当然也不能只写前一两位,因为Git可能会找到多个版本号,就无法确定哪一个

如果命令行关闭了,怎么办呢?记不住版本号了把?

Git提供了一个命令git reflog用来记录你的每一次命令:

## 5远程仓库

Git是分布式版本控制系统,同一个Git仓库,可以分布到不同的机器上,在呢么分布呢,最早,肯定值有一台机器有一个原始版本库,此后,别的机器可以克隆这个原始版本库,而且每台机器的版本库其实都一样的,并没有主次之分

你肯定会想,至少需要两台机器才能玩下远程仓库不是?到那时我只有一台电脑,怎么玩?

实际情况往往是这样,找一台电脑充当服务器的角色,每天24小时开机,其他每个人都从这个歌服务器仓库克隆一份到自己的电脑上,并且各自把各自的提交推送到服务器仓库里,也从服务器仓库中拉取别人的提交

完全可以自己搭建一一台运行Git的服务器,不过现阶段,为了学Git先搭建个服务器绝对是大题小做,好在这个世界上有个叫GitHub的神奇网站,从名字就可以看出,这个网站就是提供Git仓库托管服务的,所以,只要注册一个GitHub账号,就可以免费获得GitHub远程仓库

##### 1:注册账号

自行注册GitHub账号

登录到Github

新建一个远程仓库

##### 2本地git仓库和github仓库之间的传输是通过SSH加密,查看秘钥

鼠标右击Git bash Here下查看

```css
ls -al ~/.ssh	//检查ssh keys是否存在
```

此命令窗口	不支持Ctrl+v粘贴	需要右击	点击paste

```css
ssh-keygen -t rsa -C '***'		//添加一个ssh
```

ssh-add ~/.ssh/id_res                        生成新的key
   -t = The type of the key to generate
    密钥的类型
    -C = comment to identify the key
    用于识别这个密钥的注释
    So the Comment is for you only and you can put anything inside.
    Many sites and software are using this comment as the key name.
    所以这个注释你可以输入任何内容，很多网站和软件用这个注释作为密钥的名字

#### 本地管理员目录会出现一个.ssh文件夹

里面有id_rsa和id_rsa.pub两个文件

这两个就是SSH Key的秘钥对

id_rsa			//私钥

id_rsa.pub	 //公钥

登陆GitHub，打开“Account settings”，“SSH Keys”页面：

点击new SSH key

然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容：

ssh -T git@github.com   检测是否建立连接成功

如果不成功

```http
    https://blog.csdn.net/nightwishh/article/details/99647545
```



```
Host github.com
User 473203063@qq.com
Hostname ssh.github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa
Port 443
```

按shift

输入:wq 保存退出

为什么GitHub需要SSH Key呢？因为GitHub需要识别出你推送的提交确实是你推送的，而不是别人冒充的，而Git支持SSH协议，所以，GitHub只要知道了你的公钥，就可以确认只有你自己才能推送。
当然，GitHub允许你添加多个Key。假定你有若干电脑，你一会儿在公司提交，一会儿在家里提交，只要把每台电脑的Key都添加到GitHub，就可以在每台电脑上往GitHub推送了。
最后友情提示，在GitHub上免费托管的Git仓库，任何人都可以看到喔（但只有你自己才能改）。所以，不要把敏感信息放进去。

如果你不想让别人看到Git库，有两个办法，一个是交点保护费，让GitHub把公开的仓库变成私有的，这样别人就看不见了（不可读更不可写）。另一个办法是自己动手，搭一个Git服务器，因为是你自己的Git服务器，所以别人也是看不见的。这个方法我们后面会讲到的，相当简单，公司内部开发必备。

#### 2、添加到远程仓库

1.创建远程仓库
2.本地仓库添加到远程仓库

点击要提交的远程仓库：

把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程。
由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。

从现在起，只要本地作了提交，就可以通过命令：

```css
/*关联远程仓库*/ 
git remote add origin https://github.com/l1919202265/01webtest.git
/*断开连接*/
git remote remove origin
/*发送  推向到远程仓库*/
git push -u origin master
git push origin master
```



# 6、克隆远程仓库



上面，我们讲了先有本地库，后有远程库的时候，如何关联远程库。
现在，假设我们从零开发，那么最好的方式是先创建远程库，然后，从远程库克隆。
首先，登陆GitHub，创建一个新的仓库，名字叫xxx：
现在，远程库已经准备好了，下一步是用命令git clone克隆一个本地库：

登陆gitHub,点进项目，选择code,选择ssh,复制地址，当前地址就是我们克隆项目的地址

> git@github.com:cfg1573/test_QY133.git

> git@github.com:cfg1573/QY135Nb666.git

如果有多个人协作开发，那么每个人各自从远程克隆一份就可以了。

1、新建文件夹，输入cmd

2、输入命令：

```css
git clone git@github.com:cfg1573/test_QY133.git
```

回车 克隆完成

克隆完成，文件下载至本地

小结
要克隆一个仓库，首先必须知道仓库的地址，然后使用git clone命令克隆。
Git支持多种协议，包括https，但ssh协议速度最快。

# 6、分支的概念

分支就是科幻电影里面的平行宇宙，当你正在电脑前努力学习Git的时候，另一个你正在另一个平行宇宙里努力学习SVN。
如果两个平行宇宙互不干扰，那对现在的你也没啥影响。不过，在某个时间点，两个平行宇宙合并了，结果，你既学会了Git又学会了SVN！

分支在实际中有什么用呢？假设你准备开发一个新功能，但是需要两周才能完成，第一周你写了50%的代码，如果立刻提交，由于代码还没写完，不完整的代码库会导致别人不能干活了。如果等代码全部写完再一次提交，又存在丢失每天进度的巨大风险。

现在有了分支，就不用怕了。你创建了一个属于你自己的分支，别人看不到，还继续在原来的分支上正常工作，而你在自己的分支上干活，想提交就提交，直到开发完毕后，再一次性合并到原来的分支上，这样，既安全，又不影响别人工作。

> 注意，从远程仓库克隆下项目后，我们需要在分支上进行代码编写，不能直接在主分支上进行修改

# 7、分支操作

#### 1、gitHub新建一个远程仓库，在本地克隆

克隆成功：

#### 2、在克隆成功的项目下，查看分支：



##### 查看分支：git branch

*在哪个分支前,就表示当前在哪个分支

##### 创建分支：git branch 分支名

git branch de 创建了一个dev分支，dev是devlop的缩写，表示开发分支

我们接下来的程序会写在dev分支上，写完以后再合并到主分支中

##### 切换分支：

```css
git switch name或者git checkout name  /*name表示分支名*/
git switch dev	/*切换到dev分支*/
```

##### 创建并切换分支

```css
git switch -c name或者git checkout -b name
```

#### 合并某分支到当前分支：

如果要把dev分支合并到master 需要先切换到master分支，因为合并是要把分支合并到当前分支

```css
git merge dev
```

例：

在dev分支下新建index.html,index.css，

添加，提交

然后切换到主分支，此时主分支中没有新提交的index.html文件

合并分支， git merge dev ,这样就把dev分支的内容提交到了主分支下面

#### 删除分支：git branch -d name

我们用过以后的分支，如果不想用了可以删掉

#### 3、解决冲突

当多个分支同时修改同一处代码时（同一个文件时），合并时就会出现冲突的情况

如：

在dev分支中修改index.html,修改，提交;

切换到master分支，继续修改index.html，修改，提交

合并dev分支到main分支中，此时就会出现冲突

两个分支同时修改一个文件，git不知道要使用哪一次提交

发生冲突时Git会显示标记更改的内容

```html
<<<<<<<HEAD(当前的更改)
<h1>当前更改的内容</h1>
=======
<h1>传入的更改</h2>
>>>>>>>dev(传入的更改)
```



解决方法，手动更改

如：点击保留双方更改

点击后再次添加、提交

#### 4、查看分支情况



**git log也可以看到分支的	情况**

**git log --graph命令可以看到分支合并图**

# 8、分支策略

在实际开发中，我们应该按照几个基本原则进行分支管理：

首先，master分支应该是非常稳定的，也就是仅用来发布新版本，平时不能在上面干活；

那在哪干活呢？干活都在dev分支上，也就是说，dev分支是不稳定的，到某个时候，比如1.0版本发布时，再把dev分支合并到master上，在master分支发布1.0版本；

你和你的小伙伴们每个人都在dev分支上干活，每个人都有自己的分支，时不时地往dev分支上合并就可以了。
所以，团队合作的分支看起来就像这样：

# 9、多人协作

管理员先在远程仓库创建好仓库，并建立好相关分支，比如master分支，dev分支

建A,B两个文件夹，代表另个程序员进行克隆

要查看远程库的信息，用 git remote
用 git remote -v 显示更详细的信息

当团队成员从远程仓库克隆时，实际上Git自动把本地的master分支和远程的master分支对应起来了，并且，远程仓库的默认名称是origin。

> git push -u origin master //向远程仓库origin 的master 分支提交代码
>
> git pull origin master //拉取远程仓库origin 的master 分支的代码

要查看远程库的信息，用 git remote
用 git remote -v 显示更详细的信息

当你的小伙伴从远程库clone时，默认情况下，你的小伙伴只能看到本地的master分支。不信可以用git branch命令看看

现在，你的小伙伴要在dev分支上开发，就必须创建远程origin的dev分支到本地，于是他用这个命令创建本地dev分支和远程仓库的分支连接起来：

> git checkout -b dev origin/dev
> //等同于一下多个命令合并使用 创建一个dev分支并切换到dev分支下，同时和远程仓库的dev关联起来
>
> git branch dev //新建分支
> git checkout dev //切换分支
> //没有把本地的dev分支与远程的dev分支关联起来，此时是没有拉去数据的

现在，他就可以在dev上继续修改，然后，时不时地把dev分支push到远程：

在dev分支新建一个index.html.，添加 提交

多人协作时，大家都会往master和dev分支上推送各自的修改。但是一般master是稳定的只是用来发布新版本分支，工作干活的分支是dev分支，一般团队成员只会提交dev分支。

# 10、推送分支

推送分支，就是把该分支上的所有本地提交推送到远程库。推送时，要指定本地分支，这样，Git就会把该分支推送到远程库对应的远程分支上：

> git push origin master



如果要推送其他分支，比如dev，就改成：

> git push origin dev



但是，并不是一定要把本地分支往远程推送，那么，哪些分支需要推送，哪些不需要呢？

- master分支是主分支，因此要时刻与远程同步；
  - dev分支是开发分支，团队所有成员都需要在上面工作，所以也需要与远程同步；
- bug分支只用于在本地修复bug，就没必要推到远程了，除非老板要看看你每周到底修复了几个bug；
- feature分支是否推到远程，取决于你是否和你的小伙伴合作在上面开发。



你的小伙伴已经向origin/dev分支推送了他的提交，而碰巧你也对同样的文件作了修改，并试图推送：

**b同学也来进行提交，出现冲突**



解决办法也很简单，Git已经提示我们，先用git pull把最新的提交从origin/dev抓下来，然后，在本地合并，解决冲突，再推送：

> git pull origin dev



冲突的文件：



手动解决冲突：再次提交

git pull成功，但是合并有冲突，需要手动解决，解决的方法和分支管理中的解决冲突完全一样。解决后，提交，再push

dev分支有内容：

main分支下什么也没有，因为没有合并：

使用github解决远程仓库合并：

git branch --set-upstream-to=origin/dev dev

**因此，多人协作的工作模式通常是这样：**



>1. 从远程克隆仓库到本地
>2. 拉取建立本地开发dev分支并常规开发
>3. 用git push origin <branch-name>推送自己的修改；
>4. 如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；
>5. 如果合并有冲突，则解决冲突，并在本地提交；
>6. 没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功！
>7. 如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream-to <branch-name> origin/<branch-name>。

<hr>

# 11、添加成员

#### 邀请方：

#### 被邀请者：

点击邀请者发送的链接

此时被邀请者可以看到一个正常的仓库界面

接下来点击仓库的远程地址

>如果不想配置秘钥，可直接使用https的链接地址
>
>git  clone https的地址，就可以完成克隆了
>
>剩下的就是正常的推送

```css
/*使用 --allow-unrelated-histories 参数强制合并历史记录*/
git pull origin master --allow-unrelated-histories
```

```css
/*如果你想要强制覆盖推送到远程仓库，可以使用 --force 参数来执行 git push 命令。请确保在执行此操作之前，你已经备份了重要的代码和数据，因为强制覆盖推送会永久地替换远程仓库中的代码。*/
git push --force origin master

```





> ——横线之前是命令
>
> ——横线之后是解释说明



1.新建文件夹，上方文件地址栏输入cmd，打开命令行
2.git init——初始化一个本地仓库
3.git remote add origin git项目地址——本地仓库关联远程仓库（用http方式就行，ssh的话提前配置密钥）
4.git fetch origin master——强制关联远程master分支
5.git branch -r——查看远程仓库的所有分支

> 以上项目代码就已经克隆下来了，并且关联了远程仓库，同步了所有分支，下面创建我们自己的分支



6.git branch——查看本地的所有分支，绿色的字代表自己现在所在的分支
7.git checkout master——切换到master分支上
8.git checkout -b xxx——创建并切换到xxx分支上（xxx是你自定义的分支名）
9.git push -u origin xxx——将自己的xxx分支推至远程仓库（第一次推加-u参数，后续再推就不用加了，推的时候自己要在当前的xxx分           支上）
10.git status——查看当前状态，在哪个分支上，更改了那些文件
11.git add .——将更改的文件内容添加到暂存区（注意不要少打这个.）
12.git commit -m '备注更改内容'——提交到本地仓库
13.git push origin xxx——推送至远程的xxx分支（第一次提交加-u参数）

> 以上创建了自己的分支，更改内容，并提交到了远程仓库，下面同步测试分支



14.git checkout master----切换至master分支
15.git checkout -b dev origin/dev——创建并切换到dev分支，并且同步远程的dev分支
16.git pull origin dev——合并之前，现将远程的dev拉下来一下，以免有其他人推送过新功能
17.git merge xxx——合并xxx分支代码（注意：要往哪个分支上合并，就先切换到哪个分支上）
18.git push origin dev——推送到远程的dev分支

> 同理：推送到master分支



19.git checkout master——切换至master分支
20.git pull origin master——拉下远程master分支的新代码
21.git merge xxx——将自己的xxx分支合并到master
22.git push origin master——推送至远程master

> 拉取别人分支
> 如果要拉取别人的分支，但git branch -r 发现远程并没有别人的这个分支



23.git remote update origin --prune——同步远程仓库的所有分支，这样可以拉别人的分支一起开发



> 最后：删除自己的本地分支和删除远程仓库的分支（要删除哪个分支，当前就不能在这个分支上）

git branch -d xxx——删除本地的xxx分支,该分支没有任何未提交的内容
git branch -D xxx——删除本地的xxx分支,该分支存在未提交的内容，强制删除
git push origin --delete xxx——删除远程仓库的xxx分支

```css
/*使用 --allow-unrelated-histories 参数强制合并历史记录*/
git pull origin master --allow-unrelated-histories
```

```css
/*如果你想要强制覆盖推送到远程仓库，可以使用 --force 参数来执行 git push 命令。请确保在执行此操作之前，你已经备份了重要的代码和数据，因为强制覆盖推送会永久地替换远程仓库中的代码。*/
git push --force origin master

```



#### 可能存在的问题

```css
1:$ git push origin master
Username for 'https://github.com': li_magisk
Password for 'https://li_magisk@github.com':
remote: Support for password authentication was removed on August 13, 2021.
remote: Please see https://docs.github.com/en/get-started/getting-started-with-git/about-remote-repositories#cloning-with-https-urls for information on currently recommended modes of authentication.
fatal: Authentication failed for 'https://github.com/l1919202265/Mynotes.git/'



此问题由于GitHub 在2021年8月13日删除了对密码身份验证的支持，并建议采用其他身份验证方式。这意味着你不能再使用密码直接进行对远程仓库的推送。

为了解决这个问题，你可以考虑以下两种方法来完成身份验证：

使用 SSH 密钥身份验证：使用 SSH 密钥进行身份验证是一个更安全和推荐的方式。首先，确保你已经生成了 SSH 密钥对，并将公钥添加到你的 GitHub 帐户中。然后，修改你的远程仓库的 URL，将其替换为 SSH URL。可以使用以下命令来修改 URL：

git remote set-url origin git@github.com:l1919202265/Mynotes.git
 
这将把远程仓库的 URL 修改为使用 SSH 协议进行身份验证。

使用访问令牌（Personal Access Token）进行身份验证：如果你不打算使用 SSH 密钥进行身份验证，你可以生成一个访问令牌并将其用作密码。访问令牌是一个用于访问 GitHub API 的身份验证凭证。你可以在你的 GitHub 帐户的设置中生成一个访问令牌。生成令牌后，在执行  git push  命令时，使用生成的令牌替代密码即可。

Username for 'https://github.com': li_magisk
Password for 'https://li_magisk@github.com':
 
这些输入提示是等待你输入 GitHub 的用户名和密码。因为现在不再支持直接使用密码进行身份验证，所以你需要使用其他方法进行身份验证。
```

可能存在的问题

```css
//问题	错误提示
error: failed to push some refs to 'https://gitee.com/linkmagisk/Find-House.git'


//解释出现错误的主要原因是gitee(github)中的README.md文件不在本地代码目录中 
此时我们要执行git pull --rebase origin master命令README.md拉到本地，
任何然后执行git push origin master


//解决办法
git pull --rebase origin master
```

### 自添加

```css
/*强制推送		--force(强制)*/
git push --force origin master

/*强制拉取*/
git pull --force origin master


/*重命名分支名为dev*/
git branch -M dev
```

# 移动端

## 移动端基础

本章目标

了解移动端产品分类及现状

会调试移动端项目

会使用viewport视口标签定义理想视口

会使用rem布局网页---重点

### 什么是移动web

移动web,运行在移动设备上的页面网页

移动设备包括:手机 平板 地铁展示栏.商场的智能导航机器人其他的一些持触摸设备等

### 产品分类

app(手机应用)

现在流行的app大部分都是原生app开发者开发

	安卓开发工程师
	
	ios开发工程师

使用JavaScript来开发原生app

> phoneGap
>
> React native ...

uniapp

### H5

是一项综合的技术,基本都是运行在浏览器中

> PC浏览器:Chrome	Safari	火狐
>
> 移动端浏览器:后续专门介绍

### APP与H5的优劣势

App

> 优势:
>
> > 功能完善[如何调用产品电量]	体验好	可以离线使用[没有网页调用]

> 劣势:
>
> > 开发成本高[不同平台的需要开发不同的版本]	迭代不可控[上线通过的时间不受控制]	内容限制

H5

> 优势:
>
> > 跨平台	开发成本低	更容易迭代[连上服务器直接上传修改]

> 劣势
>
> > 功能有限	操作体验欠佳	无法离线使用

### H5运行环境的分类

移动端浏览器

原生App的webview中(hyBrid模式)

开发的H5页面嵌入到App的webview中显示

[webview就像一个嵌套在App的浏览器



为什么会出现这种浏览器?

> 很好的发挥两者的优势,规避两者的弱势
>
> 涉及到操作系统级别的选择用app来做,需要及时更新的就选择H5,分工明确
>
> 这种模式,可能就是以后工作中最经常用到的

webview不需要我们 来书写,安卓和iOS内部已经有这个东西了,我们只需要吧写好的页面传到服务器上,把服务器地址给安卓或iOS工程师即可,由他们把我们放入我们的页面放入webview中



安卓加载页面代码:[了解]

```js
//方式一:加载一个页面
webView.loadUrL('http://www.baidu.com');

//方式二:加载应用资源文件内的网页
webView.loadUrL('file:///android_asset/test.html');

//方式三:加载一段代码
webView.loadUrl(String data,String mimeType,String encoding);
```

### PC与移动web开发的区别

> 终端设备

> 输入特性
>
> > pc:靠键盘输入
> >
> > 移动端:软键盘	语音输入	科大讯飞

> 屏幕
>
> > pc:分辨率差别不大,不论什么样的分别率都需要版心放素材
> >
> > 移动端:移动设备屏幕大小分辨率各种各样曾出不穷,需要兼容不同的屏幕

> 浏览器
>
> > 浏览器差别不大,都是使用同样的内核	谷歌	IE等等

> 开发调试
>
> 移动端:
>
> 视口:
>
> > 布局视口:
> >
> > > 在写h5页面时候进行的布局分配
> >
> > 视觉视口:
> >
> > > 看到屏幕的样子

> 布局方式
>
> > 我们前面学习的pc端的布局	浮动定位等等	在移动端同样适用

### 移动端屏幕

> DPI
>
> > 代表屏幕每英寸的像素数量,即像素密度
> >
> > 高DPI屏幕显示的元素会比较精细(看起来会比较小),低DPI屏幕显示的元素相对来说就比较粗糙(看起来会比较大)

> 像素分类:
>
> > 设备像素(device independt pixels):
> >
> > 设备屏幕的物理像素,任何设备的物理像素的数量都是固定的

> css像素(css pixels):
>
> > 又称逻辑像素,是为 web开发者创造的,在css和JavaScript中使用的一个抽象的层[就是我们自己书写的多少px的像素]

#### 屏幕缩放

##### pc端:

> css的1个像素往往都是对应电脑屏幕的1个物理像素

##### 移动端:

> 由于屏幕尺寸的限制,缩放是经常性的操作
>
> 缩小操作时,1个设备像素覆盖了多少个css像素
>
> 放大操作时,1个css像素覆盖了多少个设备像素

#### DPR:设备像素比

设备像素比DPR(device Pixels Ratio)是默认缩放为100%的情况下,设备像素和css像素的比值

> DPR=设备像素/css像素(某一方向上)

DPR值越大,屏幕分辨率越高

DPR=640/320;	2

#### Retina屏幕

同样大小的屏幕上,像素多了一倍,DPR=2;

DPR=2的屏幕上最早出现在苹果4s这款手机上

#### 移动端浏览器及内核分析

##### pc浏览器

Chrome	Safari	Firefox	IE

##### 移动端浏览器类型

内置浏览器[手机到手后,手机厂商已经内置号的浏览器]

可下载浏览器[可自行下载浏览器]

代理浏览器[知道]

webView[H5页面运行在app端内部的浏览器]



##### 内核

> 浏览器内核:也被称为渲染引擎或排版引擎,主要用于对网页语法进行解释,并进行网页渲染,将网页代码转换为看得到的页面,可分为两部分:渲染引擎和js引擎

Gecko内核,css前缀为'-moz-',代表Firefox

WebKit内核,css前缀为"-webkit-",代表Chrome	苹果	微信等

Presto内核,css前缀为"-o-",代表Opera(欧朋)

Trident内核,css前缀为"-ms-"代表IE



移动端开发测试浏览器

使用Chrome浏览器作为移动开发测试浏览器的原因,很多的手机都用webkit为渲染引擎

Chrome浏览器移动测试

> 浏览器的基本设置-清除缓存
>
> 勾选代表清除缓存,应用场景:
>
> > 我们更新完html代码,发现不生效,是因为此时浏览器给我们展示的缓存的数据,此时需要清除缓存,擦能展示最新的内容

### 视口

> ###### 布局视口:写html代码时的布局宽高
>
> ```html
> <style>
>  header{height: 50px ; background: pink; margin-bottom: 10px;}
>  aside{width: 30%; background: red; height: 300px; float: left;}
>  article{width: 68%; background: pink; height: 300px; float: left;}
> </style>
> <body>
>  <header></header>
>  <aside></aside>
>  <article></article>
> </body>
> 
> ```
>
> > 把以上代码放在移动设备上预览,页面整体被压缩,相同的内容,当窗口变窄,只是尽可能缩小网站来让用户看到网站的全貌,这对易读性来说不是件好事,在移动端上如何显示pc端的网页呢,在移动端上视口与移动浏览器屏幕宽度不在相关联,而是完全独立的,我们称它为布局视口,实际为卓面容纳浏览器设计的网站,默认的布局视口宽度大于手机屏幕的宽度
> >
> > ###### 视觉视口:眼在页面上看到的内容
> >
> > 虽然布局视口很大程度上帮助了桌面网站到手机的转移,但我们还是不能完全无视移动端设备的屏幕尺寸
> >
> > > 视觉视口使用户设备所能看到的网站区域,就是浏览器的宽高,只是在pc端,浏览器窗口可以随意改变大小,我们可以直观的看道,而在client端,大部分手机	平板的浏览器是不支持改变浏览器宽高的,所以其视觉视口就是其屏幕大小,用户可以通过缩放来操作视觉视口,同时不会影响布局视口,布局视口仍然保持原来的宽度	需要注意的is视觉视口与设备屏幕一样宽,并且它的css像素的数量会随着用户的缩放而改变

> ###### 理想视口:
>
> > 默认情况下,一个手机或平板浏览器的布局狂赌在980px或1024px,虽然这能让桌面网站不被压扁,但是这并不理想,尤其对手机用户,因为子啊狭窄的屏幕上更适合一个狭窄的网站	那么真正适合手机的视口是什么呢?

>###### viewport理想视口
>
>> 布局视口宽度=视觉视口宽度=设备宽度(=内容宽度)
>>
>> ```html
>> <meta name="viewport" content="width=device-width, initial-scale=1.0 "/>;
>> ```
>>
>> ```html
>> <meta name="viewport" content="width=device-width, initial-scale=1.0,user-scalable=no,maximum-scale=1.0,minimum-scale=1.0">
>> ```
>>
>> 

###### 自定义用户代码片段

```json
{
	"html": {
		"prefix": "html",
		"body": [
			"<!DOCTYPE html>",
			"<html>\n",
			"<head>",
			"\t<meta charset=\"UTF-8\">",
			"\t<meta name=\"viewport\" content=\"width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0\">",
			"\t<meta http-equiv=\"X-UA-Compatible\" content=\"ie=edge\">",
			"\t<title>Document</title>",
			"\t<link rel=\"stylesheet\" href=\"$1\">",
			"\t<script src=\"$2\"></script>",
			"</head>\n",
			"<body>\n$3",
			"</body>\n",
			"</html>"
		],
		"description": "The full sample code - html5."
	}
}
```

### 移动网页开发

###### 移动网页开发和pc网页开发有什么异同?

> ###### 不同点
>
> > 适配不同的分辨率和屏幕尺寸
> >
> > 兼容的浏览器

> ###### 不同点
>
> > 布局结构
> >
> > 使用的技术

### 使用相对长度单位em布局网页内容

em是描述相对于当前对象内文本的字体尺寸,它是相对长度单位[相对于父元素的font-size值进行变化的]

一般浏览器字体大小默认为16px

使用场景:当首行缩进字体的时候

###### 相对单位em的特性

> em的单位并不是固定的
>
> em会继承父级元素的字体大小(相对于父级的字体大小二发生变化)

### 相对单位rem

相对单位的特性:

> rem的值并不是固定的
>
> rem是相对根节点html发生变化的(和父节点无关)
>

 实际开发中一般默认的把html根节点设置为10px(62.5%)或者是100px,方便后续计算



通过js和rem动态设置字体大小

```html
<!DOCTYPE html>
<html>

    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0">
        <meta http-equiv="X-UA-Compatible" content="ie=edge">
        <title>Document</title>
        <style>
        	 a {
  				text-decoration: none;
			}
			li {
  				list-style: none;
			}
			* {
  				margin: 0;
  				padding: 0;
			}
			.phonebox {
  				height: 100Vh;
  				background-color: #eeeeee;
			}
			.phonebox header nav {
  				display: flex;
  				align-items: center;
  				padding: 1rem 0;
  				justify-content: space-around;
  				font-size: 18px;
  				background: url(../images/back.png) 0rem center no-repeat;
  				background-size: 10%;
  				background-color: red;
  				color: white;
			}
			.phonebox main ul:nth-of-type(1) li {
  				font-size: 1.6rem;
  				display: flex;
  				padding: 0 1rem;
  				align-items: center;
  				height: 4rem;
  				box-shadow: 0 0 0.1rem gray;
  				background-color: white;
			}
			.phonebox main ul:nth-of-type(2) {
  				margin-top: 1rem;
			}
			.phonebox main ul:nth-of-type(2) li {
  				font-size: 1.6rem;
  				display: flex;
  				padding: 0 1rem;
  				align-items: center;
  				height: 4rem;
  				box-shadow: 0 0 0.1rem gray;
  				background-color: white;
			}
			.phonebox footer {
  				margin-top: 1rem;
			}
			.phonebox footer a {
  				height: 4rem;
  				font-size: 1.6rem;
  				color: #f66666;
  				background-color: white;
  				display: flex;
  				align-items: center;
  				justify-content: space-around;
			}

        </style>
    </head>

    <body>
        <div class="phonebox">
            <header>
                <nav>设置</nav>
            </header>
            <main>
                <ul>
                    <li>个人信息</li>
                    <li>清空缓存</li>
                </ul>
                <ul>
                    <li>关于我们</li>
                    <li>意见反馈</li>
                    <li>检查更新</li>
                </ul>
            </main>
            <footer>
                <a href="#">退出当前账号</a>
            </footer>
        </div>
    </body>

</html>
<script>
    function setRem() {
        var uiWidth = 375;
        var clientWidth = document.documentElement.clientWidth || document.body.clientWidth;
        var html = document.getElementsByTagName('html')[0];
        html.style.fontSize = (clientWidth / uiWidth) * 10 + 'px'
    }
    window.addEventListener('resize', setRem);
    window.addEventListener('load', setRem);
</script>
```

> 相对单位em是集相对大小和绝对大小的有点与一身
>
> 通过它既可以做到只修改根元素字体大小就成比例的调整页面所有字体大小
>
> 又可以避免字体大小逐层复合的连锁反应

## 响应式布局&媒体查询

### 自适应和响应式布局

#### 自适应

> 为了解决在不同设备大小的设备上呈现相同的网页

#### 如何实现

> 自适应主要是指的宽度的自适应
>
> 百分比的流式布局【宽度按照百分比进行布局】

使用setRem.js,css布局单位px改为rem,rem单位为移动端适配

rem的大小根据根节点html的字体大小自行调整,例如:html字体大小为16px,1rem=16px;html字体大小为10px;1rem=10px;2rem=20px

```js
function setRem(){
    var uiWidth=375;
    var html=document.getElementsByTagName('html')[0];
    var clientWidth=document.documentElement.clientWidth||document.body.clientWidth;
    html.style.fontSize=(clientWidth/uiWidth)*10+'px';
}
window.addEventListener('resize',setRem);
window.addEventListener('load', setRem);
```

### 响应式布局

响应式布局是Ethan Marcotte[伊桑马 卡特]在2010年5月份提出的一个概念,简而言之,就是一个网站能够兼容多个终端——而不是为每个终端做一个特定的版本。这个概念是为了解决移动互联网浏览而诞生的。

大白话

> 一个网站能够兼容多个终端
>
> 是同一页面在不同屏幕尺寸下有不同的布局,一套页面,可以再不同的设备商正常显示

当页面足够小的时候,会隐藏掉一部分内容,重点显示主要的内容

例如:

屏幕最大480px时,展示一套css样式

屏幕最小480px,最大760px,展示一套css样式

屏幕最小760px,最大995px时,展示一套css样式

屏幕最小1100px时,展示一套css样式

将三种已有的开发技术整合起来,并命名

> 弹性布局
>
> 弹性图片
>
> 媒体和媒体查询

## 媒体查询

媒体查询(Media Queries)

> 媒体类型
>
> 媒体特战
>
> 关键词

媒介	平台

兼容性

> 移动端上一般对css3支持比较好的高级浏览器不需要考虑响应式布局的媒体查询的兼容问题
>
> IE8及以下版本的浏览器不支持媒体查询

### 什么事媒体查询

> 媒体：指的就是各种设备(移动设备、PC设备)
>
> 查询：指的是要检测属于那种设备
>
> 
>
> 媒体查询:通过查询当前属于哪种设备,让网页能够在不同的设备上正常的预览。根据设备展示不同的css样式

#### 媒体类型：

1、all（所有的设备）

2、print（打印设备）

screen（屏幕、电脑屏幕、平板电脑，智能手机）

常用的是以上三种，w3c规定来了10余种媒体类型，最常用的就是上述三种

| 值                            | 描述                                                         |
| :---------------------------- | :----------------------------------------------------------- |
| <font color=red>all</font>    | <font color=red>用于所有设备</font>                          |
| aural                         | 已废弃。用于语音和声音合成器                                 |
| braille                       | 已废弃。 应用于盲文触摸式反馈设备                            |
| embossed                      | 已废弃。 用于打印的盲人印刷设备                              |
| handheld                      | 已废弃。 用于掌上设备或更小的装置，如PDA和小型电话           |
| <font color=red>print</font>  | <font color=red>用于打印机和打印预览</font>                  |
| projection                    | 已废弃。 用于投影设备                                        |
| <font color=red>screen</font> | <font color=red>用于电脑屏幕，平板电脑，智能手机等。</font>  |
| speech                        | 应用于屏幕阅读器等发声设备                                   |
| tty                           | 已废弃。 用于固定的字符网格，如电报、终端设备和对字符有限制的便携设备 |
| tv                            | 已废弃。 用于电视和网络电视                                  |


#### 媒体的特性：

用来描述设备的特点,比如宽度,高度

可以将媒体特性看成:

> <font color=red>“媒体类型（判断条件）+ CSS（符合条件的样式规则）”</font>



| 值                      | 描述                                                         |
| :---------------------- | :----------------------------------------------------------- |
| aspect-ratio            | 定义输出设备中的页面可见区域宽度与高度的比率                 |
| color                   | 定义输出设备每一组彩色原件的个数。如果不是彩色设备，则值等于0 |
| color-index             | 定义在输出设备的彩色查询表中的条目数。如果没有使用彩色查询表，则值等于0 |
| device-aspect-ratio     | 定义输出设备的屏幕可见宽度与高度的比率。                     |
| device-height           | 定义输出设备的屏幕可见高度。                                 |
| device-width            | 定义输出设备的屏幕可见宽度。                                 |
| grid                    | 用来查询输出设备是否使用栅格或点阵。                         |
| height                  | 定义输出设备中的页面可见区域高度。                           |
| max-aspect-ratio        | 定义输出设备的屏幕可见宽度与高度的最大比率。                 |
| max-color               | 定义输出设备每一组彩色原件的最大个数。                       |
| max-color-index         | 定义在输出设备的彩色查询表中的最大条目数。                   |
| max-device-aspect-ratio | 定义输出设备的屏幕可见宽度与高度的最大比率。                 |
| max-device-height       | 定义输出设备的屏幕可见的最大高度。                           |
| max-device-width        | 定义输出设备的屏幕最大可见宽度。                             |
| max-height              | 定义输出设备中的页面最大可见区域高度。                       |
| max-monochrome          | 定义在一个单色框架缓冲区中每像素包含的最大单色原件个数。     |
| max-resolution          | 定义设备的最大分辨率。                                       |
| max-width               | 定义输出设备中的页面最大可见区域宽度。                       |
| min-aspect-ratio        | 定义输出设备中的页面可见区域宽度与高度的最小比率。           |
| min-color               | 定义输出设备每一组彩色原件的最小个数。                       |
| min-color-index         | 定义在输出设备的彩色查询表中的最小条目数。                   |
| min-device-aspect-ratio | 定义输出设备的屏幕可见宽度与高度的最小比率。                 |
| min-device-width        | 定义输出设备的屏幕最小可见宽度。                             |
| min-device-height       | 定义输出设备的屏幕的最小可见高度。                           |
| min-height              | 定义输出设备中的页面最小可见区域高度。                       |
| min-monochrome          | 定义在一个单色框架缓冲区中每像素包含的最小单色原件个数       |
| min-resolution          | 定义设备的最小分辨率。                                       |
| min-width               | 定义输出设备中的页面最小可见区域宽度。                       |
| monochrome              | 定义在一个单色框架缓冲区中每像素包含的单色原件个数。如果不是单色设备，则值等于0 |
| orientation             | 定义输出设备中的页面可见区域高度是否大于或等于宽度。         |
| resolution              | 定义设备的分辨率。如：96dpi, 300dpi, 118dpcm                 |
| scan                    | 定义电视类设备的扫描工序。                                   |
| width                   | 定义输出设备中的页面可见区域宽度。                           |



媒体特性语法：

```html
<style>
@media  媒体类型  and  （媒体特性）{ 
        CSS样式 
}
</style>


例子：
  @media screen and (max-width:500px) {
            body{
                background-color: yellow;
            }
        }
```

#### 媒体查询案例：

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
     
        @media screen and (max-width:500px){
            body{
                background-color: yellow;
            }
        }

        @media screen and (min-width:501px) and (max-width:900px) {
            body{
                background-color: green;
            }
        }

        @media screen and (min-width:901px) {
            body{
                background-color: red;
            }
        }

    </style>
</head>

<body>
   <!--  
    - 宽度大于900px 背景red
    - 介于500-900px 背景 green
    - 小于500px 背景yellow -->



</body>

</html>
```



#### 通过媒体查询，解决屏幕获取不到高清图片

思路： 通过媒体查询dpr的值，不同的值显示不同质量的图片

在开发中，我们会根据dpr的值显示1倍图，2倍图，3倍图等

此处为了演示，我们只让显示不同的图片，来代替123倍图

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        div{
            width: 800px;
            height: 500px;
        }
        @media screen and (-webkit-min-device-pixel-ratio: 1){
            div{
                background:url(./image/1.jpg);
            }
        }

        @media screen and (-webkit-min-device-pixel-ratio: 2){
            div{
                background:url(./image/2.jpg);
            }
        }

        @media screen and (-webkit-min-device-pixel-ratio: 3){
            div{
                background:url(./image/3.jpg);
            }
        }
    </style>
</head>
<body>
    <div>

    </div>
</body>
</html>
```



刚才判断属性的时候，我们使用了and关键词，and表示多个条件同时满足

除了and，还有其他的关键词

#### and：表示多个条件同时满足

```css
@media screen and （max-width：1200px）{样式代码…}

```



#### only:

only：指定某种特定的媒体类型，可以用来排除不支持媒体查询的

```css
<link href = "style.css"  media = " only screen and  (max-width：500px) "  
```

标志，只有在屏幕最大宽度是500px的屏幕下，会执行style.css样式only.css:

```css
div{
    width: 100%;
    height: 300px;
    background-color: yellow;
}
```

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <link rel="stylesheet" href="./css/only.css" media="only screen and (max-width:500px)">
    <script src=""></script>
</head>

<body>
    <div></div>

</body>

</html>
```

#### not：

排除某种指定的媒体类型，即排除符合表达式的设

表示取反

```css
@media  not  print  and （max-width：1200px）{样式代码…}

```

**引入方式：**

@media方式：

```
@media 媒体类型 {
        选择器{ /*样式代码写在这里…*/}
}

```

### 7、媒体查询冲突

```html
<link rel="stylesheet" href="styleA.css" 
    media="screen  and (min-width: 800px)">
<link rel="stylesheet" href="styleB.css" 
    media="screen  and (min-width: 600px) and (max-width: 800px)">
<link rel="stylesheet" href="styleC.css" 
    media="screen  and (max-width: 600px)">

```

如图，在800,600等临界值处，会有冲突

修改为：

```html
<link rel="stylesheet" href="styleA.css" media="screen and(min-width:801px)">
<link rel="stylesheet" href="styleB.css" 
    media="screen and (max-width: 800px)">
<link rel="stylesheet" href="styleC.css" 
    media="screen and (max-width: 600px)">

```

#### 8、响应式实战：热门活动



#### 屏幕分辨率大于1024px：

![image-20210411211218315](/image-20210411211218315.png)

```css
@media all and (min-width:1024px) {
    .box{
        width: 1024px;
        padding: 30px;
        }
}
/*省略其他的CSS样式*/

```

#### 屏幕分辨率在638px到1023px之间:

![image-20210411211308313](/image-20210411211308313.png)

```css
@media all and (min-width:638px) and (max-width:1023px) {
    .box{
        width: 638px;
        padding: 24px;
        margin: 10px auto 0;
}
/*省略其他的CSS样式*/

```

#### 屏幕分辨率在320px到637px之间:

![image-20210411211338192](/image-20210411211338192.png)

```css
@media all and (min-width:320px) and (max-width:639px) {
    .box{
        width: 320px;
        padding: 20px;
        margin: 10px auto 0;
}
/*省略其他的CSS样式*/

```

示例：

代码：

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
        ul{
            padding: 20px;
            overflow: hidden;
            list-style: none;
        }
        ul>li{
            float: left;
            margin: 20px;
        }

        /* 屏幕分辨率在320px到639px之间: */
        @media screen and (min-width:320px) and (max-width:639px) {
            ul{
                width: 240px;
                background-color: rgb(187, 130, 24);
            }
            li{
                width: 200px;
                height: 50px;
                background-color: rgb(35, 202, 194);
            }
        }

        /* 屏幕分辨率在638px到1023px之间: */
        @media screen and (min-width:638px) and (max-width:1023px) {
            ul{
                width: 480px;
                background-color: rgb(36, 133, 120);
            }
            li{
                width: 200px;
                height: 50px;
                background-color: rgb(36, 170, 36)
            }
        }

            /* 屏幕分辨率大于1024px： */
        @media screen and (min-width:1024px) {
            ul{
                width: 960px;
                background-color: rgb(197, 139, 73);
            }
            li{
                width: 200px;
                height: 50px;
                background-color: rgb(36, 170, 36)
            }
        }
    </style>
</head>

<body>
    <ul>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
    </ul>

</body>

</html>
```



### 9、响应式布局优缺点

#### 优点:

- 不同分辨率设备灵活性强,[比自适应强，自适应只是宽度的自适应]
- 多终端视觉和操作体验好
- 响应式web设计中的大部分技术都可以用在WebApp开发中[可以用在移动端设备，也可以用在pc端]
  

#### 缺点

- 兼容各种设备工作量大，效率低下
- 代码累赘，会出现隐藏无用的元素，加载时间加长



### 10、响应式和自适应的区别

- 响应式的概念覆盖了自适应，但是包括的东西更多。响应式布局可以根据屏幕的大小自动的调整页面的展现方式，以及布局
- 自适应还是暴露出一个问题，如果屏幕太小，即使网页能够根据屏幕大小进行适配，也会感觉在小屏幕上查看，内容过于拥挤
- 响应式解决了自适应布局的问题。它可以自动识别屏幕宽度、并做出相应调整，布局和展示的内容可能会有所变动



## 11、rem响应式布局

如果移动端页面只在移动端访问，那么使用rem可以实现响应式布局



#### 实现原理：

动态改变 html的font-size值的大小，来完成rem实现响应式布局



#### rem实现响应式原理：

rem 的值都是根据html的fontsize进行计算的

统一缩放元素大小，只要修改html的fontsize

```css
html  {   font-size: 100px;
		/* 将图片的大小变成 75*75 */
		/* font-size: 50px; */}
main {
		 width: 1.5rem; height: 1.5rem;background-color: #f38;
		 }
/*省略其他的CSS样式*/

```





#### 使用rem开发响应式布局步骤1:

- 从Ui设计师拿到设计稿，一般尺寸都是以iphone 6的尺寸为准 750**1334（638*1136）
- 在样式中给html设定一个fontsize的值，我们一般设置一个方便后续计算的值，例如10px、100px等，我们使用100px
- 写样式
  - 完全按照设计稿的尺寸来写样式，设计稿上的长度、height、margin、padding、字体的值是多少，我们就写多少，这样可以100%还原设计稿
  - 注意：需要把得到的像素值/100px,转换为rem单位



#### 使用rem开发响应式布局步骤2:

- 根据当前屏幕的宽度和设计稿的宽度来重新计算html的FontSize的大小
- 根据当前屏幕宽度和设计稿的宽度的比例，动态计算当前宽度下的fontsize值大小，如果fontsize值改变了，之前设定的所有的rem单位的值自动会跟着改变

```javascript
<script>
    function setRem() {
        var ui_w = 375;
        // 获取屏幕的宽度
        var clientWidth = document.documentElement.clientWidth || document.body.clientWidth;
       

        // 通过js动态改变html根节点字体大小
        var html_ = document.getElementsByTagName('html')[0];
        html_.style.fontSize = (clientWidth/ui_w)*100 +'px';
    }
    // window.onresize 浏览器被重置大小执行事件
    window.onresize = setRem;
		window.onload = setRem;
</script>
```



### 12、判断是pc还是移动浏览器

通过JavaScript判断终端类型

```javascript
//把请求头信息转为小写  
//user agent是指用户代理,使服务器能够识别客户使用的操作系统及版本、CPU 类型、浏览器及版本、浏览器渲染引擎、浏览器语言、浏览器插件等。
sUserAgent = navigator.userAgent.toLowerCase();

sUserAgent.match('ipad') == "ipad";
sUserAgent.match('ucweb') == "ucweb";
...
```





```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
	<title>判断是PC还是移动端浏览器</title>
</head>
<body>


</body>
</html>

<script>
    
function browserRedirect() {
var curURL = window.location.href;
var sUserAgent = navigator.userAgent.toLowerCase();

var bIsIpad = sUserAgent.match(/ipad/i) == "ipad";
var bIsIphoneOs = sUserAgent.match(/iphone os/i) == "iphone os";
var bIsMidp = sUserAgent.match(/midp/i) == "midp";
var bIsUc7 = sUserAgent.match(/rv:1.2.3.4/i) == "rv:1.2.3.4";
var bIsUc = sUserAgent.match(/ucweb/i) == "ucweb";
var bIsAndroid = sUserAgent.match(/android/i) == "android";
var bIsCE = sUserAgent.match(/windows ce/i) == "windows ce";
var bIsWM = sUserAgent.match(/windows mobile/i) == "windows mobile";



if (bIsIpad || bIsIphoneOs || bIsMidp || bIsUc7 || bIsUc || bIsAndroid || bIsCE || bIsWM) {
    // 移动端浏览器 
    document.write("phone");
    //移动端浏览器
    window.location.href = "https://m.jd.com/";
    // if (curURL.indexOf("jd.com") != -1) {
    //     window.location.href = "https://m.jd.com/";
    // }
} else {
    // PC端浏览器
    document.write("pc");
    //  if (curURL.indexOf("jd.com") != -1) {
        // window.location.href = "https://www.jd.com/";
    //   }
    }
}

browserRedirect()


</script>
```

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



## 移动端页面布局&懒加载

### 水平居中

##### 行内元素，如文本居中，div中的图片居中

```css
text-align: center;
```

#### 块级元素

```css
定宽：可以采取绝对定位的方式实现
.center {
    width: 960px;
    position: absolute;
    left: 50%;
    //左外边距的 负宽度一半的距离
    margin-left: -480px;
 }
 
 定宽，不定宽都可以：借助css3的变形属性Transform来完成
 .content {
 	 width:80%;
     position: absolute;
     left: 50%;
     //向左移动自身宽度的一半
     transform: translateX(-50%);
 }


```



#### 垂直居中

##### 单行文本的垂直居中

```css
元素的高度和行高相等时，文本呈现垂直居中   height== line-height   高等于行高
```

##### 多行文本的垂直居中

```css
不固定高度的垂直居中
	通过设置padding实现
	
固定高度的垂直居中
	使用display设置为table-cell，配合样式vertical-align设置为middle来实现
	table-cell：以表格单元格的形式来解析代码
```



###### **多行文本不固定高度垂直居中通过padding实现案例：**

```html
   <style>
        div{
            width: 400px;
            border: 2px solid #999;
            padding:20px 0px;
        }
    </style>
</head>

<body>
    <div>
        撑着油纸伞，独自彷徨在悠长，悠长又寂寥的雨巷，
        我希望逢着一个丁香一样的结着愁怨的姑娘。
        她是有丁香一样的颜色，丁香一样的芬芳，
    </div>
</body>
```



###### **多行文本固定高度的垂直居中**

```css
使用display设置为table-cell，配合样式vertical-align设置为middle来实现
table-cell：以表格单元格的形式来解析代码
```
```css
<style>
        div{
            width: 400px;
            height: 500px;
            border: 2px solid #999;
            padding:20px 0px;
            display: table-cell;
            vertical-align: middle;
        }
    </style>
</head>

<body>
    <div>
        撑着油纸伞，独自彷徨在悠长，悠长又寂寥的雨巷，
        我希望逢着一个丁香一样的结着愁怨的姑娘。
        她是有丁香一样的颜色，丁香一样的芬芳，
    </div>
</body>
```



##### 块级元素垂直居中

##### 固定宽高的垂直居中

 <img src="/image-20210413213201927.png" alt="image-20210413213201927" style="zoom:50%;border:1px solid #999" />

```css
.content {
        width: 100px;
        height: 100px;
        position: absolute;
        left: 50%;
        top: 50%;
        margin-left: -50px;
        margin-top: -50px;
    }

```



##### 不固定宽高的垂直居中

```css
.content {
	   width: 30%; 
       height: 30%;
       position: absolute;
        left: 50%;
        top: 50%;
        /* 左/上边缘向左/上移动自身宽/高度的一半 */
        transform: translate(-50%, -50%);
    }

```



##### 基于Flex实现垂直居中

移动端开发中最佳的解决方案

```css
.content {
         /*转为flex弹性盒布局*/
        display: flex;
        /*主轴上的对齐方式为居中*/
        justify-content: center;
        /*交叉轴上对齐方式为居中*/
        align-items: center;
    }

```



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>

    <style>
        div{
            width: 800px;
            height: 500px;
            display: flex;
            flex-direction: column;
            background-color: rgb(28, 124, 108);
            justify-content: center;
            align-items: center;

        }
        span{
            
            width: 200px;
            height: 100px;
            background-color: rgb(250, 176, 176);
            margin: 10px 0;
        }
    </style>
</head>
<body>
    <div>
        <span></span>
        <span></span>
        <span></span>
    </div>
</body>
</html>
```



### 面试题： 如果让元素水平垂直居中



>     行内元素  文本的水平垂直居中
>
>     
>
>     单行文本 text-align:center   固定高： line-height:高度
>
>                                 无高： padding:30px 0;
>
>     
>
>     多行文本  text-align:center  无高：padding:30px 0;
>
>                                 固定的高： display:table-cell
>         
>                                                    vertical-align: middle
>
>     
>
>     
>
>     块级元素：
>
>         固定高的时候：   margin:  (父高-当前元素的高) /2  auto;
>         
>         无固定高：           margin:auto
>         
>                                       padding: 30px 0;
>
>     
>
>        定位  和 位移
>
>             需要水平垂直居中的元素  ： position:absolute
>         
>                                                              top:50%;
>         
>                                                              left:50%;
>         
>                                                              transform:translate(-50%,-50%)
>         
>             父元素：                                 position:relative
>
>     
>
>     
>
>     ​    
>
>         弹性布局：
>         
>          需要水平垂直居中的父元素： display:flex;
>         
>                                                             justify-content: center;
>         
>                                                             align-items: center;
>



### 2、掌握移动端布局的方法

百分比流式布局
响应式布局
基于rem的布局
Flex布局

#### 图片懒加载原理：

#### 响应式布局案例

##### 阶段一：制作当当书香节导航部分

需求说明
屏幕宽度大于1200px时，按钮一行显示5个

屏幕宽度大于768px小于1199px时，按钮一行显示4个

屏幕宽度大于480px小于767px时，按钮一行显示4个

屏幕宽度小于479px时，按钮一行显示3个

按钮中的字体及间距大小自行调节

每行显示的图片，在媒体查询时，使用百分比进行布局



```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>当当书香节</title>
    <!-- 引入初始化css样式 -->
    <link rel="stylesheet" href="./css/reset.css">
    <link rel="stylesheet" href="./css/index.css">
</head>

<body>
    <div class="box">
        <!-- banner图 -->
        <img src="./images/jmsj_hw150316g.jpg" alt="" class="banner">

        <!-- 导航条 -->
        <div class="nav">
            <ul class="navaList">
                <li class="nav_li">
                    <a href="#">
                        <span>小说</span>
                        <span> > </span>
                    </a>
                </li>
                <li class="nav_li">
                    <a href="#">
                        <span>青春动漫</span>
                        <span> > </span>
                    </a>
                </li>
                <li class="nav_li">
                    <a href="#">
                        <span>经济管理</span>
                        <span> > </span>
                    </a>
                </li>
                <li class="nav_li">
                    <a href="#">
                        <span>历史文化</span>
                        <span> > </span>
                    </a>
                </li>
                <li class="nav_li">
                    <a href="#">
                        <span>人文社科</span>
                        <span> > </span>
                    </a>
                </li>
                <li class="nav_li">
                    <a href="#">
                        <span>育儿产儿</span>
                        <span> > </span>
                    </a>
                </li>
                <li class="nav_li">
                    <a href="#">
                        <span>旅游美食</span>
                        <span> > </span>
                    </a>
                </li>
                <li class="nav_li">
                    <a href="#">
                        <span>中小学教辅</span>
                        <span> > </span>
                    </a>
                </li>
                <li class="nav_li">
                    <a href="#">
                        <span>外语考试</span>
                        <span> > </span>
                    </a>
                </li>
                <li class="nav_li">
                    <a href="#">
                        <span>文学艺术</span>
                        <span> > </span>
                    </a>
                </li>
                <li class="nav_li">
                    <a href="#">
                        <span>成功励志</span>
                        <span> > </span>
                    </a>
                </li>

                <li class="nav_li">
                    <a href="#">
                        <span>传记</span>
                        <span> > </span>
                    </a>
                </li>
                <li class="nav_li">
                    <a href="#">
                        <span>哲学心理</span>
                        <span> > </span>
                    </a>
                </li>
                <li class="nav_li">
                    <a href="#">
                        <span>亲自家教</span>
                        <span> > </span>
                    </a>
                </li>
                <li class="nav_li">
                    <a href="#">
                        <span>保健养生</span>
                        <span> > </span>
                    </a>
                </li>

                <li class="nav_li">
                    <a href="#">
                        <span>科技</span>
                        <span> > </span>
                    </a>
                </li>

                <li class="nav_li">
                    <a href="#">
                        <span>童书</span>
                        <span> > </span>
                    </a>
                </li>
                <li class="nav_li">
                    <a href="#">
                        <span>教材</span>
                        <span> > </span>
                    </a>
                </li>
            </ul>
        </div>

        <!-- book box  书籍部分 -->
        <ul class="book_list">
            <li>
                <div class="book_cntent">
                    <img src="./images/xiaowangz.jpg" alt="">
                    <div class="book_name">狼图腾(修订版)（一部描绘、研究蒙古草原狼的“旷世奇书”）</div>
                    <div class="book_msg">
                        <div class="book_pric">
                            <p class="pric_n">￥19.9</p>
                            <p class="pric_o">39.8</p>
                        </div>
                        <div class="buy_btn">点击购买</div>
                    </div>
                </div>
            </li>

            <li>
                <div class="book_cntent">
                    <img src="./images/langtut.jpg" alt="">
                    <div class="book_name">狼图腾(修订版)（一部描绘、研究蒙古草原狼的“旷世奇书”）</div>
                    <div class="book_msg">
                        <div class="book_pric">
                            <p class="pric_n">￥19.9</p>
                            <p class="pric_o">39.8</p>
                        </div>
                        <div class="buy_btn">点击购买</div>
                    </div>
                </div>
            </li>
            <li>
                <div class="book_cntent">
                    <img src="./images/yelusheleng.jpg" alt="">
                    <div class="book_name">狼图腾(修订版)（一部描绘、研究蒙古草原狼的“旷世奇书”）</div>
                    <div class="book_msg">
                        <div class="book_pric">
                            <p class="pric_n">￥19.9</p>
                            <p class="pric_o">39.8</p>
                        </div>
                        <div class="buy_btn">点击购买</div>
                    </div>
                </div>
            </li>
            <li>
                <div class="book_cntent">
                    <img src="./images/pinang.jpg" alt="">
                    <div class="book_name">狼图腾(修订版)（一部描绘、研究蒙古草原狼的“旷世奇书”）</div>
                    <div class="book_msg">
                        <div class="book_pric">
                            <p class="pric_n">￥19.9</p>
                            <p class="pric_o">39.8</p>
                        </div>
                        <div class="buy_btn">点击购买</div>
                    </div>
                </div>
            </li>
            <li>
                <div class="book_cntent">
                    <img src="./images/dashuju.jpg" alt="">
                    <div class="book_name">狼图腾(修订版)（一部描绘、研究蒙古草原狼的“旷世奇书”）</div>
                    <div class="book_msg">
                        <div class="book_pric">
                            <p class="pric_n">￥19.9</p>
                            <p class="pric_o">39.8</p>
                        </div>
                        <div class="buy_btn">点击购买</div>
                    </div>
                </div>
            </li>
        </ul>
    </div>



</body>

</html>
```

index.css

```css
.box{
    background-color: rgb(1,25,87);
}

.banner{
    width: 100%;
    display: block;
}
.navaList{
    overflow: hidden;
    padding: 0 5px;
}
.nav_li{
    width: 25%;
    float: left;
    margin-bottom: 5px;
}

.nav_li>a{
    display: block;
    font-size: 17px;
    margin: 4px;
    padding: 5px 0;
    color: white;
    background-color: rgb(103,69,181);
    border-radius: 7px;
    text-align: center;
}

.nav_li>a{
    box-shadow: 0px 3px 02px rgb(127, 79, 189);
}
.nav_li>a>span:nth-of-type(2){
    display: inline-block;
    width: 20px;
    height: 20px;
    background-color: rgb(1,25,87);
    border-radius: 7px;
    float: right;
    margin-right: 10px;
    line-height: 20px;
    text-align: center;
}


.book_list{
    overflow: hidden;
    margin-top: 30px;
    padding: 0 5px;
}

.book_list li{
    width: 50%;
    float: left;
   
    
    
}

.book_cntent{
    background-color: #fff;
    margin: 5px;
    border-radius: 7px;
    overflow: hidden;
    padding: 5px;
}
.book_cntent>img{
    width: 100%;
}

.book_name{
    margin-top: 20px;
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
    font-size: 20px;
}
.book_msg{
    margin-top: 10px;
}
.book_pric{
    float: left;
}
.pric_n{
    color: red;
    font-size: 24px;
    font-weight: bold;
}
.pric_o{
    color: rgb(34, 31, 31);
    font-size: 20px;
    text-decoration: line-through;
}

.buy_btn{
    float:right;
    width: 49px;
    height: 49px;
    font-size: 18px;
    font-weight: 900;
    background-color: rgb(241, 59, 59);
    color: white;
    text-align: center;
    border-radius: 5px;
}
```

##### 阶段二

需求说明
这一块需要使用百分比布局产品列表，随着屏幕宽度的变化，产品会自动适应屏幕的变化做出相应的调整，这一块并没有用到媒体查询进行控制

懒加载：

所谓图片懒加载，就是想让页面在展示图片的时候，不一下子全部开始加载，而是等到屏幕快滑到该图片的时候，再开始加载，这样做的好处，提高网页加载效率，节省用户流量

那么什么时候开始加载呢？

已加载高度 + 屏幕高度 >=  未加载区域-20

说明下面未加载区域已经窜到屏幕上了，此时不加载，更待何时呢？？？？



自定义属性

```html
 <img src="./images/bg_pic.png" data-realSrc="./images/xiaowangz.jpg" class="images">
```



```javascript
// 1.定义一个图片懒加载的函数
function lazyImg() {

    // 1.获取页面已经滚动的高度   获取当前设备的高度
    var scroolTop = document.documentElement.scrollTop || document.body.scrollTop;
    var clientHeight = document.documentElement.clientHeight || document.body.clientHeight;
    // 2.获取到所有的图片资源
    var images = document.getElementsByClassName('images');
    // 3.遍历图片  通过当前图片的自定属性 找到真是的图片路径
    for (var img of images) {

        // 4.找到当前图片距离页面最上面的距离  < = 获取页面已经滚动的高度 +  获取当前设备的高度
        // 5.替换图片资源 把真是的图片路径 替换当前图片的src

        if (((img.offsetTop - 100) <= (scroolTop + clientHeight)) && (img.getAttribute('data-realsrc'))) {
            //真实路径
            var realSrc = img.getAttribute('data-realsrc');
            console.log(realSrc);
            img.src = realSrc;
            //不让已经加载的图片 再次进入当前判断中
            img.removeAttribute("data-realsrc");
        }
    }

}
```



## 移动端事件

我们之前学习的电脑端事件,点击,双击,鼠标事件等,在手机端是没有的,因为我们很少见到有人在手机上用一个鼠标进行操作,取而代之的是触摸事件

> 点击事件
>
> 双击事件
>
> 滑动事件
>
> > 上滑	下滑	左滑	右滑
>
> 长按事件
>
> 摇一摇	重力感应等

### 在移动端事件上使用click事件

300ms延时

```js
var span = document.getElementsByTagName('span')[0];
span.onclick = function () {
    alert('点击了span元素');
};

```

#### 	300ms产生的原因

1、移动浏览器上支持的 双击缩放操作，以及 IOS系统 上的双击滚动操作，是导致300ms的点击延迟主要原因。
2、手指在屏幕上快速点击两次，移动端浏览器会将网页缩放至原始比例。 那么这和 300 毫秒延迟有什么联系呢？ 假定这么一个场景。用户在 浏览器里边点击了一个链接。由于用户可以进行双击缩放或者双击滚动的操作，当用户点击 一次屏幕之后，浏览器并不能立刻判断用户是确实要打开这个链接，还是想要进行双击操作。因此，浏览器就等待 300 毫秒，以判断用户是否再次点击了屏幕 ，如果 300ms之内再次点击 就会认为是 双击操作，如果300ms 内 没有再次去点击，就认为是单击。
3、在移动WEB兴起的初期，用户对300ms的延迟感觉不明显。但是，随着用户对交互体验的要求越来越高，现今，移动端300ms的点击延迟逐渐变得明显，那我们该如何解决这个问题呢？
    两种方式，

第一种 ：使用移动端专门提供的事件  

第二种，可以使用插件解决 300ms延时问题 后面课程会讲解到这两种方式；



## 2、Touch事件模型

| touchstart  | 手指刚接触屏幕时触发                                         |
| ----------- | ------------------------------------------------------------ |
| touchmove   | 手指在屏幕上移动时触发                                       |
| touchend    | 手指从屏幕上移开时触发                                       |
| touchcancel | 当一些更高级别的事件发生的时候（如电话接入或者弹出信息）会取消当前的touch操作，即触发touchcancel。一般会在touchcancel时暂停游戏、存档、暂停视频音乐等操作 |



注意，在绑定事件的时候，要加上关键字on

如： 

```js
div.ontouchmove = function(){

}
```



```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>移动端事件</title>

    <style>
        div {
            width: 300px;
            height: 500px;
            background-color: skyblue;
        }
    </style>

</head>

<body>
    <div></div>

</body>

<script>
    var div_ = document.getElementsByTagName('div')[0];

    // 手指触摸的时候背景颜色变红色
    div_.ontouchstart = function () {
        div_.style.backgroundColor = 'red';
    }

    // 手指在屏幕移动的时候
    div_.ontouchmove = function () {
        div_.style.backgroundColor = 'yellow';
    }

    // 手指离开屏幕的时候
    div_.ontouchend = function () {
        div_.style.backgroundColor = 'green';
    }

    // 触发高级事件的时候
    div_.ontouchcancel = function () {
        div_.style.backgroundColor = 'pink';
    }



</script>

</html>
```



### 触摸属性（event）



touches：表示当前跟踪的触摸操作的touch对象的数组（当前位于屏幕上的所有手指触摸点的一个列表）

- 当一个手指在触屏上时，
      event.touches.length=1
- 当两个手指在触屏上时，
      event.touches.length=2，以此类推

changedTouches：触发事件时改变的触摸点的集合

									哪根手指点击的事件，保存哪根手指触摸点的数据

targetTouches：绑定事件的那个结点上的触摸点的集合列表（谁点了点击事件 保存谁）

**总结：**

- touches: 当前屏幕上所有触摸点的集合列表（保存屏幕上所有的触点）
- targetTouches:  绑定事件的那个结点上的触摸点的集合列表（谁点了点击事件 保存谁）
- changedTouches:  触发事件时改变的触摸点的集合（）

举例来说，比如div1, div2只有div2绑定了touchstart事件，第一次放下一个手指在div2上，触发了touchstart事件，这个时候，三个集合的内容是一样的，都包含这个手指的touch，然后，再放下两个手指一个在div1上，一个在div2上，这个时候又会触发事件，但changedTouches里面只包含第二个第三个手指的信息，因为第一个没有发生变化，而targetTouches包含的是在第一个手指和第三个在div2上的手指集合，touches包含屏幕上所有手指的信息，也就是三个手指



#### 触摸事件坐标（event事件对象中）

查看触摸event对象：

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>

    <style>
        div{
            width: 100%;
            height: 500px;
            background-color: skyblue;
        }
    </style>
</head>

<body>
    <div></div>

</body>

<script>

    var div = document.getElementsByTagName('div')[0];
    div.ontouchstart = function(e){
        e = e||window.event;
        console.log(e);
    }

</script>

</html>
```



| clientX    | 触摸目标在视口中的x坐标  视觉视口    |
| ---------- | ------------------------------------ |
| clientY    | 触摸目标在视口中的y坐标   视觉视口   |
| identifier | 标识触摸的唯一ID                     |
| pageX      | 触摸目标在页面中的x坐标     布局视口 |
| pageY      | 触摸目标在页面中的y坐标     布局视口 |
| screenX    | 触摸目标在屏幕中的x坐标              |
| screenY    | 触摸目标在屏幕中的y坐标              |
| target     | 触摸的DOM节点目标，返回触摸的元素    |

注意：

clientX/Y和pageX/Y的区别：

clientX/Y：相对于视觉视口的左上角

pageX/Y：相对布局视口的左上角。布局视口 是可以滚动的



```js
<script>

    var div = document.getElementsByTagName("div")[0];
  div.ontouchstart = function (e) {
    e = e || window.event;
    console.log(e);
    str = "";
    for (var i = 0; i < e.changedTouches.length; i++) {
      str += "第" + (i + 1) + "根手指的id是：" + e.changedTouches[i].identifier;
      str +=
        "<br>第" +
        (i + 1) +
        "根手指的screenx坐标：" +
        e.changedTouches[i].screenX;
      str +=
        "<br>第" +
        (i + 1) +
        "根手指的screenY坐标：" +
        e.changedTouches[i].screenY;
      str +=
        "<br>第" + (i + 1) + "根手指的pagex坐标：" + e.changedTouches[i].pageX;
      str +=
        "<br>第" + (i + 1) + "根手指的pageY坐标：" + e.changedTouches[i].pageY;
      div.innerHTML = str;
    }
  };

</script>
```



## 3、移动端事件封装



- ##### 实操-单击事件

  

#### 封装单击事件：



为什么要封装单击事件？

比如：

我们现在给同一个元素绑定了点击和移动两个事件

因为移动端的屏幕非常小，点击完以后，手在抬起来的时候，很容易造成一点的移动偏差

此时就很容易触发移动事件

我们需要进行一个判断，比如手在抬起来的时候，位置偏差范围多少的情况下视为单击离开

偏差多少的范围外，视为移动事件

```html
<!DOCTYPE html>
<html>

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>封装单击事件</title>
    <style>
        *{
            margin: 0;
            padding: 0;
        }
        .div1,.div2{
            height: 200px;
            background-color: skyblue;
            margin-bottom: 30px;
        }
    </style>
    
</head>

<body>
    <div class="div1"></div>
    <div class="div2"></div>

</body>

<script>
    var div1 = document.getElementsByClassName('div1')[0];
    var div2 = document.getElementsByClassName('div2')[0];

    // 把点击事件封装成对象的方法
    var touchEvent = {
        
        tab:function(el){
            var end_x,end_y,start_x,start_y;
            el.ontouchstart = function(e){
                e =e||window.event;
                // 获取按下动作的x值和y值
                start_x = e.changedTouches[0].clientX;
                start_y = e.changedTouches[0].clientY;
            }

            el.ontouchend = function(e){
                e = e||window.event;
                //获取抬起动作的x值和y值
                end_x = e.changedTouches[0].clientX;
                end_y = e.changedTouches[0].clientY;

                if(Math.abs(end_x-start_x)<10 && Math.abs(end_y-start_y)<10){
                    alert('您调用了点击事件')
                }else{
                    alert('您调用了移动事件');
                }
            }
        }
    }

    touchEvent.tab(div1);
    touchEvent.tab(div2);
</script>

</html>
```



## 4、移动端事件库



#### Touch.js 

`Touch.js`是移动设备上的手势识别与事件库, 由百度云Clouda团队维护，也是在百度内部广泛使用的开发工具.(已停更)

`Touch.js`手势库专为移动设备设计,是Web移动端touch点击事件不错的解决方案

https://github.com/Clouda-team/touchjs

##### 支持移动端事件（部分）

| **属性**   | **设备类型** |
| ---------- | ------------ |
| tap        | 单击屏幕     |
| doubletap  | 双击屏幕     |
| swipe      | 滑动         |
| swipeleft  | 向左滑动     |
| swiperight | 向右滑动     |
| swipeup    | 向上滑动     |
| swipedown  | 向下滑动     |
| hold       | 长按屏幕     |
| dragstart  | 拖动开始     |
| drag       | 拖动         |
| pinchstart | 缩放手势起点 |
| pinchin    | 收缩         |
| pinchout   | 放大         |



用法：

```js
//引入touchjs
<script src="js/touch-0.2.14.min.js"></script>
/*
	touch.on(1,2,3)

    三个参数：
	1、DOM元素
	2、移动端事件
	3、处理函数

 */
touch.on(oBox, 'tap', function(ev) {
     this.style.background = "red";
     this.style.color = '#fff'; 
});
```

示例：

```javascript
<script>
    var div = document.getElementsByTagName('div')[0];
    touch.on(div,'tap',function(){
        this.style.backgroundColor = 'red';
    });
    touch.on(div,'doubletap',function(){
        this.style.backgroundColor = 'green';
    });

    // 长按
    touch.on(div,'hold',function(){
        alert('长按');
        this.style.backgroundColor = 'yellow';

    })
    // 拖动
    touch.on(div,'drag',function(){
        
        this.style.backgroundColor = 'pink';

    })



</script>
```



#### hammer.js 

一款开源的移动端脚本框架，他能完美的实现在移端开发的大多数事件，如点击、滑动、拖动、多点触控等事件

http://hammerjs.github.io/getting-started/

用法：

```js
<script src="js/hammer.min.js"></script>
//创建一个新的hammer对象并且在初始化时指定要处理的dom元素
var hammertime = new Hammer(document.getElementById("test"));

//添加事件
// tap、swipe、rotate、press、pinch、pan等事件，这里就给大家演示tap，剩余的大家可以课下自行学习
hammertime.on("tap", function(e) {
    document.getElementById("result").innerHTML += "点击触发了，长按无效<br />";
    //控制台输出,可以自行查看相关的参数
    console.log(e);
});

```



### 点透现象

```js
/* 点击第一层第一个,令其消失*/
b.addEventListener('touchstart', function(e) {
    level10.style.display = 'none';
});
a.onclick = function() {
    console.log('看下会不会被点击到');
}
点透发生的条件
A 和 B不是后代继承关系，而是兄弟关系
b发生touch， b touch后立即消失， a事件绑定click
b显示在a浮层之上

```

```html
  <style>
        div{
            width: 100%;
            height: 200px;
            
        }

        .a{
            position: absolute;
            background-color: rgb(241, 71, 71);
        }
        .b{
            position: absolute;
            background-color: rgb(70, 145, 41);
        }
    </style>
  
</head>

<body>
    <div class="a"></div>
    <div class="b"></div>

</body>

<script>
    var a = document.getElementsByClassName('a')[0];
    var b = document.getElementsByClassName('b')[0];

    b.addEventListener('touchstart',function(){
        b.style.display = 'none';
    });

    a.onclick = function(){
        alert('a显示出来了，红色的');
    }
</script>
```



#### 解决点透问题

将click换成移动端事件

```javascript
  // a.onclick = function(){
 //     alert('a显示出来了，红色的');
 // }
a.ontouchstart = function(){
        alert('a显示出来了，红色的');
    }
```

不建议使用：

e.preventDefault()

```js
// 阻止pc的事件
document.addEventListener('touchend', function(e){
	// 可以阻止本次点击系统触发的click事件 
    e.preventDefault();
}, false);

```

# Eacharts

## 数据可视化

- 数据可视化的主要目的:借助于图形化手段,清晰有效地传达与沟通的信息
- 数据可视化可以把数据从冰冷的数字转化成图形,揭示蕴含在数据中的规律和道理

#### 阶段目标：项目介绍

	应对现在数据可视化的趋势，越来越多企业需要在很多场景(营销数据，生产数据，用户数据)下使用，可视化图表来展示体现数据，让数据更加直观，数据特点更加突出。我们引入 '立可得' 数据可视化项目。
	
	该项目除了使用了基础的DIV+CSS布局，还引入了一些C3技术，还引入了各类图表的绘制，以及高级的地图数据可视化案例。主要功能有：饼状图、柱状图、线形图、地图 ...

#### 使用技术

完成该项目需要具备以下知识：

- div + css 布局
- flex 布局
- css3动画
- css3渐变
- css3边框图片
- 原生js  使用
- rem适配
- **echarts基础**

粗略代码统计：

- css  580行
- html  450行
- js 400行 (有效)



### eacharts-介绍

> ECharts，一个使用 JavaScript 实现的开源可视化库，可以流畅的运行在 PC 和移动设备上，兼容当前绝大部分浏览器（IE8/9/10/11，Chrome，Firefox，Safari等），底层依赖矢量图形库 [ZRender](https://github.com/ecomfe/zrender)，提供直观，交互丰富，可高度个性化定制的数据可视化图表。

大白话：

- 是一个JS插件
- 性能好可流畅运行PC与移动设备
- 兼容主流浏览器
- 提供很多常用图表，且可**定制**。
  - [折线图](https://echarts.apache.org/examples/zh/index.html#chart-type-line)、[柱状图](https://echarts.apache.org/examples/zh/index.html#chart-type-bar)、[散点图](https://www.echartsjs.com/zh/option.html#series-scatter)、[饼图](https://echarts.apache.org/examples/zh/index.html#chart-type-scatter)、[K线图](https://echarts.apache.org/examples/zh/index.html#chart-type-candlestick)

       <a herf="https://echarts.apache.org/zh/index.html">ECharts官网:</a>

### 03、Echarts-体验

```js
1、引入eacharts库,引入依赖
2、需要有一个可以展示eacharts图标的容器	div......
3、初始化eacharts
	var mychart=eacharts.init('装图标的容器')
4、开始写eacharts图标的配置项
	var option={...};
5、把配置项 设置给eacharts对象
```

官方教程：[快速上手](https://echarts.apache.org/handbook/zh/get-started/)

下载步骤：

- 下载echarts  ：

  在 https://www.jsdelivr.com/package/npm/echarts 选择 `dist/echarts.js`

  点进去，c t r l+a全选复制，

  把复制的内容新建 `echarts.js` 文件，进行存储。

  

  下载方法2：

  https://github.com/apache/echarts 点击，

在dist 下面，找到echarts.js

- 引入创建好的echarts .js文件
- 准备一个具备大小的DOM容器

```html
<div id="main" style="width: 600px;height:400px;"></div>
```

- ###### 初始化echarts

```js
var myChart = echarts.init(document.getElementById('main'));
```

- 指定配置项和数据(option)

```js
var option = {
    xAxis: {
        type: 'category',
        data: ['Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat', 'Sun']
    },
    yAxis: {
        type: 'value'
    },
    series: [{
      w  data: [820, 932, 901, 934, 1290, 1330, 1320],
        type: 'line'
    }]
};
```

- 将配置项设置给echarts实例对象

```js
myChart.setOption(option);
```

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>ECharts</title>
    <!-- 1、引入刚刚下载的 ECharts 文件 -->
    <script src="echarts.js"></script>
  </head>
  <body>
    <!-- 2、为 ECharts 准备一个定义了宽高的 DOM -->
    <div id="main" style="width: 600px;height:400px;"></div>
    <script type="text/javascript">
      // 3、基于准备好的dom，初始化echarts实例
      var myChart = echarts.init(document.getElementById('main'));

      // 4、指定图表的配置项和数据
      var option = {
        title: {
          text: 'ECharts 入门示例'
        },
        tooltip: {},
        legend: {
          data: ['销量']
        },
        xAxis: {
          data: ['衬衫', '羊毛衫', '雪纺衫', '裤子', '高跟鞋', '袜子']
        },
        yAxis: {},
        series: [
          {
            name: '销量',
            type: 'bar',
            data: [5, 20, 36, 10, 10, 20]
          }
        ]
      };

      // 5、使用刚指定的配置项和数据显示图表。
      myChart.setOption(option);
    </script>
  </body>
</html>
```

#### 自定义图标类型

即可自定义不同的图标样式

### 04-Echarts-基础配置

可查阅文档——API——配置项，查看具体每一项配置项的详解

> 需要了解的主要配置：`series` `xAxis` `yAxis` `grid` `tooltip` `title` `legend` `color` `toolbox` 



- series
  - 系列列表。每个系列通过 `type` 决定自己的图表类型
  - 大白话：图标数据，指定什么类型的图标，可以多个图表重叠。

- xAxis：直角坐标系 grid 中的 x 轴

  -  boundaryGap: 坐标轴两边留白策略 true，这时候刻度只是作为分隔线，标签和数据点都会在两个刻度之间的带(band)中间。

- yAxis：直角坐标系 grid 中的 y 轴

- grid：直角坐标系内绘图网格。 

- title：标题组件

- tooltip：提示框组件，即鼠标经过图标时提示的内容

- toolbox:工具栏，内置有[导出图片](https://echarts.apache.org/zh/option.html#toolbox.feature.saveAsImage)，[数据视图](https://echarts.apache.org/zh/option.html#toolbox.feature.dataView)，[动态类型切换](https://echarts.apache.org/zh/option.html#toolbox.feature.magicType)，[数据区域缩放](https://echarts.apache.org/zh/option.html#toolbox.feature.dataZoom)，[重置](https://echarts.apache.org/zh/option.html#toolbox.feature.reset)五个工具。

- legend：图例组件，即图例，什么颜色代表什么内容

- color：调色盘颜色列表，数组类型

  数据堆叠，同个类目轴上系列配置相同的`stack`值后 后一个系列的值会在前一个系列的值上相加。

演示代码：

```js
var option = {
            color: ['pink', 'blue', 'green', 'skyblue', 'red'],
            title: {
                text: '我的折线图'
            },
            tooltip: {
              // 触发提示： 经过坐标轴的时候
                trigger: 'axis'
            },
  					// 图例
            legend: {
                data: ['直播营销', '联盟广告', '视频广告', '直接访问']
            },
  					//坐标系网格
            grid: {
              	//当前网格距离整体容器左边3%
                left: '3%',
                right: '3%',
                bottom: '3%',
                // 当刻度标签溢出的时候，grid 区域是否包含坐标轴的刻度标签。如果为true，则显示刻度标签
                // 如果left right等设置为 0% 刻度标签就溢出了，此时决定是否显示刻度标签
                containLabel: true
            },
  					//工具栏 如刷新图标 导入图表为图片等等。。
            toolbox: {
                feature: {
                    saveAsImage: {}
                }
            },
            xAxis: {
              	// category 种类的意思 如果设置为该值 表示x坐标系的划分，根据xAxis中的data数据划分
                type: 'category',
                // 坐标轴两边留白策略 true，这时候刻度只是作为分隔线，标签和数据点都会在两个刻度之间的带(band)中间。
                boundaryGap: false,
                data: ['星期一', '星期二', '周三', '周四', '周五', '周六', '周日']
            },
            yAxis: {
                type: 'value'
            },
  					//图表系列
            series: [
                {
                  	//name 系列名称  用于tooltip的显示，图例示选等
                    name: '直播营销',
                    // line 图表类型是线形图  type 选择图表的类型  bar 柱状图  pie 饼图
                    type: 'line',
                  	// y轴的数据 和x轴一一对应
                  	// 如120 对应星期一 132 对应星期二
                    data: [120, 132, 101, 134, 90, 230, 210],
                  	// stack 数据堆叠 后面值一样的数据 数据堆叠
                  	//       第二个数据显示的值 = 第一个的值 + 第二个的值
                    stack:'总量'
                },
                {
                    name: '联盟广告',
                    type: 'line',
                    data: [220, 182, 191, 234, 290, 330, 310],
                    stack:'总量',
                },
                {
                    name: '视频广告',
                    type: 'line',
										stack:'总量'
                    data: [150, 232, 201, 154, 190, 330, 410]
                },
                {
                    name: '直接访问',
                    type: 'line',
										stack:'总量',
                    data: [320, 332, 301, 334, 390, 330, 320]
                }
            ]
        };
```

#### 项目准备知识

1、获取对应属性，字符串

```js
 var obj = {
    name: "张三",
  };

  var val = obj.name;

  var val = "name";
  console.log(obj.name);
  console.log(obj[val]);
```

2、如何自动切换

```js
//点击切换
  //   var lis = document.getElementsByTagName("li");
  //   for (var i = 0; i < lis.length; i++) {
  //     lis[i].setAttribute("index", i);

  //     lis[i].onclick = function () {
  //       var index = this.getAttribute("index");
  //       console.log(index);

  //       for (var j = 0; j < lis.length; j++) {
  //         lis[j].className = "";
  //         lis[index].className = "active";
  //       }
  //     };
  //   }

  var lis = document.getElementsByTagName("li");
  for (var i = 0; i < lis.length; i++) {
    lis[i].setAttribute("index", i);

    lis[i].onclick = function () {
      var index = this.getAttribute("index");
      console.log(index);

      for (var j = 0; j < lis.length; j++) {
        lis[j].className = "";
        lis[index].className = "active";
      }
    };
  }

  var start = 0;
  setInterval(function () {
    start++;
    if (start >= lis.length) {
      start = 0;
    }

    lis[start].click();
  }, 1000);
```

### 06-REM适配

- 设计稿是1920px  

- PC端适配： 宽度在 1024~1920之间页面元素宽高自适应

  1. setRem.js 把屏幕分为 18等份（我的屏幕宽1440）

  2. cssrem 插件的基准值是  80px 

     插件-配置按钮---配置扩展设置--Root Font Size 里面 设置。 

     但是别忘记重启vscode软件保证生效

  3. 要把屏幕宽度约束在1024~1920之间有适配，实现代码：

```js
//setRem.js
function setRem() {
    var clientWidht = document.clientWidht || document.body.clientWidth;

    clientWidht = clientWidht > 1920 ? 1920 : clientWidht;
    clientWidht = clientWidht < 1024 ? 1024 : clientWidht;

    var rem = clientWidht / 18;
    var html = document.getElementsByTagName('html')[0];
    html.style.fontSize = rem + 'px';

}

window.onload = setRem;
window.onresize = setRem;
```

html结构：

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="UTF-8" />
    <meta
      name="viewport"
      content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=0"
    />
    <meta http-equiv="X-UA-Compatible" content="ie=edge" />
    <title>Document</title>
    <link rel="stylesheet" href="./css/index.css" />
  </head>

  <body>
    <div class="viewport">
      <div class="column">
        <!--概览-->
        <div></div>
        <!--监控-->
        <div></div>
        <!--点位-->
        <div></div>
      </div>
      <div class="column">
        <!--地图-->
        <div></div>
        <!--用户-->
        <div></div>
      </div>
      <div class="column">
        <!--订单-->
        <div></div>
        <!--销售-->
        <div></div>
        <div>
          <!--渠道-->
          <div></div>
          <!--季度-->
          <div></div>
        </div>
        <!--排行-->
        <div></div>
      </div>
    </div>
  </body>
</html>
<script src="./js/setRem.js"></script>

```

- 效果图： 1920px *  1078px 
- body 设置背景图 ，行高1.15
- viewport 主体容器，限制最小宽度1024px，与最大宽度1920px，最小高度780px。
  - 需要居中显示
  - 使用logo.png做为背景图，在容器内显示
  - 内间距 70px 20px 0
- column 列容器，分三列，占比 3：4：3
  - 中间容器外间距  30px  15px 0

css样式：

```css
* {
  margin: 0;
  padding: 0;
}

body {
  background: url(../images/bg.jpg) no-repeat;
  background-size: cover;

}

h4,
h3,
ul {
  margin: 0;
  padding: 0;
  font-weight: normal;
}
ul {
  list-style: none;
}
a {
  text-decoration: none;
}

/* 主体容器 */
.viewport {
  min-width: 1024px;
  max-width: 1920px;
  min-height: 10rem;
  margin: 0 auto;
  padding: 1rem 0.25rem 0;
  box-sizing: border-box;
  background: url(../images/logo.png) no-repeat;
  background-size: contain;
  display: flex;
}

.viewport > .column {
  flex: 3;
  background-color: rgb(248, 187, 187);
}

/* 中间板板占四份  3:4:3的比例分配 */

.viewport > .column:nth-of-type(2) {
  flex: 4;
  background-color: skyblue;
  margin: 0.375rem 0.1875rem 0;
}

```