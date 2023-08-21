---
typora-root-url: images
---



# 第五章：Proxy(代理拦截操作)



Proxy 可以理解成，在目标对象之前架设一层“拦截”，外界对该对象的访问，都必须先通过这层拦截，因此提供了一种机制，可以对外界的访问进行过滤和改写。Proxy 这个词的原意是代理，用在这里表示由它来“代理”某些操作，可以译为“代理器”。

```js
ES6 原生提供 Proxy 构造函数，用来生成 Proxy 实例。
var proxy = new Proxy(target, handler);
Proxy 对象的所有用法，都是上面这种形式，不同的只是handler参数的写法。其中，new Proxy()表示生成一个Proxy实例，target参数表示所要拦截的目标对象，handler参数也是一个对象，用来定制拦截行为。
let obj = {
    sex:'man'
}
let myproxy  = new Proxy(obj,{
    get(){},
    set(){},
    has(){},
    delteProperty(){}
    ...
});
```



```
let pro_ = new Proxy(target,handler);
target:目标对象   handler:拦截操作
```



被proxy代理的目标对象，所有的访问都需要经过proxy实例来完成

不能直接访问目标对象，否则，就是绕过了proxy代理操作了



```js
let Person = {
        name: '小陈',
        age: 25,
        address: '河南郑州',
        money: 987888
    }

    //    创建prox拦截代理
    // let proxy_ = new Proxy(target,handler);
    // target：要代理的对象  handler:拦截操作

    let proxy_ = new Proxy(Person,{
        // 目标对象、 属性名 和  proxy 实例本身
        get(target,prokey,self){
            console.log(target);
            console.log(prokey);
            console.log(self);
        }
  
    });

    proxy_.money;
```



完整的get操作，t，其他的正常访问

```js
  let Person = {
        name: '小陈',
        age: 25,
        address: '河南郑州',
        money: 987888
    }

    //    创建prox拦截代理
    // let proxy_ = new Proxy(target,handler);
    // target：要代理的对象  handler:拦截操作

    let proxy_ = new Proxy(Person,{
        // 目标对象、 属性名 和  proxy 实例本身
        get(target,prokey,self){
            if(prokey == 'money'){
                throw '余额为***';//只要来获取money属性值，人为的抛出一个错误
              
            }
            //访问其他属性正常的返回
            return target[prokey];//target.prokey
        }
    });

    // proxy_.money;// Uncaught 余额为***
    // console.log(proxy_.name);//小陈
    console.log(proxy_.address);//河南郑州
```



## Proxy 支持的拦截操作一览，一共 13 种。



- **get(target, propKey)**：拦截对象属性的读取，比如`proxy.foo`和`proxy['foo']`。



```js
  let Person = {
        name: '小陈',
        age: 25,
        address: '河南郑州',
        money: 987888
    }

    //    创建prox拦截代理
    // let proxy_ = new Proxy(target,handler);
    // target：要代理的对象  handler:拦截操作

    let proxy_ = new Proxy(Person,{
        // 目标对象、 属性名 和  proxy 实例本身
        get(target,prokey,self){
            if(prokey == 'money'){
                throw '余额为***';//只要来获取money属性值，人为的抛出一个错误
              
            }
            //访问其他属性正常的返回
            return target[prokey];
        }
    });

    // proxy_.money;// Uncaught 余额为***
    // console.log(proxy_.name);//小陈
    console.log(proxy_.address);//河南郑州
```



- **set(target, propKey, value)**：拦截对象属性的设置，比如`proxy.foo = v`或`proxy['foo'] = v`，返回一个布尔值。

   例：如果修改金额，不能修改，其他person属性正常修改



```js
<script>
    let Person = {
        name: '小陈',
        age: 25,
        address: '河南郑州',
        money: 9878880
    }

    let proxy = new Proxy(Person, {
        set(target,prokey,value){
            if(prokey === 'money'){
                console.log('老子的钱不容侵犯');
                return;
            }
            target[prokey] = value;
        }
    })

    //金额部分无法完成修改，因为被拦截了，其他正常修改
    proxy.money = 300;
    proxy.name = '张三';
    console.log(proxy);//name: "张三", age: 25, address: "河南郑州", money: 987888
    console.log(Person);//name: "张三", age: 25, address: "河南郑州", money: 987888
</script>
```

```js
<script>
    // 在进行设置的时候， 如果对象中没有要设置的属性名 则显示属性名undefind
    let Person = {
        name: '小陈',
        age: 25,
        address: '河南郑州',
        money: 987888
    }

    let proxy = new Proxy(Person, {
        set(target, prokey, value) {
            if (!(prokey in target)) {
                throw `${prokey} is not defind`;
            } else if (prokey === 'money') {
                throw '老子的钱不容侵犯';
            } else {
                target[prokey] = value;
            }

        }
    })


    // proxy.money = 300; //报错
    // proxy.aa = 'hahah'; //报错
    proxy.name = 'zhangsna';//正常修改
    console.log(proxy);

</script>
```



