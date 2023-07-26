# BOM

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

