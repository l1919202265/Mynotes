# Ajax

ajax是一种在无需重新加载整个网页的情况下，能够更新部分网页的技术

前后台建立连接，把前台请求发送给后台。把后台的相应拿个前台

简单说：大白话：就是没用Ajax网页，你点一个按钮就要刷新一下页面，尽管新页面上只有一行字和当前页面不一样，但你还是要无聊的等待页面刷新

用了Ajax之后，你点击，然后页面上的一行字就变化了，页面本身不用刷。

Ajax只是一种技术，不是某种具体的东西

#### 创建Ajax步骤

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

#### get和post请求的区别：

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

#### 请求状态码 readyState：

从 0 到 4 发生变化
0: 请求未初始化（还没有调用到open方法）
1: 服务器连接已建立（已调用send方法，正在发生请求）
2: 请求已接收（send方法完成，已接收到全部请求内容）
3: 请求处理中（解析响应内容）
4: 请求已完成，且响应已就绪

#### 响应状态码 status：

200："OK"

404：未找到页面	路径错误

403：请求成功 服务器拒绝响应 没有权限

5**：服务器内部错误，（检查拼接的参数对不对）

500： 服务器内部错误

### JSON语法规则

数据在 名称/值在对中

##### json字符串转为对象

```js
//1、eval('('+json名称+')')；
//2、JSON.parse(json名称)
```

##### json 对象转为字符串

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
        //get用来请求数据,请求参数拼接在了请求路径的后面，http://*********?参数=值&餐数2=值
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

