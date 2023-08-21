## 初识Vue

### vue介绍

> Vue,js是目前最流行的、国产的前端MVVM框架
>
> > 框架:封装与业务无关的重复代码,形成框架
> >
> > 框架的优势:提升开发效率,提高代码重用性,是前端开发变得更简单
> 
> 渐进式JavaScript框架:
>
> > 可以由浅入深,有简单到复杂的使用vue.js
> >
> > 渐进式意味着你可以将Vue作为你的应用的一部分嵌入其中,带来更丰富的交互体验
>
> 作者是尤雨溪(中国人),前Google员工
>
> GitHub账号：https://github.com/yyx990803
>
> 官方入门：https://cn.vuejs.org/
>
> vue 2.0API 文档：https://v2.cn.vuejs.org/
>
> vue3.0 API 文档：https://www.vue3js.cn/docs/zh/
>
> GitHub 库：https://github.com/vuejs/vue

### 历史由来

​		尤雨溪谈Vue.js :“我在 Google 的工作需要在浏览器上进行大量原型设计，于是我想要尽快获得有形的东西。当时有些项目使用了 Angular。Angular提供了一些用数据绑定和数据驱动来处理 DOM的方法，所以你不必自己碰DOM。它也有一些副作用，就是按照它规定的方式来构建代码。对于当时的场景而言实在是太重了。
​		我想，我可以只把我喜欢的部分从Angular中提出来，建立一个非常轻巧的库，不需要那些额外的逻辑。我也很好奇Angular的源码到底是怎么设计的。我最开始只是想着手提取 Angular 里面很小的功能，如声明式数据绑定。Vue 大概就是这么开始的。

​		用过一段时间之后，我感觉我做的东西还有点前途，因为我自己就很喜欢用。于是我花了更多的时间把它封装好，取了一个名字叫做Vue.js 。

​		2014年 2月，我第一次将它作为实际的项目发布在 Github 上，并把链接发送到了 Hacker News 上，它就被顶到了首页，然后它在首页待了好几个小时。后来，我写了一篇文章，分享了Vue 第一周的使用数据以及我的感受。那是我第一次看见这么多人在 Github 上为一个项目打星星。我当时一个星期收获了好几百个星星,整个人都激动坏了。

### Vue.js优势

> 体积小,压缩后80k
>
> 更高的运行效率:基于虚拟DOM,一种可以预先通过JavaScript进行各种计算,把最终的DOM操作计算出来并优化的技术,由于这个DOM操作属于预处理操作,并没有真是的DOM,所以叫做虚拟DOM
>
> 双向数据绑定:让开发者不用再去操作DOM对象,把更多的精力投入到业务逻辑上;
>
> 生态丰富、学习成本低、被广泛的应用于web端、移动端、跨平台应用开发；市场上拥有大量成熟、稳定的基于vue.js的UI框架、常用组件！拿来即用实现快速开发！对初学者友好、入门容易、学习资料多

### MVC框架

MVC全名是Model View Controller，是模型Model——视图view——控制器Controller的缩写，一种软件设计典范，用一种业务逻辑、数据、界面侠士分离的方法组织代码，将业务逻辑聚集到一个部件里面，在改进和个性化定制界面及用户交互的同时，不需要重新编写业务逻辑。MVC被独特的发展起来用于映射传统的输入、处理和输出功能在一个逻辑的图形化用户界面的结构中。

### MVC模式的意思是，软件可以分成三个部分

> 模型(Model):数据保存
>
> 视图(View):用户界面
>
> 控制器(Controller):业务逻辑

```
View 传送指令到Controller
Controller完成业务逻辑后,要求Model改变状态
Model将新的数据发送到View,用户得到反馈
所有的通信都是单向的
```



### MVVM框架

MVVM是Model-view-viewModel的简写。它本质上就是MVC的改进版。就是将其中的view的状态和行为抽象化，让我们将视图UI和业务逻辑分开

MVVM有Model，ViewViewModel三部分构成，Model层代表数据模型，也可以在Model中定义数据修改和操作的业务逻辑；View代表UI组件，他负责将数据模型转换成UI展现出来，ViewModel是一个同步View和Model的对象

在MVVM架构下，View和Model之间并没有直接的联系，而是通过ViewModel进行交互，Model和ViewModel之间的交互是双向的，因此View数据的变化会同不懂啊Model中，而Model数据的变化也会立即反映到View上

ViewModel通过双向数据绑定View层和Model层连接了起来，而View和Model之间的同步工作完全是自动的，无需人为干涉，因此开发者只需关注业务逻辑，不需要手动操作DOM，不需要关注数据状态

### MVVM的优势

数据驱动页面

