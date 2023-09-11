## 函数扩展&模板字符串&Set&Map

## 模版字符串



在传统javascript中，输出模版通常是字符串拼接的形式，如下：



```javascript
  let name = '张三';
  let age = 25;
  let address = '河南郑州';

    //传统
    document.write('我叫'+name+'，今年'+age+'岁了来自'+address);

    // es6写法
    document.write(`我叫${name}今年${age}岁了，`\n`来自${address}`);
```



```js
let person = {
    name:'铁柱',
    age:45,
    job:'不会写代码的铁匠不是一个合格的干饭人，请问我的工作是什么'
}
let str = '<ul><li>我叫:'+person.name+'</li></li>我今年:'+person.age+'</li><li>我的工作：'+person.job+'<li></ul>';

缺点：写法繁琐，不好维护，使用不方便；
改进方案：ES6中，引入模版字符串，来解决此问题；
```

ES6中用反引号（``）标识。它可以当作普通字符串使用，也可以用来定义多行字符串，或者在字符串中嵌入变量

```js
//普通自字符串
`javaScript String`

//多行字符串
`It's a fine day today
Let's study together
`

//在字符串中嵌入变量,需要将变量名写在${}之中
`
<ul>
<li>我叫：${person.name}</li>
<li>我今年：${person.age}</li>
<li>我的工作：${person.job}</li>
</ul>
`

//大括号内部可以放入任意的 JavaScript 表达式，可以进行运算，以及引用对象属性。
//模板字符串之中还能调用函数
`今天是：${new Date()}`

let x = 1;
let y = 2;
var str = `${x} + ${y * 2} = ${x + y * 2}`;
document.write(str)
// "1 + 4 = 5"
```



## 函数参数的默认值

ES6 允许为函数的参数设置默认值，即直接写在参数定义的后面。

```js
function add(a=1,b=1){
	return a+b;
}
add();//2
add(2);//3
add(20,1) //21
```

ES6之前函数参数默认值的实现：

```js
   function fn(x,y){
        y = y ||'world';
        console.log(x,y);
    }


    // fn('hello','world');
    fn('hello');
    fn('hello','');
```

ES6之后：

```js
function fn(x,y='world'){
        console.log(x,y);
    }

    fn('hello','world');
    fn('hello');
    fn('hello','');
```





## 和对象的解构赋值结合：

```js
function fn({x,y='world'}){
        console.log(x,y);
    }

    fn({x:'hello',y:''});
    fn({x:'hello',y:undefined});
    fn({x:'hello'});
```



```js
function add(a,b){
 return a+b;
}
add();//NaN

function add(a,b){
   a = a || 1;
   b = b || 1;
 return a+b;
}
add();//2
//传参，但是传参时对应的布尔值为false,则赋值不起作用
add(2,0) // 3   原因是0在做 || 运算时，被对应转成了false, 所以默认值 1 起作用了。  可以尝试 '' ,undefined,null 等


优化：
function add(a,b){
    a = typeof a == 'undefined' ? 1 : a;
    b = typeof b == 'undefined' ? 1 : b;
    return a+b;
}
add();//2
add(2)//3
add(2,undefined); //3   依然存在问题，所以推荐使用ES6中的函数参数默认值

```

与解构赋值默认值结合使用（回顾上一章节）

## rest参数

ES6 引入 rest 参数（形式为`...变量名`），用于获取函数的多余参数（...运算符，剩余运算符的用法），这样就不需要使用`arguments`对象了。rest 参数搭配的变量是一个数组，该变量将多余的参数放入数组中。

```js
function add(...arg){
    console.log(arg); //[1,2,3,4,5]
    let sum = 0;
    arg.forEach(function(item){
        sum+=item;
    });
    return sum;
}
add(1,2,3,4,5); //15

```

