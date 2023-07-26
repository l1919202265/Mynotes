## JavaScriptCookie

Cookie用于存储页面的用户信息

常见例子：自动登录、记住用户名或密码

##### 会话

一次会话，就像一次谈话

一次会话包含多次请求和响应

http是无状态的协议

一次会话：浏览器第一次给服务器资源发送请求，会话建立，知道一方断开为止

##### 会话的功能

共享数据

在一次会话的多次请求间共享数据

我们之前学习了http协议，http协议无状态的，每次浏览器发送请求，服务器给出相应，不同的请求响应之间，相互独立，是没有关系的，无法进行数据的共享和交换

、

想要不同请求响应之间可以进行数据的交换，这就用到了会话技术。比如我们点击淘宝买东西，买不同的东西加入购物车，最终我们去购物车结算的时候，算的是这全部的商品，每点击添加一个商品完成了一次请求响应，最终这么多请求相应的数据一起结算，这就是使用了会话技术

##### 共享数据的方式

1、客户端会话技术：Cookie	client客户端	浏览器

把共享的数据存储在客户端（浏览器）

cs	client——>server 客户端

bs	browser——>server	浏览器

2、服务器端会话技术：Session	server  服务器

把共享的数据存储在服务器端

## Cookie

##### 1、Cookie概念：

将数据存在客户端【浏览器】的一门会话技术

### 2、Cookie会话技术的过程

客户端发送请求，服务器响应数据

客户端把响应得到的数据存储在浏览器端

第二次请求的时候，浏览器携带存储的数据继续请求



### Cookie实现原理

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

### 5、Cookie特性

1、同一个网站中所有页面共享一套cookie，cookie是按照域名进行存储的

2、数量、大小有限4-10k

3、过期时间，因为存储的空间太小了，所以到期就把数据给清理掉了

4、每次会随着HTTP请求发送给服务器，每次请求都要携带的信息（最典型的就是身份认证的信息）就特别适合放在cookie中，其他类型的数据就不合适了

## 使用JavaScript操作cookie

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

#### 封装Cookie

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

## storage本地存储

#### cookie和storage对比的缺点

##### Cookie

只能存储4KB

浪费宽带，每次会随着HTTP请求发送给服务器

操作数据很繁琐，没有方便的API

存储默认20分钟，页面关闭就消失

### Storage本地存储（H5新增特性）

大小最小5MB，可以申请更大的空间

不会随HTTP请求发送给服务器

非常容易操作

移动端普及高

LocalStorage与sessionStorage两种

localStorage只要不删除，永久删除

sessionStorage 页面关闭 立即消失

## LocalStorage本地存储

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

### sessionStorage

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

#### LocalStorage同源事件

当同源的LocalStorage有更改以后，会触发这个事件

#### 使用cookie记住密码