> 低耦合：MVVM模式中，数据是独立于UI的，ViewModel只负责处理和提供数据，UI想怎么处理数据都由UI自己决定，ViewModel不涉及任何和UI相关的事，既是空间改变，ViewModel几乎不需要更改任何代码，专注自己的数据处理就可以了
>
> 自动同步数据：ViewModel通过双向数据绑定吧View层和Model层连接了起来，View和Model这两者可以自动同步。程序员不需要手动操作DOM，不需要关注数据状态的同步问题，MVVM统一管理了复杂的数据状态维护（vue是以数据驱动视图）
>
> 可重用性：你可以把一些视图逻辑放在一个ViewModel里面，让很多View重用这段逻辑。
>
> 独立开发：开发人员可以专注于业务逻辑和数据的开发（ViewModel），设计人员可以专注于页面设计。
>
> 可测试：ViewModel里面是数据和业务逻辑，View中关注的是UI，这样的测试是很方便的，完全没有彼此的依赖，不管是UI的单元测试韩式业务逻辑的单元测试，都是低耦合的

二者区别

MVC和MVVM其实区别并不大。都是一种设计思想

>MVC中Controller演变成MVVM中的ViewModel
>
>MVVM通过数据来驱动视图层的显示而不是节点操作；vue是通过数据来驱动视图
>
>MVC中Model和View是可以直接打交道的，造成Model层和View层之间的耦合度高。而MVVM中Model和View不直接交互，而是通过中建桥梁ViewModel来同步的；MVC数据单向传递，MVVM数据双向绑定
>
>MVVM主要解决了：MVC中大量的DOM 操作使页面渲染性能降低，加载速度变慢，影响用户体验

### Vue起步

下载vue.js库

https://github.com/vuejs/vue/tree/2.6

解压压缩包

找到dist目录下的vue.js或者vue.min.js

此时以vue.js为例

```html
<!DOCTYPE html>
<html lang="en">

    <head>
        <meta charset="UTF-8">
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <title>Vue</title>
        <link rel="icon" href="./images/favicon.ico">
        <link rel="stylesheet" href="./css/reset.css">
    </head>

    <body>
        <-- 第一步创建View视图,Vue容器 -->
        <div id="app">
            
            <-- 第四步解析vue实例data中的数据 {{}}表示此范围内都是vue解析出来的 -->
            <h1>{{msg}}</h1>
        </div>
    </body>

</html>
<-- 第二步引入vue.js -->
<script src="./js/vue.js"></script>
<script>
    //第三步实例化vue对象,创建vue实例
    let vue = new Vue({
        
        //el 选择器
        el: '#app',
        
        //存放数据
        data: {
			msg:'Hello World'
        },
        
        //方法
        methods: {

        }
    })
</script>
```

> Do not mount Vue to<html>or<body> - mount to normal elements instead.
>
> 不要将Vue挂载到<html>或<body>元素上

### Vue差值表达式概述

> 什么是差值表达式
>
> > 使用双大括号来包裹js代码构成插值表达式
>
> 插值表达式用来做什么
>
> > 将双大括号中的数据替换成对应属性值进行展示
>
> 双大括号语法
>
> > 也叫模版语法,Mustache语法
> > 
> > Vue.js使用了基于HTML的模版语法,允许开发者声明式地将DOM绑定至底层Vue实例的数据。所有Vue.js的模版都是合法的HTML所以能被遵循规范的浏览器和HTML解析器解析
>
> 插值表达式中可以写入哪些内容
>
> > JSON数据
>>
> > 数字
>>
> > 字符串
>>
> > js表达式

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <!-- 第一步：引入vue -->
    <script src="./vue.js"></script>
</head>

<body>
    <!-- 第二步 创建视图层 -->
    <div id="box">{{msg}}
        <ul>
            <li>{{obj.name}}</li>
            <li>{{obj.age}}</li>
            <li>{{'010101'}}</li>
            <!-- 转为了二进制 -->
            <li>{{0101}}</li>

            <!-- 可以调用函数  但不能定义函数 -->
            <li>{{fn()}}</li>

            <!-- 可以写表达式 -->
            <li>{{num>10?'是':'否'}}</li>
        </ul>
    </div>
  

</body>

</html>

<script>
    // 第三步 通过vue实例化一个 vue对象
    const vm = new Vue({
        el: '#box',
        data: {
            msg: 'helloVue',
            num:10,
            obj:{
                name:'老陈',
                age:'18'
            }
        },
        methods:{
            fn(){
                return '小晨晨';
        }
        }
    });
    //第四步 使用数据
