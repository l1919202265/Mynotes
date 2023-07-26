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

#### less语法:

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



#### 混合(Mixins)

混合(Mixin)是一种将一组属性从一个规则包含(或混入)到另一个规则集的方法

#### 混合变量

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

#### 带参混合

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

## 匹配模式

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

## sass

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

##### 相同点:

1:他们都是css预处理器,优化了普通的css,增加了变量,混合模式,匹配模式等方法,使的css的书写更为简单

##### 不同点:

1:文件了类型的不同,sass的文件类型是scss,lessd的文件类型是.less

2:声明变量的方式不同,less声明变量使用@变量名,sass声明变量使用$变量名

3:less编译为css文件后,会生成一个和less文件同名的css文件

sass编译为css文件后,会生成和sass文件同名的css文件,同时还会生成一个压缩文件,即和sass同名.min.css

