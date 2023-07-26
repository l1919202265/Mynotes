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

##### 微博评论减字功能

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

##### 制作表单用户名输入

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

## JavaScript事件二

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

##### event对象放在事件处理函数中

```javascript
document.onclick=function(e){
    oEvent(oEvent.clientX+','+oEvent.clientY);
}
```

##### 查看event对象：

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

键盘按键事件

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

#### 右键事件

```javascript
document.oncontextmenu=function(){
	alert('右键');
}
```

#### 阻止默认事件

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

#### 自定义菜单

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

#### 防抖：

> ​     连着点了好多次，我们想要点击停止后间隔一定的时间 执行一次
>
> ​     一些频繁触发的事件，我们不想让它频繁执行，比如 keyup scroll resize mousemove
>
> ​     不想让它如此频繁，执行停止后间隔一定的时间执行 就用防抖
>
> ​     应用场景： 比如搜索框联想
>
> 总结：防止点击多次后重复叠加，每次点击都清空，只执行最后一次

#### 节流


> ​    不论执行的频率有多高 ，我们总是让间隔一定的时间执行一次
>
> ​     一些频繁触发的事件，我们想让它频繁执行，但不想那么的频繁，节制一点
>
> ​    比如 keyup scroll resize mousemove
>
> ​    不想让它如此频繁，执行停止后间隔一定的时间执行 就用防抖
>
> ​    应用场景： 比如拖拽内容
>
> 总结：防止点击频率过高，限制执行频率，每间隔一段后执行一次


#### 使用lodash库完成防抖节流

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