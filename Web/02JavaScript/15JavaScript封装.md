## JavaScript封装

#### 基于Object的方式创建对象

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

#### 对象字面量

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

#### 在为函数传递大量可选参数时，可考虑使用对象字面量：



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

#### 工程模式的弊端：

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




#### instanceof和typeof的区别
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



#### constructor

用来查找当前对象的构造函数(找爸爸)