## Promise(异步编程解决方案)

#### 回调地狱

回调地狱的超级英雄

把异步编程同步解决

回调地狱（下一次的操作严格依赖于上一次）

回调地狱：最主要的就是因为功能逻辑代码嵌套的层次太多，导致可读性降低，维护困难，对代码性能，以及易读性，不友好

### Promise的含义

Promise是异步编程的一种解决方案，比传统的解决方案——回调函数和事件——更合理和更强大。它由社区最早提出和实现，ES6将其写进了语言标准，统一了用法，原生提供了Promise对象，所谓Promise，简单说就是一个容器，里面管理着异步的操作，从它可以获取异步操作的消息，本身不是异步的，是里面管理的操作是异步的。

Promise对象有以下两个特点：

1、对象的状态下不受外界影响。Promise对象代表一个异步操作，有三种状态：pending（进行中，待解决）、fufilled（已成功）、和rejected（已失败）。只有异步操作的结果，可以决定当前Promise对象+是哪一种状态，任何其他操作都无法改变这个状态。这也是Promise这个名字的由来，它的英语意思就是承诺，表示洽谈手段无法改变。

2、一旦状态改变，就不会再变，任何时候都可以得到这个结果。Promise对象的状态，只有两种可能：从pending变为fulfilled和从pending变为rejected。只要这两种情况发生，状态就凝固了，不会再变了，会一直保持这个结果，这时就称为resolved（已定型）。如果改变已经发生了，你再对Promise对象添加回调函数，也会立即得到这个结果。这与事件(Event)完全不同，事件的特点是，如果你错过了它，再去监听，是得不到的。

有了Promise对象，就可以将异步操作以同步操作的流程表达出来，避免了层层嵌套的回调函数。此外，Promise对象

提供统一的接口，使得控制异步操作更加容易。

Promise也有一些缺点。首先无法取消Promise，一旦新建他就会立即执行，无法中途取消，其次如果不设置回调函数，Promise内部抛出的错误，不会反映到外部，第三，当处于pending状态时，无法得知目前进展到哪一个阶段

Axios请求基于Promise

### 基本语法

定义：

ES6规定，Promise对象是一个构造函数

，用来生成Promise实例。

Promise是一个构造函数，需要实例化对象

Promise构造函数，接受一个函数作为参数



作为参数的函数也接受两个函数，分别是：

resolve

rejected

它们是两个函数，由JavaScript引擎提供，不用自己部署

resolve函数的作用是：将Promise对象的状态从"未完成"变为"成功"。即(从pending变为fulfilled)

在异步操作成功时调用，并将异步操作的结果，作为参数传递出去；

reject函数的作用，将Promise对象的状态从“未完成”变为"失败"。(即从pending变为rejected)

在异步操作失败时调用，并将异步操作报出的错误，作为参数传递出去。

即异步操作成功调用resolve函数  失败调用reject函数

```js
//Promise对象
//异步编程的解决方案	 解决了回调地狱的问题

//Promise本身是同步	但是promise。then()是异步的 Promise把内部的这些操作  同步化解决了

//Promise把异步编程同步化

//Promise立即执行

//创建Promise实例对象的时候  需要接受一个函数作为参数

//作为函数的参数，也有两个参数resolve（放成功的状态）、reject（失败的状态）

//三种状态：pending（等待中 此时Promise的状态不是成功也不是失败）、fulfilled（成功的状态）、rejected（失败的状态）

//promise本身是同步的
//接收promise的结果 是异步的

//Promise的状态一经修改  无法改变
let promise=new Promise(function(){
    
    //resolve('成功');//修改为成功fulfilled
    
    //rejected('失败');//修改为失败	rejected
    
    var successData={
        status:200,
        data:'成功获取数据'
    }
    var errorData={
        status:500,
        data:'服务器内部产生错误'
    }
   resolve(successData);//fulfilled  成功
});

//接收Promise的结果 使用then()

//then()方法中，接收两个函数作为参数，第一个函数接收成功的结果，第二个接受失败的结果

//第一种写法
promise.then(function(res){
    console.log('res:',res)
},function(){
    console.log('error:',error)
})
console.log(promise);

//第二种方法
promise.then((res)=>{
    console.log('res:',res);
},(error)=>{
    console.log('error',error);
})
console.log(promise)

//第三种方法
//then()只写结束成功的函数，catch()捕获异常的结果
//promise.then() 是异步的
promise.then(res=>{
    console.log('res:',res);
}).catch(error=>{
    console.log('error',error);
})
console.log(promise);
```

```js
//Promise 新建后就会立即执行
let promise=new Promise(function(resolve,reject){
    console.log('111');
    resolve();
});
promise.then(function(){
    console.log('222');
});
console.log('333');
//111,333,222
```