- **has(target, propKey)**：拦截`propKey in proxy`的操作，返回一个布尔值。

  `propKey in proxy` 判断属性是否在对象中

```js
<script>
    //在person对象中添加vip属性  值是true
    // 在别人访问的时候  访问是否具备vip属性的时候 要拦截一下 永远返回false 
    let Person = {
        name: '小陈',
        age: 25,
        address: '河南郑州',
        money: 987888,
        vip:true
    }

    let proxy = new Proxy(Person,{
        has(taget,prokey){
            if(prokey == 'vip'){
                return false;
            }
            return prokey in taget;
        }
    })

    console.log('vip' in proxy);//false
    console.log('name' in proxy);//true
    console.log('address' in proxy);//true
    console.log('add' in proxy);//false
</script>
```



- **deleteProperty(target, propKey)**：拦截`delete proxy[propKey]`的操作，返回一个布尔值。

```js
<script>
    // 做删除拦截  当删除money的时候，返回你无权删除
    let Person = {
        name: '小陈',
        age: 25,
        address: '河南郑州',
        money: 987888,
        vip: true
    }

    let proxy = new Proxy(Person, {
        deleteProperty(target, prokey) {
            if(prokey == 'money'){
                throw '你无权更改我的钱';
            }
            //正常删除
            delete target[prokey];
        }
    })

    // delete proxy.money;//报错  你无权更改我的钱
    delete proxy.name;//删除了姓名
    console.log(proxy);

</script>
```





#### 对象.属性  和 对象[属性的区别]

```js
    var obj = {
        name:'老陈',
        age:18,
        address:'河南郑州'
    };

    for(let i in obj){
        console.log(i); //name age address

        // console.log(obj.i); //undefined 因为此时的i 没有在obj对象中声明，即obj没有i这个属性
        console.log(obj[i]);// 此时的i 是动态的，通过一个叫i的变量名去取i对应的值
    }
```



get

```js
    //target:目标对象,要代理的对象   handler:拦截操作
    // let proxy=new Proxy(target,handler);

    let person = {
        name: '小李',
        age: 18,
        address: '河南郑州',
        money: 99999999,
    }

    //创建proxy拦截代理
    let proxy = new Proxy(person, {
        //拦截对象属性的读取,比如proxy.name和proxy['name'];
        get(target, prokey, self) {
            console.log(target);
            console.log(prokey);
            console.log(self);
        },
        get(target, prokey, self) {
            if (prokey == "money") {
                throw '余额***'//当访问money时人为的抛出一个异常
            }
            //访问其他属性正常返回
            return target[prokey];//target.prokey
        }
    })

    // proxy.money;//余额***
    console.log(proxy.name)//小李
    console.log(proxy.address);//河南郑州
```



set

```js
    let person = {
        name: '小李',
        age: 18,
        money: 99999999,
        address: '河南郑州',
    }
    let proxy = new Proxy(person, {
        set(target, prokey, value) {
            if (!(prokey in target)) {
                throw '没jb这配置';
            } else if (prokey === 'money') {
                throw '老子的钱不准动';
                return;
            } else {
                target[prokey] = value;
            }
        }
    })

    // proxy.money = 10000;
    proxy.address = "河南";
    console.log(proxy.address);//河南
    console.log(person);//name:小李,age:18,money:99999999,address:河南
    proxy.hoby = 'play';//没有这项配置
```



has

```js
    let person = {
        name: '小李',
        age: 18,
        money: 99999999,
        address: '河南郑州',
        vip: '是',
    }

    let proxy = new Proxy(person, {
        //拦截prokey in proxy的操作,返回一个布尔值
        // prokey in proxy 判断属性是否在对象中
        has(target, prokey) {
            if (prokey === 'vip') {
                throw '不是'
                return false;
            } else if (prokey === 'money') {
                throw '***********你猜多少'
            }
            return prokey in target;
        }
    })

    // console.log('vip' in proxy);//不是
    // console.log('money' in proxy);//***********你猜多少
    console.log('name' in proxy);//true
```



deleteProperty

```js
    let person = {
        name: '小李',
        age: 18,
        money: 99999999,
        address: '河南郑州',
        vip: '是',
    }

    let proxy = new Proxy(person, {
        deleteProperty(target, prokey) {
            if (prokey === 'money') {
                throw '你无权更改我的money';
            }
            //正常删除
            delete target[prokey];
        }
    })
    delete proxy.vip;//删除了vip
    console.log(proxy);
    delete proxy.money;//你无权更改我的钱
```

