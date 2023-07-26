## JavaScript继承

一个对象去通过另一个对象，拥有自己没有的方法和属性，这个过程我们称之为继承

大白话：

张三跟着张三丰学习太极剑，张三继承张三丰的太极剑。继承以后张三拥有太极剑技能张三丰依然拥有本身的技能

### 原型链继承

对象.prototype=new 被继承的对象;

```js
function GaoBW(){
    this.car='兰博基尼';
    this.house='温哥华山庄别墅1001号'
}
function Father(name,age){
    this.name=name;
    this.age=age;
}
Father.prototype=new GaoBW();
var son=new Father('李四',18);
console.log(son.name);
console.log(son.age);
console.log(son.car);
console.log(son.house)

//弊端：存在继承紊乱，son通过Father创建出来的。但是继承过后，会发现，son的构造函数，不在Father，而是GaoBW
console.log(son.constructor)//结果是GaoBW，发现自己的亲爹不再是亲爹

//因此需要手动修改继承链
Father.prototype.consttructor=Father
console.log(son.constructor)//此时为Father
```

### 原型链继承-直接继承prototype

由于GaoBW对象中，不变的属性都可以直接写入GaoBW.prototype。所以，可以让Father()跳过GaoBW，直接继承GaoBW.prototype

```js
function GaoBW(){}

GaoBW.prototype.house='温哥华山庄别墅1001号';
GaoBW.prototype.car='兰博基尼';

function Father(name,age){
    this.name=name;
    this.age=age;
}
//不再继承GaoBW 直接继承GaoBW的原型对象 少了一个new的过程
//依然存在继承紊乱
Father.prototype=GaoBW.prototype;
//手动修改继承链
Father.prototype.constructor=Father;
console.log(son.constructor)//Father

var son=new Father('李四',18);
console.log(son.name);
console.log(son.age);
console.log(son.car);
console.log(son.house)

//另一个弊端
Father.prototype.car='五菱宏光';
var GaoBW=new GaoBW();
console.log(GaoBW.car);//五菱宏光;
```

优点：效率比较高（不用执行和GaoBW的实例了）

缺点：1、依然会产生继承链紊乱，需要手动修改继承链

​			2、因为Father的原型对象指向了GaoBW的原型对象，所以Father修改原型对象的值，GaoBW原型对象的值也被修改了，这样就等于继承别人的财富，还随意的更改别人的内容，太霸道，不合理

### 利用空对象继承

```js
function GaoBW(){}

GaoBW.prototype.house='温哥华山庄别墅1001号';
GaoBW.prototype.car='兰博基尼';

function Null(){}

Null.prototype=GaoBW.prototype;

function Father(name,age){
    this.name=name;
    this.age=age;
}

var son=new Father('李四',18);
console.log(son.name);
console.log(son.age);
console.log(son.car);
console.log(son.house)

Father.prototype=new Null();
Father.prototype.constructor=Father;

Father.prototype.car='五菱宏光';
var GaoBW=new GaoBW();
console.log(GaoBW.car);//兰博基尼
```

##### 把继承的过程封装为函数

```js
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <script>
        function GaoBW(){}
        GaoBW.prototype.car = '兰博基尼';
        GaoBW.prototype.house = '温哥华山庄别墅1001号';

        function Fater(n,a){
            this.a=a;
            this.n=n;
        }
        // 封装函数
        function extence(parent,child){
            function F(){}
            F.prototype= parent.prototype;
            child.prototype = new F();
            child.prototype.constructor = child;
        }
        
        extence(GaoBW,Fater);
     
        var tc_ = new Fater('tc',20);
        console.log(tc_.car,tc_.house)

        Fater.prototype.car = '五菱';
        var gao_ = new GaoBW();
        console.log(gao_.car);//兰博基尼
 
    </script>
</body>
</html>
```



### 构造函数的绑定

即在子类型构造函数的内部调用父类型构造函数

