## ES6

【1、代码块；2、先声明，再使用】

#### 基本用法

ES6新增let命令，用来声明变量。他的用法类似于var，但是所声明的变量，只在let命令所在的代码块{}内有效。

```js
{
    let A=10;
    var b=1;
}
a // ReferenceError: a is not defined.
b // 1
```

上面代码块中,分别用let和var声明了两个变量.然后在代码块之外调用这两个变量,结果let声明的变量报错,var声明的变量返回了正确的值,这表明,let声明的变量只在他所在的代码块有效

for循环的计数器,就很适合let命令.

```js
for(let i=0;i<10;i++){
//...
}
console.log(i)//ReferenceError:i is not defined
```

上面的代码块中,计数器 i 只在for循环体中有效,在循环体外引用就会报错

下面的代码如果使用var,最火输出的是10;

```js
for(var i=0;i<10;i++){
    
}
console.log(i)//10

var a = [];
for(let i=0;i<10;i++){
    a[i]=function(){
        console.log(i);
    };
}
a[6]();//10
```

上面代码中,变量i是let声明的,当亲爱的i侄子啊本轮循环中有效,所以每一次循环的i其实都是一个新的变量,所以最后输出的是6,你可能会问,如果每一轮循环的变量i都是重新声明的,那它怎么知道上一轮循环的值,从而计算出本轮循环的值?这是因为JavaScript引擎内部会记住上一轮的值,初始化本轮的变量i时,就在上一轮循环的基础上进行计算

另外,for循环还有一个特别之处,就是设置循环变量的那部分是一个父作用域,而循环体内部是一个单独的子作用域(作用域相互独立)

```js
for(let i=0;i<3;i++){
    let i=='adc';
    console.log(i);
}
//abc
//abc
//abc
```

上面代码正确运行,输出3次abc;表明函数内部的变量i与循环变量的i不在同一个作用域,有各自单独的作用域



#### 不存在变量提升

var命令会发生变量提升现象,即便两可以再声明之前使用,值为undefined;这种显现多多少少是有些奇怪的,按照一般逻辑,变量应该声明在语句之后才可以使用;

为了纠正这一现象,let命令改变了语法行为,他所在的声明的变量一定要在声明后使用,否则会报错

```js
//var的情况

console.log(floor);//输出undefined
var floor=2;


//let的情况
console.log(fire);//报错ReferenceError
let fire=2;
```

上面代码中,变量floor用var命令声明,会发生变量提升,及脚本开始运行时变量floor已经存在了,但是没有值,所以会输出undefined;变量fire用let命令声明,不会发生变量提升;这表示在生命给他之前,变量fire是不存在的,这时如果用到它就会抛出一个错误;

#### 暂时性死区

只要块级作用域内部存在let命令,他所声明的变量就绑定(binding)这个区域,不再受外部的影响;

```js
var tmp=123;
if(true){
    tmp='abc';
    let tmp;
    console.log(tmp);//ReferenceError
}
console.log(tmp)
```

上面代码中,存在全局变量tmp,但是块级作用域内let有声明了一个局部变量tmp导致后者绑定这个块级作用域,所以在let声明变量前,对tmp赋值会报错;

ES6明确规定;如果区块中存在let和const命令,这个区块对这些命令声明的变量,从一开始就形成了封闭的作用域;凡是在声明前就使用这些变量,就会报错;

总之在代码块内,使用let命令声明变量之前,该变量都是不可用的;这在语法上,称为暂时性死区(temporal dead zone 简称TDZ)

```js
if(true){
   //TDZ开始
    tmp='abc';//ReferenceError
    console.log(tmp)//ReferenceError
    
    let tmp=;//TDZ结束
    console.log(tmp)//undefined
    
    tmp=123;
    console.log(tmp);//123
   }
```

上面的代码中,在let命令声明变量tmp前都属于变量tmp的死区;

暂时性死区也意味着typeof不在是一个百分之百安全的操作

```js
typeof x;//ReferenceError
let x;
```

上面代码中,变量x使用let声明,生命之前,都属于x的死区,只要用到该变量就会报错.;因此typeof运行时就会抛出一个ReferenceError

作为比较,如果一个变量根本没有被声明,使用typeof反而不会报错

```js
console.log(typeof a);//undefined
var a=10;
```

上面的代码中,typeof a结果返回undefined所以,在没有let之前,typeof运算符是百分之百安全的,永远不会报错;现在这一点不成立了;这样的设计是为了让大家养成良好的变成习惯,变量一定要在声明之后使用,否则就会报错;

有些死区比较隐蔽,不太容易发现;

```js
//函数参数默认的写法
function bar(x=y,y=2){
    return [x,y];
}
bar()//报错
```

