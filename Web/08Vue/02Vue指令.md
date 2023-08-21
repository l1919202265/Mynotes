## Vue指令



###   什么是 Vue.js 指令

指令 (Directives) 是带有 `v-` 前缀的特殊 attribute。指令 attribute 的值预期是**单个 JavaScript 表达式**。指令的职责是，当表达式的值改变时，将其产生的连带影响，响应式地作用于 DOM。

例如：

```js
//点击toggle按钮，会显示红色方块，再次点击，红色方块消失，这里就是通过控制属性的真假，通过指令作用到红色方块上来控制方块的显示隐藏
<button v-on:click="isaaa = !isaaa">toggle</button>
<div class="block" v-show="isaaa"></div>
```

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
   
    <title>v-show 展示图片</title>
    
    <style>
        .red_div{
            width: 200px;
            height: 200px;
            background-color: rgb(250, 116, 116);
        }
    </style>
</head>

<body>
    <div id="box">
        <button v-on:click = 'fn'>点击切换</button>
        <div class="red_div" v-show='isShow'></div>
    </div>


</body>

</html>

<script src="./vue.js"></script>

<script>
    const vm = new new Vue({
        el: '#box',
        data:{
            isShow:false
        },
        methods: {
            fn(){
                this.isShow = !this.isShow;
            }
        }
    })
</script>
```



### Vue.js 指令的书写规范

```js
//书写位置：任意 HTML 元素的开始标签内
<p v-if="seen">现在你看到我了</p>

//注意：一个开始标签内可写入多个指令，多个指令间使用空格分隔
<a href="javascript:;" :class="{active:timeflag}" @click="queryAll('time')">全部</a>

```





### 指令用法 

- 代码演示所有指令用法
- 不在文档中写案例，学习时，查阅官方手册或上课案例。



### v-text:

v-text相当于 元素的innerText();

设置元素的内容，同时会覆盖元素内的内容

```html
<body>
    <div id="box">
        <!-- 结果： 老李! -->
        <p v-text = 'msg+"!"'>哈哈</p>
    </div>
</body>
</html>

<script src="./vue.js"></script>
<script>

    var vm = new Vue({
        el:'#box',
        data:{
            message:'老陈',
            msg:'老李'
        }
    })

</script>
```

### v-html:

```
v-text相当于 元素的innerText();

设置元素的内容，同时会覆盖元素内的内容
如果指令获取的数据里面有html标签，会自动解析为html样式
```

```html
<body>
    <div id="box">
        <!-- v-html 相当于元素.innserHtml -->
        <p v-html = 'message+"!"'>哈哈</p>
        <p v-text='message'></p>
    </div>
</body>
</html>

<script src="./vue.js"></script>
<script>

    var vm = new Vue({
        el:'#box',
        data:{
            message:'<h1>老陈</h1>',
            msg:'老李'
        }
    })