通过call()或apply()方法

构造函数实现对实例属性的继承，完成不了对父类原型对象的继承

#### call

语法：

a.call(b,agr1,agr2);

表示b继承a	agr1,agr2是a的参数

```js
        function Father(car,house){
            this.car=car;
            this.house = house;
        }

        function Son(name,age){
            this.name=name;
            this.age = age;
            //son 继承 father
            //a.call(b，ag1,ag2);
            //表示b继承a,ag1，ag2是a的参数
            Father.call(this,'汤臣一品','大众捷达');
        }
        var son_ = new Son('小宝',20);
        console.log(son.house);
        console.log(son.car);
```

#### apply:

语法：

a.apply(b，[ag1,ag2]);

表示b继承a,ag1，ag2是a的参数

```js
        function Father(car,house){
            this.car=car;
            this.house = house;
        }

        function Son(name,age){
            this.name=name;
            this.age = age;
            //son 继承 father
            //a.call(b，ag1,ag2);
            //表示b继承a,ag1，ag2是a的参数
            Father.apply(this,['汤臣一品','大众捷达']);
        }
        var son_ = new Son('小宝',20);
        console.log(son.house);
        console.log(son.car);
```

#### 组合继承

构造函数继承，只能继承构造函数内部的属性方法，无法继承其原型对象的属性方法

```js
    function Father(house, car) {
        this.car_ = car;
        this.house_ = house;
    }

    Father.prototype.say = function(){
        console.log('我是祖宗');
    }

    function Son(n,a){
        this.name = n;
        this.age = a;
        // Father.call(this,'汤臣一品','劳斯莱斯');
        Father.apply(this,['汤臣一品','哈罗单车']);
    }


    var xw = new Son('小王',30);
    console.log(xw.car_,xw.house_,xw.name,xw.age);
    console.log(xw.constructor);

    xw.say();// 无法显示  
```

也叫伪经典继承
将原型链继承和构造函数继承组合在一块
原型链实现对原型属性和方法的继承
借用构造函数实现对实例属性的继承

```js
    function Father(house, car) {
        this.car_ = car;
        this.house_ = house;
    }

    Father.prototype.say = function(){
        console.log('我是祖宗');
    }

    function Son(n,a){
        this.name = n;
        this.age = a;
        // Father.call(this,'汤臣一品','劳斯莱斯');
        Father.apply(this,['汤臣一品','哈罗单车']);
    }

    Son.prototype = new Father();// 把子类原型指向父类，即可继承父类的原型对象的属性方法
    Son.prototype.constructor = Son;//手动更改原型对象

    var xw = new Son('小王',30);
    console.log(xw.car_,xw.house_,xw.name,xw.age);

    console.log(xw.constructor);// Son

    xw.say();// 我是祖宗
```

### 原型链

```js
        function Person(){

        }

        Person.prototype.sayname=function(){
            console.log('我是person原型对象的sayname')
        } 

        Object.prototype.sayname = function(){
            console.log('我是object原型对象的sayname')
        } 

        var p1 = new Person();

        p1.sayname = function(){
            console.log('我是person实例对象对象的sayname')
        }

        p1.sayname();
```

大白话：



> 就是你有个对象，你丈母娘问你要20W彩礼，你自己拿不出来你没有（对象本身没有属性），丈母娘让你问你爸爸（原型对象）要，如果你爸爸也没有，你爸爸就得问你爸爸的爸爸也就是你爷爷要（原型对象的原型对象，这里的第一个原型对象实质上成了一个实例对象，因为你爸爸在你爷爷那里永远是儿子），如果你爷爷也没有就继续往上要……如此反复，实在拿不出来(null)，丈母娘大手一挥，拿不出来就不嫁了（直到为null时停止）；

三个面试题：

1、js实现继承的几种方法

2、call 和apply的区别

3、谈谈你对原型链的理解