```js
//promise的then()	也是一个promise对象
let p1=new Promise((resolve,reject)=>{
    resolve('p1的成功');
})

let p2 = p1.then(res=>{
    console.log('res');
    //promise的then方法 也是一个promise对象
    //如果想修改状态 return '值'	===》resolve('值');
    //失败状态	throw('值')抛出一个异常 ===》 reject('值');
    return '成功了'
})
console.log("p2:",p2);

let p3=p2.then(res=>{
    console.log('p3内部')
    throw '失败了'
})
console.log('p3:',p3)
```

```js
//promise的then()	也是一个promise对象
    //如果想修改状态 return '值'	===》resolve('值');
    //失败状态	throw('值')抛出一个异常 ===》 reject('值');
new Promise((resolve,reject)=>{
    resolve('p1的成功');
}).then(res=>{
    console.log('res');
    return '成功了'
}).then(res=>{
    console.log('res')
    throw '失败了'
}).then(res=>{
    
}).catch(error=>{
    console.log(error)
})
```

#### promise加载图片

```js
let loadImg=function(imgUrl)=>{
    return new Promise((resolve,reject)=>{
        let img = new Image();
        img.src = imgUrl;
        img.onload=()=>{
            resolve(img)
        }
        img.onerror = (error)=>{
            reject(error)
        }
    })
}
imgUrl='http://********';
imgUrl2='http://********';
imgUrl3='http://********';
loadImg(imgUrl).then(res=>{
    console.log(res)
  document.documentElement.appendChild(res);
}).catch(error=>{
    throw error;
});

loadImg(imgUrl2).then(res=>{
    console.log(res)
  document.documentElement.appendChild(res);
}).catch(error=>{
    throw error;
})

loadImg(imgUrl3).then(res=>{
    console.log(res)
  document.documentElement.appendChild(res);
}).catch(error=>{
    throw error;
})


//then()	catch()		all()
Promise.all([
    loadImg(imgUrl),
    loadImg(imgUrl2),
    loadImg(imgUrl3)
]).then(res=>{
    console.log(res);
    for(let item of res){
        document.documentElement.appendChild(item);
    }
}).catch(error=>{
    console.log(error);
})
```

### async&await

基本用法

async关键字，用来修饰函数，把这种函数称之为async函数，async修饰的函数，就是一个promise对象

async是es7中，引入的，一个用于异步编程的一种解决方案；

async函数返回一个promise对象，可以使用then方法添加回调函数。

async函数内部return语句返回的值（相当于修改promise的状态为成功的状态，并返回结果），会成为then方法回调函数的参数

```js
function fn(){}
console.log(fn());

//使用async修饰的函数	就是一个promise对象
//async 函数内部 return 值，就相当于 resolve(值);成功的状态
async function fn1(){
    //return '成功';
    throw '异常，失败，报错';
    //async内部放await 直接取promise的结果
}
console.log(fn1());//Promise

fn1().then(res=>{
    console.log(res);
}).catch(error=>{
    console.log(error)
})
```

#### await

await命令与async配合使用，正常情况下，await命令后面是一个Promise对象，返回该对象的结果，如果不是Promise对象，就直接返回对应的值。

1、await是一个关键字，用来修饰promise对象

2、await可以直接取到promise对象成功状态的返回值

3、await必须写在async函数内部【async是爹，await是儿子】

4、await后面如果跟的不是promise，就直接是一个结果，就相当于直接取到了await后面的值

5、await是异步的，async函数运行到await的时候，直接跳出，执行同步操作。

如果函数内使用了await外层函数就必须要用async修饰

```js
let promise =new Promise((resolve,reject)=>{
resolve('成功了......')
})

promise.then(res =>{
console.log(res);
}).catch(error=>{
console.log(error);
})
```

```js
let getResult=async()=>{
let result=await new Promise((resolve,reject)=>{
resolve('成功了......');
reject('错误了');
})
console.log(result);
}
getResult();
```

```js
//await是异步的，async函数运行到await的时候，直接跳出，执行同步操作。 await 后面的内容  全部都是异步的  在当前函数内
console.log('0')
let getResult=async()=>{
console.log('1')
let result=await '2'
})
console.log(result);
console.log('3')
}
getResult();
console.log('4')
```

```js
async function fn3(){
let res = await 123;
console.log('函数内部'+res);
return res;
}
//调用执行一次，then 执行一次
fn3().then(res=>{
console.log('------------');
console.log(res);

//log 结果
//函数内部的 123
//-------------
//123

})
```
Fetch API
fetch 基于 promise
默认是 get 方式
提供了全局 fetch()方法，该语法提供了一种简单，合理的方式来跨网络异步获取资源。这种功能以前是使用 XMLHttpRequest 实现的。Fetch 提供了一个更理想的替代方案

```js
fetch('http://localhost:4000?name=三体').then(res=>{
//返回的是服务端的响应，不是真正的数据;
//但是，我们要获取的数据，就要 使用一个方法 res.json;
//console.log(res)
return res.json();
})
```