//将 data 中变量 msg 放在 #box内的双花括号内	
//修改 data 中的 msg，会同步显示在页面中
</script>
```

- 注意

  - 避免在双括号中使用复杂表达式(或者js语句)

  - ```js
    <!-- 这是语句，不是表达式 -->
    {{ var a = 1 }}
    
    <!-- 流控制也不会生效，请使用三元表达式 -->
    {{ if (ok) { return message } }}
    ```

### 数据双向绑定原理分析

底层原理实现后面课程讲到

- DOM监听
  - 视图层发生变化，DOM监听到之后，会传到逻辑层进行处理
- 数据绑定
  - 逻辑层把数据处理完成之后，通过数据绑定，把处理后的结构返回给视图层



### 学员操作—制作Vue.js 起步

需求说明
引入vue.js库
创建 view 视图
通过vue实例化一个 vue对象
将 data 中变量 msg 放在 #box内的双花括号内,最后显示在浏览器中

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>hellworld</title>
</head>
<body>
    <div id="box">
      <h1>{{msg}}</h1> 
    </div>
</body>
</html>
<script src="./vue.js"></script>
<script>
    const vm = new Vue({
        el:'#box',
        data:{
            msg:'hello,world'
        }
    })
</script>
```



### 学员操作—制作倒序字符串

需求说明
使用插值表达式完成右图效果，将“hello”转为“olleh”
调用原生的JavaScript方法字符串分割、数组翻转等

方法1：表达式

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>字符串反转</title>

    <script src="./vue.js"></script>
</head>
<body>
    <div id="con"><h1>{{msg}}转为{{msg.split('').reverse().join('')}}</h1></div>
</body>
</html>

<script>
    const vm = new Vue({
        el:'#con',
        data:{
            msg:'hello'
        }
    })
</script>
```



方法2：使用方法

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>字符串反转2</title>
</head>
<body>
    <div id="box">
        <h1>{{msg}}反转{{fn()}}</h1>
    </div>
</body>
</html>

<script src="./vue.js"></script>

<script>
    const vm = new Vue({
        el:'#box',
        data:{
            msg:'Hello'
        },
        methods:{
            fn(){
                return this.msg.split('').reverse().join('');
            }
        }
    });

</script>
```



### [计算属性](https://cn.vuejs.org/v2/guide/computed.html#计算属性)



模板内的表达式非常便利，但是设计它们的初衷是用于简单运算的。

在模板中放入太多的逻辑会让模板过重且难以维护。

如上案例。所以，对于任何复杂逻辑，你都应当使用**计算属性**（computed）。

可以把一个函数声明为属性，通过调用属性，达到调用函数的目的



```js


var vm = new Vue({
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
    }
  }
})

你可以像绑定普通 property 一样在模板中绑定计算属性。Vue 知道 vm.reversedMessage 依赖于 vm.message，因此当 vm.message 发生改变时，所有依赖 vm.reversedMessage 的绑定也会更新。

我们可以将同一函数定义为一个方法而不是一个计算属性。两种方式的最终结果确实是完全相同的。然而，不同的是计算属性是基于它们的响应式依赖进行缓存的。只在相关响应式依赖发生改变时它们才会重新求值。这就意味着只要 message 还没有发生改变，多次访问 reversedMessage 计算属性会立即返回之前的计算结果，而不必再次执行函数。
#计算属性默认只有 getter，不过在需要时你也可以提供一个 setter
演示案例-计算属性steer
```

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>字符串反转2</title>
</head>
<body>
    <div id="box">
        <!-- 调用计算属性时  不需方法  只用调用属性名即可 -->
        <h1>{{msg}}反转{{reverseMsg}}</h1>
    </div>
</body>
</html>

<script src="./vue.js"></script>

<script>
    const vm = new Vue({
        el:'#box',
        data:{
            msg:'Hello'
        },
    //    计算属性
        computed:{
            reverseMsg:function(){
                return this.msg.split('').reverse().join('');
            }
        }
    });

</script>
```

计算属性默认getter

演示setter:

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>字符串反转2</title>
</head>

<body>
    <div id="box">
        <!-- 调用计算属性时  不需方法  只用调用属性名即可 -->
        <h1>{{msg}}反转{{reverseMsg}}</h1>
        <!-- 调用 属性=值  表示调用setter方法 -->
        <h1>{{msg}}反转{{reverseMsg='laochen'}}</h1>
    </div>
</body>

</html>

<script src="./vue.js"></script>

<script>
    const vm = new Vue({
        el: '#box',
        data: {
            msg: 'Hello'
        },
        //    计算属性
        computed: {
            reverseMsg: {
                get: function () {
                    return this.msg.split('').reverse().join('');
                },

                set: function(nevValue){
                    this.msg=nevValue;
                }
            }
        }
    });

</script>
```