上面代码中,调用bar函数之所以会报错(某些实现可能不报错),是因为参数x默认等于另一个参数y,而此时y还没有声明,属于死区;如果y的默认值是x,就不会报错,因为此时x已经声明了

```js
function bar(x=2,y=x)
return [x,y];
bar();//[]2,2]
```

另外,下面的代码也会报错,与var的行为不同

```js
//不报错
var x=x;

//报错
let x=x;
//ReferenceError:x is not defined
```

上面的代码报错,也是因为暂时性死区;使用let声明变量是,只要变量在还没有生命完成前使用,就会报错;上面这行就属于这个情况,在变量x的声明语句还没有执行完成前,就去取x的值,导致报错x未定义

ES6规定暂时性死区和let、const语句不出现变量提升，主要是为了减少运行时出现的错误，防止在变量声明前就是用这个变量，从而导致意料之外的行为；这样的错误在ES6是很常见的，现在有了这种规定，避免此类错误就很容易了

总之，暂时性死区的本质就是，只要已进入当前作用域，所要使用的变量就已经存在了，但是不可获取，只有等到变量声明的哪一行代码出现，才可以获取和使用该变量

> 先声明 再使用

#### 不允许重复声明变量

let不允许重复在相同作用域内,重复声明同一个变量

```js
//报错
let a=10;
var a=10;

console.log(a);

let a=10;
let a=10;
```

#### 块级作用域

##### 为什么需要块级作用域?

ES6只有全局作用域和函数作用域,没有块级作用域,这会带来很多不黑的场景

第一种常见,内层变量可能会覆盖外层的变量

```js
var tmp=new Date();

function f(){
    console.log(tmp);
    if(false){
       	var tmp='hello world';
       }
}
f();//undefined
```

上面的代码的原意是if代码块的外部使用外层的tmp变量,内部使用内层的tmp变量;但是,函数f执行后,输出结果为undefined,原因在于变量提升,导致内层的tmp变量覆盖了外层的tmp变量

第二种场景,用来技术的循环变量泄露为全局的变量;

```js
var s='hello';
for(var i=0;i<s.length;i++){
    console.log(s[i]);
}

console.log(i);//5
```

上面的代码中,变量i只用来控制循环,但是循环结束后,他并没有消失,泄露了全局变量

#### ES6的块级作用域

let实际上为JavaScript新增了块级作用域

```js
function f1(){
    let n=5;
    if(true){
       let n=10;
       }
    console.log(n);//5
}
f1();
```

上面的函数有两个代码块,都声明了变量n;运行后输出5;这表示外层代码块不收内层代码块的影响,如果两次都是用var定义变量n,最后输出的值时10;

ES6允许块级作用域的任意嵌套

```js
{{{{
    {let insane='Hello World'}
    console.log(insane);//报错
}}}};
```

上面的代码使用了一个五层的块级作用域,每一层都是一个单独的块级作用域;第四层作用域无法读取第五层作用域的内部变量

内层作用域可以定义外层作用域的同名变量

```js
{{{{
    let insane='Hello World';
    {let insane="Hello World"}
}}}};
```

块级作用域的出现,实际上是的获得广泛应用的匿名立即执行函数表达式(匿名 IIFE)不再必要了

```js
//IIFE写法
(function(){
    var tmp=...;
    ...
})();
    IIFE的好处,
        1、避免作用域命名污染
        2、提升性能（减少了对作用域的查找）
        3、避免全局命名冲突
        4、保存闭包状态
        //块级作用域写法
        {
            let tmp=...;
            ...
        }
```

#### 块级作用域与函数声明

函数能不能在块级作用域之中声明呢?这是一个相当令人混淆的问题

ES6规定,函数只能在顶层作用域和函数作用域之中声明,不能在块级作用域声明;

```js
//情况一
if(true){
   function f(){
       console.log('haha');
   }
   }
f();
```

上面函数声明,根据ES6的规定都是非法的

但是,浏览器没有遵守这个规定,为了兼容以前的旧代码,还是支持在块级作用域之中声明函数,因此上面两种情况实际都能运行,不会报错

ES6引入了块级作用域,明确规定在块级作用域之中声明函数;ES6规定,块级作用域之中,函数声明语句的行为类似于let,在块级作用域之外不可引用

```js
function f(){
    console.log('I am outside!');
}

(function (){
    if(true){
       //重复声明一次函数f
        function f(){
            console.log('I am inside');
        }
       }
    f();
})();
```

上面在ES5中运行,会得到"I am inside",因为在if内声明的函数f会被提升到函数头部,实际运行的代码如下

```js
//ES5环境
function f(){
    console.log("I am outside");
}
(function (){
    function f(){
        console.log('I am inside')
        if(false){
           
           }
    }
    f();
})();
```