</script>
```



### v-show:



```tex
v-show='表达式'
可以根据表达式值的真假，来控制页面元素的显示(true）和隐藏(false)控制元素显示和隐藏
本质:就是css的display: block display:none
```

例：控制div的显示与隐藏

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>v-show</title>

    <style>
        .red{
            width: 200px;
            height: 200px;
            background-color: red;
        }
    </style>
</head>

<body>
    <div id="box">
        <!-- 要显示的div -->
        <div class="red" v-show='isShow'></div>
    </div>

</body>

</html>

<script src="./vue.js"></script>

<script>
    const vm = new new Vue({
        el: '#box',
        data: {
            isShow: true
        }
    })
</script>
```



### v-if:

v-if:根据表达值的真假,切换元素的显示和移除(操纵dom元素)

v-else-if:如果if表达式不成立，则 判断当前表达式，成立显示元素，否则移除

v-else:如果if不成立，则显示v-else绑定的daom元素。无需表达式



注意：v-if v-else-if  和 v-else中间  不能有其他的内容 必须紧密的连接在一起

```html
<body>
    <ul id="list">
        <li v-if='num>85'>离离原上草</li>
        <li v-else-if = 'num>80'>一岁一枯荣</li>
        <li v-else-if = 'num>75'>野火烧不尽</li>
        <li v-else>春风吹又生</li>
    </ul>
</body>
</html>

<script src="./vue.js"></script>
<script>
    const vm = new new Vue({
        el:'#list',
        data:{
            num:80
        }
    })
</script>
```

> v-if和v-show的区别:
>
> v-if：纯粹的元素插入和删除
>
> v-show：纯粹的css的显示和隐藏

```
//v-if与v-show区别
//v-show指令的元素始终会被渲染到HTML
//它只是简单地为元素设置CSS的style属性。当不满足条件的元素被设置style="display:none"样式
//v-if指令满足条件是，会渲染到html中，不满足条件时，是不会渲染到html中的

v-if 指令有更高的切换消耗
v-if当条件成立的时候会将元素加上，不成立的时候，就会移除dom，并且内部的指令不会执行
v-show 指令有更高的初始渲染消耗
v-show只是简单的隐藏和显示
如果需要频繁切换使用 v‐show 较好，如果在运行时条件不大可能改变 使用v‐if 较好
```



### v-for：



`v-for` 指令可以绑定数组的数据来渲染一个项目列表：

`v-for`指令需要使用item in items形式的特殊语法，
其中 items是源数据数组，而item则是被迭代的数组元素的别名，即数组中每一项的内容。



```html
<body>
    <div id="box">
        <ol>
            <li v-for="clas in classes">
                {{ clas.text }}
            </li>
        </ol>
    </div>
</body>
<script src="./vue.js"></script>
<script>
    const vm = new Vue({
        el: '#app',
        data: {
            num: 80,
            classes:[
                {text:"郭德纲相声集"},
                {text:"易中天品三国"},
                {text:"陈福国相声"},
            ]
        }
    })
</script>
```





### v-on:

```
为 HTML 元素绑定事件监听
v-on：事件名称 =‘函数名称()’
表达式可以是一个方法的名字或一个内联语句
简写语法：@事件名称 =‘函数名称()’
注：函数定义在 methods 配置项中

<button v-on:click='fn()'>toggle</button>
//v-on: 可以简写成 @
<button @click='fn()'>toggle</button>
```



```html
<body>
    <div id="box">
        <input type="button" value="v-on普通点击" v-on:click='fn'>
        <input type="button" value="v-on简写" @click='fn'>
        <input type="button" value="v-on双击" @dblclick='fn'>

        <p @click='show'>{{msg}}</p>
    </div>
    
</body>
</html>

<script src="./vue.js"></script>
<script>
    var vm = new Vue({
        el:'#box',
        data:{
            msg:'老陈真帅'
        },
        methods:{
            fn:function(){
                alert('点击成功');
            },
            show:function(){
                // 改变值
                this.msg +='呵';
                console.log(this.msg);
                
            }
        }
    })
</script>
```

```html

v-on后面可以增加修饰符
事件修饰符：
.stop：调用event.stopPropagation() 阻止冒泡
.prevent : 调用event.preventDefault() 阻止默认事件 
           e.returnValue = false; //兼容ie 
           return false;//必须放在函数代码的末尾
.self : 只当事件是从侦听器绑定的元素本身触发时才触发回调
.once:点击事件将只会触发一次

按键修饰符
.{keycode} : 只在指定键上触发回调

系统修饰键
.ctrl
.alt
.shift
.meta

.exact 修饰符 精确修饰符
举个栗子：
<input @keydown.ctrl="fn">  按下的按键中只要有ctrl即可，他可以有其他的按键
<input @keydown.ctrl.exact="fn">  有且只有按下ctrl键时，在点击，才能触发事件

鼠标按钮修饰符
.left
.right
.middle

#获取事件对象
<div class="out" @click="fn($event)">event</div>
```

#### .stop

事件修饰符阻止冒泡：

```html
<head>
    <meta charset="UTF-8">
    <title>阻止冒泡</title>

    <style>
        div{
            border: 1px solid black;
            padding: 50px;
        }
    </style>
</head>
<body>
    <div id="box" v-on:click="fn('out')">
        <div class="inner" @click.stop='fn("inner")'>

        </div>
        
    </div> 
```

```js
<script>
    const vm = new Vue({
        el:'#box',
        methods: {
            fn(v){
                alert(v);
            }
        }
    })
</script>
```

#### .prevent

事件修饰符阻止默认事件：

```html
    <style>
        div{
            width: 200px;
            height: 200px;
            background-color: red;
        }
    </style>
</head>
<body>
    <!-- .prevent  阻止默认事件 -->
    <div id="box" @contextMenu.prevent='onright("hahah")'></div>
</body>
```

```js
<script>
    const vm = new Vue({
        el:"#box",
        methods:{
            onright(v){
                alert(v);
            }
        }
    })
</script>
```



#### .self属性

 只要点击自身才会触发事件

以阻止冒泡为例

```html

    <style>
        div{
            border: 1px solid black;
            padding: 50px;
        }
    </style>
</head>
<body>
    <!-- 都添加.self -->
    <div id="box" v-on:click.self="fn('out')">
        <div class="inner" @click.self='fn("inner")'>
        </div>
    </div>
</body>
```

```js
<script>
    const vm = new Vue({
        el: '#box',
        methods: {
            fn(v) {
                alert(v);
            }
        }
    })
</script>
```



#### .once

点击事件将只会触发一次，底层中触发一次以后，立即解绑了该事件

比如给上面例子中的out添加一个.once 则只弹出一次 out

```
<div @click.self.once='cli("out")'>
```



#### 按键修饰符

在监听键盘事件时，我们经常需要检查详细的按键。Vue 允许为 `v-on` 在监听键盘事件时添加按键修饰符：

```css
<!-- 只有在 `key` 是 `Enter` 时调用 `vm.submit()` -->
<input v-on:keyup.enter="submit">

为了在必要的情况下支持旧浏览器，Vue 提供了绝大多数常用的按键码的别名：

.enter
.tab
.delete (捕获“删除”和“退格”键)
.esc
.space
.up
.down
.left
.right

举个栗子：
<input @keyup.ctrl="fn">  按下的按键中只要有ctrl即可，他可以有其他的按键
<input @keydown.ctrl.exact="fn">  有且只有按下ctrl键时，在点击，才能触发事件

```

```html
<body>
    <input id="ipt" type="text" v-on:keyup.enter="sub()">
  	//                同时按下ctrl 和 enter键
  	<input type="text" v-on:keydown.ctrl.enter="sub()">
</body>
```

```js
 const vm = new Vue({
        el:'#ipt',
        methods:{
            sub(){
                alert('提交');
            }
        }
    })
```



#### 鼠标按钮修饰符

.left
.right
.middle



```html
    <style>
        #box{
            width: 100%;
            height: 200px;
            background-color: rgb(219, 148, 148);
        }
    </style>
</head>
<body>
    <div id="box"
     @click='click_event("普通点击")'
     @click.left = 'click_event("左键点击")'
     @click.right.prevent = 'click_event("右键点击")'
     @click.middle= 'click_event("滚轮点击")'
     
     ></div>
</body>
```

```js
  const vm = new Vue({
        el:'#box',
        methods: {
            click_event(v){
                alert(v);
            }
        }
    })
```



#### 获取事件对象

$event作为参数传递，可获取当前对象

```html
<div class="out" @click="fn($event)">event</div>
```

```html
<body>
    <div id="box" v-on:click="fn($event)">div id 为box</div>
</body>

<script>
  const vm = new Vue({
        el: '#box',
        methods: {
            fn(e) {
                console.log(e);
            }
        }
    })
</script>
```

```html
同时传递当前事件 和参数
<body>
    <div id="box" v-on:click="fn($event,5)">div id 为box</div>
</body>

<script>
  const vm = new Vue({
        el: '#box',
        methods: {
            fn(e,num) {
                console.log(e);
               console.log(num);
            }
        }
    })
</script>
```



### v-bind

```html
v-bind可以在其名称后面带一个参数，参数通常是HTML元素的属性（attribute），v-bind是动态绑定指令，默认情况下自带属性的值是固定的，为了能够动态的给这些属性添加值可以使用v-bind指令
v-bind:属性名 = ‘表达式’
简写形式：v-bind可以省略，直接书写为 :属性名 = ‘表达式’
<img v-bind:src="imageSrc"> 等价于  <img :src="imageSrc">   //绑定一个属性
//绑定多个属性
<div v-bind:class="{'textColor':isColor, 'textSize':isSize}">多个样式的绑定</div>
```



### 绑定属性：

```html
<div id="box">
      <a v-bind:href="rurl">百度</a>
      <a :href="rurl">百度</a>
    </div>
```

```
 const vm = new Vue({
        el:'#box',
        data:{
            rurl:'http://www.baidu.com'
        }
    })
```



### v-bind:绑定class

```html
<div :class="{类名：布尔值}">v-bind: class</div> 
根据属性值的情况来定，是否要添加类名
```

```html
    <style>
        .active {
            width: 200px;
            height: 200px;
            background-color: red;
        }
    </style>
</head>

<body>
    <div id="box" :class="{active:bool}"></div>
</body>

```

```js
<script>
    const vm = new Vue({
        el: '#box',
        data: {
            bool: false// 布尔类型结果 决定了是否要添加类名
        },
        methods: {

        }
    })
```



可以同时绑定多个类名，也可以和静态类名同时存在

```html
<div id="box" class="aa"  :class="{active:bool,two:bool}"></div>
```

```html
const vm = new Vue({
        el: '#box',
        data: {
            bool: true
        },
        methods: {

        }
    })
```





数组形式绑定类名：

```html
<div id="box" :class=[name1,name2]>数组绑定类名</div>
```

```js
 const vm = new Vue({
        el:'#box',
        data:{
            name1:'aaa',
            name2:'bbb'
        },
        methods:{

        }
    })
```

 



```js
//对象语法
我们可以传给 v-bind:class 一个对象，以动态地切换 class：
<div v-bind:class="{ active: isActive }"></div>

<div class="static" v-bind:class="{ active: isActive, 'text-danger': hasError }"></div>

//数组语法
我们可以把一个数组传给 v-bind:class，以应用一个 class 列表：
<div v-bind:class="[activeClass, errorClass]"></div>
 data: {
  activeClass: 'active',
  errorClass: 'text-danger'
}

<div v-bind:class="[isActive ? activeClass : '', errorClass]"></div>
```







### v-bind:绑定内联样式

对象语法

```html
 <div id="box" :style="{color:xxcolor,fontSize:xxpx+'px'}">
        对象方式设置css样式
    </div>
```

```js
const vm = new Vue({
        el:'#box',
        data:{
            xxcolor:'red',
            xxpx:50
        },
        methods:{

        }
    })
```



```js
#对象语法
//v-bind:style 的对象语法十分直观——看着非常像 CSS，但其实是一个 JavaScript 对象。CSS property 名可以用驼峰式 (camelCase) 或短横线分隔 (kebab-case，记得用引号括起来) 来命名：
 <div id="box" :style="{color:xxcolor,fontSize:xxpx+'px'}">
        对象方式设置css样式
    </div>

data: {
  xxcolor: 'red',
  xxpx: 30
}


//直接绑定到一个样式对象通常更好，这会让模板更清晰：
<div v-bind:style="styleObject"></div>
data: {
  styleObject: {
    color: 'red',
    fontSize: '13px'
  }
}

#数组语法
//v-bind:style 的数组语法可以将多个样式对象应用到同一个元素上：
<div v-bind:style="[styleObject，baseStyles, overridingStyles]"></div>
```



### v-model  双向数据绑定



```
你可以用 v-model 指令在表单 <input>、<textarea> 及 <select> 元素上创建双向数据绑定。它会根据控件类型自动选取正确的方法来更新元素。尽管有些神奇，但 v-model 本质上不过是语法糖。它负责监听用户的输入事件以更新数据，并对一些极端场景进行一些特殊处理。
```

> `v-model` 会忽略所有表单元素的 `value`、`checked`、`selected` attribute 的初始值而总是将 Vue 实例的数据作为数据来源。你应该通过 JavaScript 在组件的 `data` 选项中声明初始值。

大白话： v-model会自动的将表达式的值，插入到表单对应的内容



```html
 <div id="box">
        <input type="text" value="默认数据" v-model="msg">
        <p>{{msg}}</p>
    </div>
```

```js
 const vm = new Vue({
        el:'#box',
        data:{
            msg:'v-model数据'
        },
        methods:{

        }
    })
```





#### 单个复选框

单个复选框，绑定得到布尔值：

v-model  拿到的是checked选中的值，true或者false

```html
 <div id="box">
        <input type="checkbox" v-model="checked">英雄
        <p>{{checked}}</p>
    </div>
```

```js
 const vm = new Vue({
        el:'#box',
        data:{
            checked:''
        },
        methods:{

        }
    })
```





#### 多个复选框

用v-model 接收到的值，在data中用数组接收，接收到的是值

```html
 <div id="box">
        <input type="checkbox" v-model="checkedNames" value="hreo">英雄
        <input type="checkbox" v-model="checkedNames" value="History">历史
        <input type="checkbox" v-model="checkedNames" value="music">音乐
        <input type="checkbox" v-model="checkedNames" value="movie">电影
        <p>{{checkedNames}}</p>
    </div>
```

```js
 const vm = new Vue({
        el:'#box',
        data:{
            checkedNames:[]
            // 如果想选择默认 直接在数组中写上默认的value值
            // checkedNames:['movie']

        },
        methods:{

        }
    })
```



#### 单选按钮：

```html
 <div id="box">
        <input type="radio" name="sex" value="woman" v-model="msg">女
        <input type="radio" name="sex" value="man" v-model="msg">男
        <p>{{msg}}</p>
    </div>
```

```js
 const vm = new Vue({
        el:'#box',
        data:{
            msg:""
        },
        methods:{

        }
    })
```





#### select下拉选择框

v-model 拿到的是选中选项的值

v-module 后有value属性 取的是 选中option中value的值

                 没有value属性 取的是  选中option标签内的值

```html
<div id="box">
        <select v-model="selected">
            <option>请选择</option>
            <option>A</option>
            <option>B</option>
            <option>C</option>
          </select>
          <br>
          <span>Selected: {{ selected }}</span>
     
    </div>
```

```js
  const vm = new Vue({
        el:'#box',
        data:{
            selected:''
        },
        methods:{

        }
    })
```



#### 学员操作—注册页面

需求说明
使用常见表单元素布局注册页面
使用v-model指令完成对应数据的绑定
填写的表单内容可以显示在表单下方

https://www.w3school.com.cn/tiy/t.asp?f=eg_html_fieldset





#### 学员操作—点击重新编辑

需求说明
点击“Edit Me”，下方出现文本框，可以自行修改文本
输入框中的文字和页面中的文字保持一致
使用 v-show、v-on、v-model 指令



#### 学员操作—计算总价



#### 学员操作—仿京东左侧菜单

需求说明
完成京东左侧菜单的页面布局
使用 v-for 指令遍历子分类名称，从而显示子分类的列表

#### 学员操作—导航切换

需求说明
点击导航条中的导航项目，当前被点击的项目内容会显示在下方绿色方块中，并且当前被点击项目的背景会变成红色
使用 v-for 指令遍历显示导航项目，使用v-on添加添加事件，使用v-bind指令动态绑定class和key属性