```js

#//注意，rest 参数之后不能再有其他参数（即只能是最后一个参数），否则会报错。
 function add(...arg,a,b) {
        console.log(a,b); 
        let sum = 0;
        arg.forEach(function (item) {
            sum += item;
        });
        return sum;
    }
    add(1, 2, 3, 4, 5); 
```



补充arguments

```js
//arguments对象是所有（非箭头）函数中都可用的局部变量。
//你可以使用arguments对象在函数中引用函数的参数。此对象包含传递给函数的每个参数，第一个参数在索引0处。
//是一个对应函数参数的类数组对象。不是一个真正的数组。无法使用数组的方法

 // let arr = [1, 3, 10, 7];
    // arr = arr.sort(function (a, b) {
    //     return a - b;
    // });
    // console.log(arr);

    function add() {
        // console.log(arguments[3]);
        // console.log(typeof arguments);
        arguments = arguments.sort(function (a, b) {
            return a - b;
        });
        console.log(arguments);


    }
    add(1, 2, 3, 4, 5);
```



## 严格模式

es5中：

```javascript
<script>
    // 未使用严格模式时，可以使用
    // 此时为声明的a 作为了全局变量
    a = 10;
    console.log(a);
</script>
```

```javascript
<script>
    // 未使用严格模式时，可以使用
    // 此时为声明的a 作为了全局变量


    //使用严格模式  即声明 'use strict'
    //此时会报错 因为a没有声明 使用了严格模式 不会自动提升为全局变量
    'use strict'
    a = 10;
    console.log(a);//a is not defined
</script>
```





ES2016 做了一点修改，规定只要函数参数使用了默认值、解构赋值、或者扩展运算符，那么函数内部就不能显式设定为严格模式，否则会报错。

```javascript
// 报错
function doSomething(a, b = a) {
  'use strict';
  // code
}


// 报错
const doSomething = function ({a, b}) {
  'use strict';
  // code
};


// 报错
const doSomething = (...a) => {
  'use strict';
  // code
};


const obj = {
  // 报错
  doSomething({a, b}) {
    'use strict';
    // code
  }
};
```





## [箭头函数](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Functions/Arrow_functions)



### 基本用法

```js
//ES6 允许使用“箭头”（=>）定义函数。
var f = v => v;

// 等同于
var f = function (v) {
  return v;
};
//如果箭头函数不需要参数或需要多个参数，就使用一个圆括号代表参数部分。
//如果箭头函数的代码块部分多于一条语句，就要使用大括号将它们括起来，并且使用return语句返回。
//由于大括号被解释为代码块，所以如果箭头函数直接返回一个对象，必须在对象外面加上括号，否则会报错。
//箭头函数可以与变量解构结合使用。
//箭头函数表达式的语法比函数表达式更简洁，并且没有自己的this，arguments，super或new.target。箭头函数表达式更适用于那些本来需要匿名函数的地方，并且它不能用作构造函数。
```

```js
 var f1 = v => v;

// 等同于
var f2 = function (v) {
        return v;
 };

console.log(f1(5));
console.log(f2(8));
```



>如果箭头函数的参数有且只有一个那么、小括号可以省略
>如果箭头函数的返回值只有一个那么return和都可以省略

```js
var f1 = ()=>5;
    console.log(f1());
```

```js
var f1 = (x,y)=>{return (y+x)};
    console.log(f1(1,2));
```

```js
 var f1 = (x,y)=>{return ({x,y})};

    let obj = f1(1,2);

    console.log(obj.x);
    console.log(obj.y);
```



### 使用注意点

（1）箭头函数体内的`this`对象，并且没有自己的`this`，但是可以使用（继承）

```css
	 箭头函数自身没有this，它的this是父级普通函数的this。如果箭头函数式没有父级函数，则this指向window
```

（2）不可以当作构造函数，也就是说，不可以使用`new`命令，否则会抛出一个错误。

```css
		因为箭头函数内部没有this对象
```

（3）不可以使用`arguments`对象，该对象在函数体内不存在。如果要用，可以用 rest 参数代替。

  (4)   箭头函数没有`prototype`属性。