ES6就完全不一样了,理论上会得到 I am outside因为块级作用域内声明的函数类似于let,对作用域至外没有影响;到那时,如果,你真的在ES6浏览器运行一下上面的代码.是会报错的,这是为什么呢?

```js
//浏览器的ES6环境
function f(){
    console.log('I am outside');
}
(function (){
    if(false){
        //重复声明一次函数f
        function f(){
            console.log('I am inside');
        }
    }
    f();
})();
//Uncaught TypeError:f is not a function
```

上面的代码在ES6浏览器中都会报错

原来,如果改变了块级作用域内声明的函数的处理规则,显然会对老代码产生很大的影响;为了减轻因此产生的不兼容问题,ES6附录里面规定,浏览器的实现可以不遵守上面的规定,有自己的行为方式

+ 允许在块级作用域内声明函数;
+ 函数声明的类似于var,即会得到全局作用域或函数作用域的头部
+ 同时,函数声明还会提升到所在的块级作用域的头部

注意,上面的三条规则只对ES6的浏览器实现有效,其他环境的实现不用遵守,还是将块级作用域的函数声明当做let处理

根据这三条规则,浏览器的ES6环境中,块级作用域内声明的函数,行为类似于var的声明的变量;上面的例子实际运行的的代码如下

```js
//浏览器的ES6环境
function f(){
    console.log('I am outside');
	(function (){
        var f=undefined;
        if(false){
           function f(){
               console.log('I am inside');
           }
           }
        f();
    })();
}
```

考虑到环境导致id行为差异太大,应该避免咋块级作用域内声明函数,如果确实需要,也应该写成函数表达式,而不是函数声明语句

```js
//块级作用域内部的函数声明语句,简易不要使用
{
    let a='secret';
    function f(){
        return a;
    }
    console.log(f());
}

//块级作用域内部,优先用函数表达式
{
    let a='secret';
    let f=function(){
        return a;
    };
    console.log(f());
}
```

另外,还有一个需要注意的地方,ES6的块级作用域必须有大括号,若没有大括号,JavaScript引擎就认为不存在块级作用域

```js
//第一种写法,报错
if(true) let x=1;
console.log(x);

//第二种写法,不报错
if(true){
   let x=1;
    console.log(x);
   }
```

上面代码中,第一种写法没有大括号,所以不存在块级作用域,而let只能初心爱女子啊当前作用域的顶层,所以报错,第二种写法有大括号,所以块级作用域成立

> 1、let不存在变量提升
>
> 2、let不允许重复声明同名变量
>
> 3、let必须先声明，再使用
>
> 4、使用let声明的变量 产生了块级作用域 离声明该变量 最近的大括号作用域链 向上取值 就近原则

## const 命令 



### 基本用法

`const`声明一个只读的常量。一旦声明，常量的值就不能改变。

```javascript
const PI = 3.1415;
PI // 3.1415

PI = 3;
// TypeError: Assignment to constant variable.
```

上面代码表明改变常量的值会报错。

`const`声明的变量不得改变值，这意味着，`const`一旦声明变量，就必须立即初始化，不能留到以后赋值。

```javascript
const foo;
// SyntaxError: Missing initializer in const declaration
```

上面代码表示，对于`const`来说，只声明不赋值，就会报错。

`const`的作用域与`let`命令相同：只在声明所在的块级作用域内有效。

```javascript
if (true) {
  const MAX = 5;
}

MAX // Uncaught ReferenceError: MAX is not defined
```

`const`命令声明的常量也是不提升，同样存在暂时性死区，只能在声明的位置后面使用。

```javascript
if (true) {
  console.log(MAX); // ReferenceError
  const MAX = 5;
}
```

上面代码在常量`MAX`声明之前就调用，结果报错。

`const`声明的常量，也与`let`一样不可重复声明。

```javascript
var message = "Hello!";
let age = 25;

// 以下两行都会报错
const message = "Goodbye!";
const age = 30;
```

### 本质

`const`实际上保证的，并不是变量的值不得改动，而是变量指向的那个内存地址所保存的数据不得改动。对于简单类型的数据（数值、字符串、布尔值），值就保存在变量指向的那个内存地址，因此等同于常量。但对于复合类型的数据（主要是对象和数组），变量指向的内存地址，保存的只是一个指向实际数据的指针，`const`只能保证这个指针是固定的（即总是指向另一个固定的地址），至于它指向的数据结构是不是可变的，就完全不能控制了。因此，将一个对象声明为常量必须非常小心。

```javascript
const foo = {};

// 为 foo 添加一个属性，可以成功
foo.prop = 123;
foo.prop // 123

// 将 foo 指向另一个对象，就会报错
foo = {}; // TypeError: "foo" is read-only

```

上面代码中，常量`foo`储存的是一个地址，这个地址指向一个对象。不可变的只是这个地址，即不能把`foo`指向另一个地址，但对象本身是可变的，所以依然可以为其添加新属性。

