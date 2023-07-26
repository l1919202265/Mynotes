# DOM

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

## DOM操作HTML

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

## DOM节点之间的关系

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



## Element属性

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

## 节点信息

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

## 操作节点属性

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

## 排他法



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

# DOM2

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



## 删除和替换节点

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



#### 元素属性的应用：

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