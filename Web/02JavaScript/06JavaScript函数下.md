# 函数下

### 作用域

1、全局作用域

```javascript
var num = 10;
num = 10;
//不写var的时候 声明变量 默认全局变量
function fn(){
    console.log('函数内调用num:'+num);
}
fn();
console.log(num);
```

2、函数（局部）作用域

```javascript
//函数内部声明的变量 作用域：声明变量的函数内
//离当前变量 向上最近的大括号内
function fn(){
    var num =10;
    console.log('函数内调用的：'+num);
}
fn();
console.log(num);//num is not defined num这个变量找不到 意思 还没有声明

 

var num = 99;
function fn(){
    num = 10;//不加var默认全局变量	全局变量修改
    console.log('函数内调用：' + num);
}
console.log(num);//99
fn();//10
console.log(num);//10
```

## 1、代码的检查装载阶段（预编译阶段）

```javascript
//此阶段进行变量和函数的声明，但是不对变量进行赋值，变量的默认值为undefined

//大白话，就是将所有的声明（此时可理解为变量声明），都提升到最当前作用域最上面的位置，!!!有变量名，但是没有值!!!，就叫只声明不赋值，所以默认值undefined

//对变量进行提升 提升到当前作用域的最前面 只声明 不赋值
//函数 具名函数 对函数 进行提升 提升到当前作用域的最前面 整个提升 包含函数内的内容

//预编译阶段	把所有的变量	提升到最前面	只声明	不赋值


//ES6不存在变量提升
```

```javascript
//var num;

console.log(num);//undefined
var num = 18;





//函数和变量名在进行预编译阶段 进行提升的时候 变量在最前面 函数在下面
/*var num;
function fn(){
    console.log(num);//undefined
}*/

fn();
var num = 5;
function fn(){
    console.log(num);
}
```



## 2、代码的执行阶段

```javascript
//此阶段对变量进行赋值核函数的声明

//大白话：搞完步骤1以后，会对变量进行赋值。并从上向下执行

//对变量 进行一一赋值
```

```javascript
var a = 100;//全局
function fn(){
    var b = 2*a;
    var a = 200;
    var c = a / 2;
    alert(b);
    alert(c);
}
fn();
```

## 作用域链

一般情况下，变量取值是到创建这个变量的函数的作用域中取值。

但是如果在当前作用域中没有查到值，就会向上级作用域去查，直到查到全局作用域

这么一个查找过程形成的链条就叫做作用域链	

```javascript
        var x = 10;
        function f1() {
            var x = 11;
            function f2() {
                var x = 12;
                function f3() {
                    console.log(x);
                }
                f3()
            }
            f2()
        }
        f1(); //12
```

## 闭包

```javascript
function zs(){
    var ring = '祖母绿宝石戒指'
    return function (){
        return ring;
    }

}
var xpt_ = zs();
console.log(xpt_);
var ring _ = xpt();
console.log)(ring_);
```

## 闭包的优缺点

```javascript
function fn(){
    vae num = 0;
    return function(){
        num++;
        console.log(num);
    }
}
var fn1 = fn();
fn1();//1
var num =10;
fn1();//2
fn1();//3

var fn2 = fn();
fn2()；//1
fn2();//2
fn2();//3



//js垃圾回收机制	GC
//全局变量	永远在 页面关闭 变量回收
//局部变量	用完就回收
//函数	用完就回收	函数正在被人用的时候	不能回收
//内存泄露
```