下面是另一个例子。

```javascript
const a = [];
a.push('Hello'); // 可执行
a.length = 0;    // 可执行
a = ['Dave'];    // 报错
```

上面代码中，常量`a`是一个数组，这个数组本身是可写的，但是如果将另一个数组赋值给`a`，就会报错。

如果真的想将对象冻结，应该使用`Object.freeze`方法。

```javascript
const foo = Object.freeze({});

// 常规模式时，下面一行不起作用；
// 严格模式时，该行会报错
foo.prop = 123;
```

上面代码中，常量`foo`指向一个冻结的对象，所以添加新属性不起作用，[严格模式](https://www.runoob.com/js/js-strict.html)时还会报错。

除了将对象本身冻结，对象的属性也应该冻结。下面是一个将对象彻底冻结的函数。

```javascript
var constantize = function(obj){
  Object.freeze(obj);
    //Object.values();
  Object.keys(obj).forEach( (key, i) => {
    if ( typeof obj[key] === 'object' ) {
      constantize( obj[key] );
    }
  });
};
```



### ES6 声明变量的六种方法

ES5 只有两种声明变量的方法：`var`命令和`function`命令。ES6 除了添加`let`和`const`命令，后面章节还会提到，另外两种声明变量的方法：`import`命令和`class`命令。所以，ES6 一共有 6 种声明变量的方法。



## 顶层对象的属性



顶层对象，在浏览器环境指的是`window`对象，在 Node 指的是`global`对象。ES5 之中，顶层对象的属性与全局变量是等价的。



```javascript
window.a = 1;
a // 1

a = 2;
window.a // 2
```

上面代码中，顶层对象的属性赋值与全局变量的赋值，是同一件事。

顶层对象的属性与全局变量挂钩，被认为是 JavaScript 语言最大的设计败笔之一。这样的设计带来了几个很大的问题，首先是没法在编译时就报出变量未声明的错误，只有运行时才能知道（因为全局变量可能是顶层对象的属性创造的，而属性的创造是动态的）；其次，程序员很容易不知不觉地就创建了全局变量（比如打字出错）；最后，顶层对象的属性是到处可以读写的，这非常不利于模块化编程。另一方面，`window`对象有实体含义，指的是浏览器的窗口对象，顶层对象是一个有实体含义的对象，也是不合适的。



ES6 为了改变这一点，一方面规定，为了保持兼容性，`var`命令和`function`命令声明的全局变量，依旧是顶层对象的属性；另一方面规定，`let`命令、`const`命令、`class`命令声明的全局变量，不属于顶层对象的属性。也就是说，从 ES6 开始，全局变量将逐步与顶层对象的属性脱钩。

```javascript
var a = 1;
// 如果在 Node 的 REPL 环境，可以写成 global.a
// 或者采用通用方法，写成 this.a
window.a // 1

let b = 1;
window.b // undefined
```

上面代码中，全局变量`a`由`var`命令声明，所以它是顶层对象的属性；全局变量`b`由`let`命令声明，所以它不是顶层对象的属性，返回`undefined`。

## globalThis 对象

JavaScript 语言存在一个顶层对象，它提供全局环境（即全局作用域），所有代码都是在这个环境中运行。但是，顶层对象在各种实现里面是不统一的。

- 浏览器里面，顶层对象是`window`，但 Node 和 Web Worker 没有`window`。
- 浏览器和 Web Worker 里面，`self`也指向顶层对象，但是 Node 没有`self`。
- Node 里面，顶层对象是`global`，但其他环境都不支持。

同一段代码为了能够在各种环境，都能取到顶层对象，现在一般是使用`this`变量，但是有局限性。

- 全局环境中，`this`会返回顶层对象。但是，Node.js 模块中`this`返回的是当前模块，ES6 模块中`this`返回的是`undefined`。
- 函数里面的`this`，如果函数不是作为对象的方法运行，而是单纯作为函数运行，`this`会指向顶层对象。但是，严格模式下，这时`this`会返回`undefined`。
- 不管是严格模式，还是普通模式，`new Function('return this')()`，总是会返回全局对象。但是，如果浏览器用了 CSP（Content Security Policy，内容安全策略），那么`eval`、`new Function`这些方法都可能无法使用。

综上所述，很难找到一种方法，可以在所有情况下，都取到顶层对象。

[ES2020](https://github.com/tc39/proposal-global) 在语言标准的层面，引入`globalThis`作为顶层对象。也就是说，任何环境下，`globalThis`都是存在的，都可以从它拿到顶层对象，指向全局环境下的`this`。

```js
//demo.js

//浏览器环境：
console.log(globalThis); //window
//node环境
console.log(globalThis); //global
```