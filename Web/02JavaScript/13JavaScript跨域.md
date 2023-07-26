## 跨域

CORS是一个W3C标准，全称是：跨域资源共享。它允许浏览器向跨源服务器，发出XMLHttpRequest，从而克服Ajax只能同源使用的限制

跨域，指的是浏览器不能执行其他网站的脚本，简单的理解就是因为JavaScript同源策略的限制，a.com域名下的js无法操作b.com或是c.a.com域名下的对象

例子：比如淘宝网不能请求京东的数据

#### 产生跨域的原因：

由于浏览器的同源策略造成的

同源策略，它是由Netscape提出的一个著名的安全策略，现在所有支持JavaScript的浏览器都会使用这个策略。

同源策略：

生活中，社会能够安定的运行，有一个前提，大家都默认遵守一个约定：每个人都只能自由的出入自己的家，拿取自己家的东西。而如果大家都不遵循这种协定，你可以随便拿别人家的东西，别人也可以随便的出入你的家，这样社会就乱套了。此处大家都遵守的各用各家的东西，久啊叫做同源策略。

同源策略大白话：

> 生活中，社会能够安定的运行，有一个前提，大家都默认遵守一个协定：每个人只能自由的出入自己的家，拿取自己家的东西。而如果大家都不遵循这种协定，你可以随便去拿别人家的东西，别人也可以随便的出入你的家，这样社会就乱套了。此处大家都遵循的各用各家的东西，就叫做同源策略

##### 所谓同源是指：

<font color=red>同域名：

同协议：http，https

同端口：
</font>

#### 跨域的限制

随着互联网的发展，同源策略越来越严格。目前，如果非同源，共有三种行为受到限制。

1、无法读取非同源网页的Cookie、LocalStorage和IndexedDB。【缓存数据】

2、无法接触非同源网页的DOM。

3、无法向非同源地址发送AJax请求（可以发送，但浏览器会拒绝响应）

#### 后台加入响应头解决跨域：

```java
response.setHeader("Access-Control-Allow-Origin", "*");响应头。
```
“*”表示所有的域都可以接受
CORS 需要浏览器和服务器同时支持。目前，所有浏览器都支持该功能。


#### AJax跨域请求【代理服务器】解决跨域

代理服务器

由于在工作中需要使用AJax请求其他域名下的资源，但是会出现拒绝访问的情况，这是因为基于安全的考虑，AJax只能访问本地同域的资源，而不能跨域访问

可以让服务器去别的网站获取内容然后返回页面

大白话：我们要租房子，房源被中介垄断了，我们无法直接找到房东。我们先找到中介，中介和房东谈具体事宜，谈好以后把每个月多少钱的信息告诉我们

#### 使用jsonp可以完成跨域

jsonp	借助的是	src可以跨域，src本身就是访问外部资源

jsonp只能完成get请求，不能使用post方法

因为get请求方式把请求参数放在了URL地址中，后台解析jsonp是通过URL的callback参数进行判断的，所以支持get请求



#### jsonp实现的思路：

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