### 箭头函数的this

- 箭头函数不会创建自己的`this,但是可以使用（继承）`
- 它只会从自己的作用域链的上一层继承this
- 涉及到函数嵌套，内层的箭头函数的this， 继承于父级
- 如果没有函数嵌套，箭头函数中的this,指向window



> 箭头函数的this是静态的，他的this始终指向函数声明作用域下的this的值
>
> 箭头函数声明在全局中，直接调用的话  this指向window

```js
  window.name = '老陈';

    function getName1() {
        console.log(this.name);
    }

    // 箭头函数
    let getName2 = ()=>{
        console.log(this.name);
    }

    let start_name = {
        name:'吴彦祖'
    }
    // 直接调用
    // getName1(); //老陈
    // getName2(); //老陈

    //call方法调用 改变this指向 继承strat_name

    getName1.call(start_name);//吴彦祖       
    getName2.call(start_name);//老陈       

```



箭头函数无法作为构造函数：

```javascript
 //箭头函数无法作为构造函数
    let Person=(name,age)=>{
        this.name = name;
        this.age = age;
    }

    let lc = new Person('老陈',18);
    console.log(lc);//Uncaught TypeError: Person is not a constructor
```



箭头函数不可以使用`arguments`对象

```javascript
  //箭头函数不可以使用arguments对象
    let fn = () =>{
        console.log(arguments);
    }
    fn();//arguments is not defined
```





箭头函数的使用场景：

需求，点击div，1s后变颜色

通过定时器修改div的背景颜色为红色

```javascript
    var div_ = document.querySelector('div');
    div_.addEventListener('click',function(){    
        //无法完成 因为此时的this指向了window
        setTimeout(function(){
            console.log(this);
            div_.style.backgroundColor = 'red';
        },2000)
        
    })
```

指定当前对象  

```javascript
    var div_ = document.querySelector('div');
    div_.addEventListener('click',function(){ 
        let that = this;   
        //无法完成 因为此时的this指向了window
        setTimeout(function(){
            console.log(that);
            that.style.backgroundColor = 'red';
        },2000)
        
    })
```







使用箭头函数：

```javascript
 var div_ = document.querySelector('div');
    div_.addEventListener('click',function(){ 
       
        // 因为箭头函数的this 指向了声明时所在的作用域的中
        setTimeout(()=>{

            this.style.backgroundColor = 'red';
        },2000)
        
    })
```



### **箭头函数跟普通函数的区别**【面试题】

1.**写法不同**

> 箭头函数使用箭头定义，普通函数中没有。
>
> 普通函数使用function定义函数，箭头函数，省略了funchtion，在函数的参数后面使用箭头声明

```javascript
//箭头函数
(参数1，参数2...参数n)=>{  //代码段 }
//普通函数
function 函数名(参数1，参数2...参数n)=>{  //代码段  }
1234
```



**2.箭头函数不能用于构造函数**

> 普通函数可以用于构造函数，以此创建对象实例。
>
> 构造函数的this 指向到 当前构造函数的实例对象   this是可以改变的
>
> 箭头函数的this无法改变，箭头函数的this无法指向当前函数的实例对象，继承他声明所在上级函数的this,所以 他不能作为构造函数



**3.箭头函数中this的指向不同**

> 箭头函数自身没有this，它的this是父级普通函数的this。如果箭头函数式没有父级函数，则this指向window
> 在普通函数中，this总是指向调用它的对象或者window，如果用作构造函数，它指向创建的对象实例。



**4.箭头函数不具有arguments对象**

> 每一个普通函数调用后都具有一个arguments对象，用来存储实际传递的所有参数。
> 但是箭头函数并没有此对象。
>
> 如果箭头函数想要获取全部的参数，需要使用reset参数获取



**5.箭头函数不具有prototype原型对象。**

```javascript
  let fn = function () { }
  console.log(fn.prototype);//constructor: ƒ fn()

  let fn1 = () => { }
  console.log(fn1.prototype);//undefined
```



**6.箭头函数不具有super。**



## this指向【定稿，面试题】



1.在普通函数中，this指向window

2.在自执行函数中，this指向window

3.在定时器，this指向window

4.计时器中，this指向window

5.在事件调用函数中，this指向触发当前事件的对象

6.在对象的方法中 ，this 指向当前对象

7.在构造函数中使用this,this指向当前构造函数创建的实例。（new 构造函数得到的对象）

8.在构造函数的原型对象中，this依然指向当前构造函数的实例对象

9.箭头函数中，箭头函数本身是没有this的，它的this是父级普通函数的this。如果箭头函数没有父级函数，则this指向window



## Set 数据结构



> 里面没有重复的值
>
> 如果你往set里面存储重复值，只保留一个，把重复的值自动过滤掉
>
> 利用set结构，完成数组去重



基本用法：

- ES6 提供了新的数据结构 Set。它类似于数组，但是成员的值都是唯一的，没有重复的值。

- `Set`本身是一个构造函数，用来生成 Set 数据结构

- `Set`函数可以接受一个数组作为参数(或者具有 iterable 接口的其他数据结构），用来初始化。

- ```js
  let my_set = new Set();
  my_set.add('a');
  my_set.add('a');
  [...my_set];//['a']
  
  let arr = [1, 2, 3, 2, 2, 5, 8, 4, 5, 87, 1, 2, 5, 5];
  let s = new Set(arr);
  
  
  ```

```js
 // 去除数组的重复成员
 let arr = [1, 2, 3, 2, 2, 5, 8, 4, 5, 87, 1, 2, 5, 5];

    // 去重数组成员
    var set = new Set(arr);
    let new_arr =[...set];
    console.log(new_arr);
```



```js
 // 字符串去重
    let str = 'hello baby';
    let set = new Set(str);
    let n_str =  [...set].join('');
    console.log(n_str); //helo bay
```

向 Set 加入值的时候，不会发生类型转换，所以`5`和`"5"`是两个不同的值。Set 内部判断两个值是否不同，使用的算法叫做“Same-value-zero equality”，它类似于精确相等运算符（`===`），主要的区别是向 Set 加入值时认为`NaN`等于自身，而精确相等运算符认为`NaN`不等于自身。



下面代码向 Set 实例添加了两次`NaN`，但是只会加入一个。这表明，在 Set 内部，两个`NaN`是相等的。

```js
 let set = new Set();
    let a = NaN;
    let b = NaN;
    set.add(a);
    set.add(b);

    console.log(set);//NaN
```





set中，两个对象总是不相等的。

因为两个对象内存地址不一样

```js
 	let set = new Set();

    set.add({});
    console.log(set.size);//1

    set.add({});
    console.log(set.size);  // 2
	console.log({} === {});//false
```



## Set实例的属性和方法

Set 结构的实例有以下属性。

- `Set.prototype.constructor`：构造函数，默认就是`Set`函数。
- `Set.prototype.size`：返回`Set`实例的成员总数。

Set 实例的方法分为两大类：操作方法（用于操作数据）和遍历方法（用于遍历成员）。



### 操作方法



- `Set.prototype.add(value)`：添加某个值，返回 Set 结构本身。
- `Set.prototype.delete(value)`：删除某个值，返回一个布尔值，表示删除是否成功。

```js
  let set = new Set();
    set.add('a');
    set.add('b');
    set.add('c');
    set.add('d');
    set.add('e');

    console.log(set);//abcde

    set.delete('a');
    console.log(set);bcde
```



- `Set.prototype.has(value)`：返回一个布尔值，表示该值是否为`Set`的成员。

```js
 // has 判断是否包含
    let set = new Set();
    set.add('a');
    set.add('b');
    set.add('c');
    set.add('d');
    set.add('e');

    console.log(set.has('a'));//true
    console.log(set.has('h'));//false
```



- `Set.prototype.clear()`：清除所有成员，没有返回值。

```js
// clear() 清空set
    let set = new Set();
    set.add('a');
    set.add('b');
    set.add('c');
    set.add('d');
    set.add('e');

    set.clear();
    console.log(set);//set(0){}
```



###       遍历方法

- `Set.prototype.keys()`：返回键名的遍历器对象

没有键值对  键值是一样的

```js
 let set = new Set(['red', 'green', 'blue']);
    console.log(set.keys());//{"red", "green", "blue"}
    for (let i of set.keys()){
        console.log(i); // red  green  blue
    } 
```



- `Set.prototype.values()`：返回键值的遍历器对象

```javascript
let set = new Set(['red', 'green', 'blue']);
    console.log(set.values());//{"red", "green", "blue"}
    for (let i of set.values()){
        console.log(i); // red  green  blue
    } 
```



- `Set.prototype.entries()`：返回键值对的遍历器对象

```javascript
let set = new Set(['red', 'green', 'blue']);
console.log(set.entries());//{"red" => "red", "green" => "green", "blue" => "blue"}
for (let i of set.entries()){
   console.log(i); //  ["red", "red"] ["green", "green"] ["blue", "blue"]
} 
```



- `Set.prototype.forEach()`：使用回调函数遍历每个成员

```javascript
 let set = new Set(['red', 'green', 'blue']);
    // set.forEach((value,key)=> console.log(value+'::::'+key))
    // set.forEach((value)=> console.log(value))

    set.forEach(function(value){
        console.log(value);//red green  blue
    })
```

Set 结构的键名就是键值（两者是同一个值），因此第一个参数与第二个参数的值永远都是一样的。





```js
    //set不存储重复值
    let arr01 = [1, 3, 5, 7, 3, 2, 4, 3, 9, 7, 5, 4, 5, 9];
    let set01 = new Set(arr01);
    console.log(set01);
    /*{ 1, 3, 5, 7, 2, … }
    [[Entries]]
    0: 1
    1: 3
    2: 5
    3: 7
    4: 2
    5: 4
    6: 9
    size: 7
    [[Prototype]]: Set*/

    //set.add() 添加值到最后
    set01.add(99)
    console.log(set01);

    //set.delete()  删除匹配值
    set01.delete(99);



    let arr02 = 'hello world'
    let set02 = new Set(arr02);
    console.log(set02);
    //set.has() 判断是否包含值返回值为布尔类型
    let result01 = set02.has('l');
    console.log(result01);//true
    let result02 = set02.has('i');
    console.log(result02);//false

    //清除所有值,没有返回值
    set02.clear();
    console.log(set02);//Set(0) {size: 0}



    let arr03 = ['red', 'green', 'blue'];
    let set03 = new Set(arr03);
    console.log(set03.keys());
    //遍历返回每一项键名
    for (let item of set03.keys()) {
        console.log('for of 键名的' + item);
    }

    console.log(set03.values());
    //遍历返回每一项键值
    for (let item of set03.values()) {
        console.log('for of 键值的' + item);
    }

    console.log(set03.entries());
    //遍历返回每一项键名及键值
    for (let item of set03.entries()) {
        console.log(item);
    }

    //forEach回调函数遍历出set03的每一项
    set03.forEach(item => {
        console.log('forEach的' + item);
    });
```



## Map数据结构



### 基本用法：



ES6之前，对象以键值对来保存数据时，键只能是字符串，这给他带来了很大的限制



```js
//    es5中  对象的键名必须是字符串
 
    let person = {
        1:100,
        name:'张三', 
        
    }
    console.log(person.name);//张三
 // console.log(person.1);//报错
        
```

为了解决这个问题，ES6 提供了 Map 数据结构。它类似于对象，也是键值对的集合，但是“键”的范围不限于字符串，各种类型的值（包括对象）都可以当作键。也就是说，Object 结构提供了“字符串—值”的对应，Map 结构提供了“值—值”的对应，是一种更完善的 Hash 结构实现。如果你需要“键值对”的数据结构，Map 比 Object 更合适。

```js
 // new Map() 创建map对象
    // map.set(键，值)  向map中存放键值对
    var map = new Map();
    map.set(1,10);
    map.set([1,2,3],10);
    console.log(map);//{1 => 10, Array(3) => 10}

//作为构造函数，Map 也可以接受一个数组作为参数。
// 该数组的成员是一个个表示键值对的数组。 数组里面的两个值 分别是一个键值对
let m = new Map([["key","value"],["num","000001"],["age",120]]);
console.log(m,m.size);
```



### Map 结构的实例有以下属性和操作方法。

- `size`属性返回 Map 结构的成员总数。

- **Map.prototype.set(key, value)**
  
  - `set`方法设置键名`key`对应的键值为`value`，然后返回整个 Map 结构。如果`key`已经有值，则键值会被更新，否则就新生成该键。
  
  ```javascript
   // set 添加成员
      var map = new Map();
      map.set(1,'你好');
      map.set('age',20);
      console.log(map);//{1 => "你好", "age" => 20}
  ```
  
  
  
- **Map.prototype.get(key)**
  
  - 	`get`方法读取`key`对应的键值，如果找不到`key`，返回`undefined`。
  
- **Map.prototype.has(key)**
  
  - `has`方法返回一个布尔值，表示某个键是否在当前 Map 对象之中。
  
  ```
   const map = new Map([
          ['name', '张三'],
          ['title', 'Author']
      ]);
  
      map.size // 2
      console.log(map.has('name'));  // true
      console.log(map.get('name'));  // "张三"
      console.log(map.has('title')); // true
      console.log(map.get('title')); // "Author"
  ```
  
  
  
- **Map.prototype.delete(key)**
  
  - `delete`方法删除某个键，返回`true`。如果删除失败，返回`false`。
  
  
  
- **Map.prototype.clear()**
  
  - `clear`方法清除所有成员，没有返回值。
  
  
  
  ```js
   const map = new Map([
          ['name', '张三'],
          ['title', 'Author']
      ]);
      console.log(map.delete('name'));//true
      console.log(map);//Map(1) {"title" => "Author"}
  
      map.clear();
      console.log(map);//全部删除
  ```
  
  

### 遍历方法

Map 结构原生提供三个遍历器生成函数和一个遍历方法。

- `Map.prototype.keys()`：返回键名的遍历器。

- `Map.prototype.values()`：返回键值的遍历器。
- `Map.prototype.entries()`：返回所有成员的遍历器。

- `Map.prototype.forEach()`：遍历 Map 的所有成员(值)。



```js
  // 遍历
    const map = new Map([
        ['name', '张三'],
        ['title', 'Author'],
        ['age', '30']

    ]);

    //遍历键名
    for (let i of map.keys()) {
        console.log(i);// name  title age
    }

    for (let v of map.values()) {
        console.log(v);//张三 Author 30
    }

    // entries() 拿到所有的键值
    console.log(map.entries());
    console.log('------------entris------------');
    for (let item of map.entries()) {
        console.log(item[0], item[1]);
    }

    //entries 第二种取值方法
    for (let [key, value] of map.entries()) {
        console.log(key, value);
    }


  //   forEach (第一个参数是值，第二个参数是键名)
  map.forEach((val, key) => {
    console.log(key, val);
  });
```



## ES6对象新增方法



> Object.keys()：获取对象的键，es6之前就有的方法；
> Object.values()：获取对象的值，es6新增方法；
> Object.entries()：获取对象的键与值，es6新增方法。



```js
const person = {
	name: 'laochen',
	age: 22
};

cnosole.log(Object.keys(person)); // ["name", "age"]
cnosole.log(Object.values(person)); // ["laochen", 22]
cnosole.log(Object.entries(person)); // [["name", "laochen"], ["age", 22]]

```



## 与其他数据结构的互相转换



**（1）Map 转为数组**

前面已经提过，Map 转为数组最方便的方法，就是使用扩展运算符（`...`）。

```javascript
const map = new Map([
        [1, 'one'],
        [2, 'two'],
        [3, 'three'],
    ]);

    console.log([...map.keys()]); //[1, 2, 3]
    console.log([...map.values()]); // ["one", "two", "three"]

```

**（2）数组 转为 Map**

将数组传入 Map 构造函数，就可以转为 Map。

```javascript
 let arr = [[1, 'one'],[2, 'two'],[3, 'three'],];
    let map = new Map(arr);
    console.log(map);
```

**（3）Map 转为对象**

如果所有 Map 的键都是字符串，它可以无损地转为对象。

```javascript
 function strMapToObj(strMap) {
        let obj = Object.create(null);//创建空的对象
        for (let [k, v] of strMap) {
            obj[k] = v;
        }
        return obj;
    }

    const myMap = new Map()
        .set('yes', true)
        .set('no', false);

    console.log(strMapToObj(myMap)); 
// { yes: true, no: false }
```

如果有非字符串的键名，那么这个键名会被转成字符串，再作为对象的键名。

**（4）对象转为 Map**

对象转为 Map 可以通过`Object.entries()`。    Object.keys() //返回对象的键名    Object.entries() //以数组形式返回对象的键值对

```javascript
obj ==>数组==>map
let obj = {"a":1, "b":2};
Object.entries(obj) //[['a',1],['b',2]]
let map = new Map(Object.entries(obj));
```

此外，也可以自己实现一个转换函数。

```javascript
function objToStrMap(obj) {
  let strMap = new Map();
  for (let k of Object.keys(obj)) {
    strMap.set(k, obj[k]);
  }
  return strMap;
}

objToStrMap({yes: true, no: false})
// Map {"yes" => true, "no" => false}
```

**（5）Map 转为 JSON**

Map 转为 JSON 要区分两种情况。一种情况是，Map 的键名都是字符串，这时可以选择转为对象 JSON。

```javascript
map==>obj==>json
  function strMapToObj(strMap) {
        let obj = Object.create(null);//创建空的对象
        for (let [k, v] of strMap) {
            obj[k] = v;
        }
        return obj;
    }
    
    function strMapToJson(strMap) {
        return JSON.stringify(strMapToObj(strMap));
    }

    let myMap = new Map().set('yes', true).set('no', false);
    console.log(strMapToJson(myMap)); 
// '{"yes":true,"no":false}'
```



**（6）JSON 转为 Map**

JSON 转为 Map，正常情况下，所有键名都是字符串。

```javascript
json==>obj===>map
jsonString == > obj ==> map
function jsonToStrMap(jsonStr) {
  return objToStrMap(JSON.parse(jsonStr));
}

jsonToStrMap('{"yes": true, "no": false}')
// Map {'yes' => true, 'no' => false}



  function objToStrMap(obj) {
        let strMap = new Map();
        for (let k of Object.keys(obj)) {
            strMap.set(k, obj[k]);
        }
        return strMap;
    }

    function jsonToStrMap(jsonStr) {
        return objToStrMap(JSON.parse(jsonStr));
    }

    console.log(jsonToStrMap('{"yes": true, "no": false}')); 
```



```js
    // let map01 = new Map();

    // //map.set();存储键和值  一次只存储一个键和值,剩余的丢弃
    // map01.set(1, 2, 3, 4, 5)
    // console.log(map01);//{1:2}
    // map01.set([1, 2, 3, 4], 5, 6, 7)
    // console.log(map01);//{[1,2,3,4]:5}


    // let map02 = new Map([
    //     ['name', '张三'],
    //     ['age', '18']
    // ])
    // 取键名为name的值
    // console.log(map02.get('name'));//张三
    // 取键名为age的值
    // console.log(map02.get('age'));//18
    // 判断是否包含address返回值为布尔类型
    // console.log(map02.has('address'));//false
    // 判断是否包含sex返回值为布尔类型
    // console.log(map02.has('sex'));//false

    // map02.set('address', '河南郑州');
    // 删除键名和键值
    // map02.delete('address');
    // console.log(map02);
    // 清除所有键值
    // map02.clear();
    // console.log(map02);


    // //遍历取出map02中所有的键名
    // for (let item of map02.keys()) {
    //     console.log(item);
    // }
    // //遍历取出map02中所有的键值
    // for (let item of map02.values()) {
    //     console.log(item);
    // }
    // //遍历取出map02中所有的键名和键值
    // for (let item of map02.entries()) {
    //     console.log('第一种方法' + item[0], item[1]);
    // }
    // //遍历取出map02中所有的键名和键值
    // for (let [key, value] of map02.entries()) {
    //     console.log('第二种方法' + key, value);
    // }
    // //遍历取出所有的键值
    // map02.forEach(item => {
    //     console.log(item);
    // });



    // // Object.keys()：获取对象的键，es6之前就有的方法；
    // // Object.values()：获取对象的值，es6新增方法；
    // // Object.entries()：获取对象的键与值，es6新增方法。


    // const obj = {
    //     name: '老六',
    //     age: '666',
    //     address: '羀醴鶹'
    // }
    // console.log(obj);
    // //该对象所有的键名
    // console.log(Object.keys(obj));

    // //该对象所有的键值
    // console.log(Object.values(obj));

    // //该对象所有的键名和键值
    // console.log(Object.entries(obj));





    let map03 = new Map([
        [1, 'one'],
        [2, 'two'],
        [3, 'three'],
    ]);
    // map转为数组
    // console.log([...map03]);//[Array(2), Array(2), Array(2)]
    // console.log([...map03.keys()]);//[1, 2, 3]
    // console.log([...map03.values()]);//['one', 'two', 'three']
    // console.log([...map03.entries()]);//[Array(2), Array(2), Array(2)]


    //数组转为map
    // let arr04 = [[1, 'one'], [2, 'two'], [3, 'three']];
    // console.log(arr04);
    // let map04 = new Map(arr04);
    // console.log(map04);


    // map转为对象
    StrMapToObj = (StrMap) => {
        // let obj = Object.create(null)//等同于new Object
        let obj = new Object();//等同于new Object
        for (let [key, value] of map03) {
            obj[key] = value;
        }
        return obj;
    }
    let obj = StrMapToObj(map03)
    console.log(obj);


    //对象转为map
    ObjToStrMap = (obj) => {
        let map04 = new Map();
        for (let [key, value] of Object.entries(obj)) {
            map04.set(key, value)
        }
        return map04;
    }

    let map04 = ObjToStrMap(obj)
    console.log(map04);
```

```js
    // Map转JSON
    let map = new Map();
    map.set('1', 'one');
    map.set('2', 'two');
    map.set('3', 'three');
    console.log(map);

    maptoobj = (map) => {
        let obj = {};
        for (let [key, value] of map.entries(map)) {
            obj[key] = value;
            console.log(obj[key] = value);
        }
        return obj;
    }
    let obj = maptoobj(map);
    console.log(obj);

    objtojson = (obj) => {
        let json = JSON.stringify(obj);
        return json;
    }


    let json = objtojson(obj);
    console.log(json);



    //json转map
    jsontomap = (json) => {

        let obj2 = JSON.parse(json)
        return obj2;
    }
    let obj2 = jsontomap(json);
    console.log(obj2);


    objtomap = (obj2) => {
        let map01 = new Map();
        for (let [key, value] of Object.entries(obj2)) {
            map01.set(key, value)
        }
        return map01;
    }
    let map01 = objtomap(obj2);
    console.log(map01);
```

