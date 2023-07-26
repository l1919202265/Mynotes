# 函数

###### 函数数程序的基本单元，是完成任务的代码语句块

##### 函数分类：

1、系统函数

2、自定义函数

##### 函数的特征：

1、可实现一定的功能

2、可以返回一个结果

3、可以有参数



###### 函数不会立即执行，调用才会执行

```javascript
<button onclick="函数名()"></button>
```

调用函数的方法

函数变();

##### 系统函数

```javascript
parseInt();	//取整 省略小数点后面的内容 取整数
parseFloat();	//保留小数
isNaN();		//判断是否为一个数字 内存中的值 是否是一个数字

```

##### 自定义函数

```javascript
//具名无参函数	-----------
function 函数名(){
    js执行内容
}
//调用的：
//函数名()
//事件名 = '函数名()'

```

##### 参数

##### 实参

```javascript
函数的参数是按照顺序一一对应的
如果形参没有值，结果及时undefined
```



```javascript
//带参函数	----------
//写函数的时候 声明的参数	形参
//调用函数的时候 传递的参数 实参
<button onclick="fn(prompt('请输入')-0)"></button>

function fn(num){	//num形参	声名函数的时候
for(var i= 1;i<=num;i++){
    document.write(i+'老陈你好<br>');
}    
}

fn(3);	//3实参	调用的时候
```

```javascript
function fn(metal){
    document.write(metal+'狗狗');
}
fn('黄金');
```

```javascript
<button onclick="fn(prompt('请输入您的姓名'))"></button>

<script>
    function fn(name_){
    var num = Math.round(Math.random() * 10);
    if(num < 3){
       alert('大气，牛逼，富贵');
       }else if(num<7){
                alert('有磅礴之气，何愁博不得历史年荣华');
                }
    else{
        alert('虎豹之驹，虽未成纹，亦有食牛之气');
    }
}
</script>
```

#### 具名函数

```javascript
//具名函数
function fn(){
    console.log('具名函数');
}
```



#### 匿名函数

没有函数名的函数

```javascript
//匿名函数 
var fn= function(){
     console.log('匿名函数');
 }
fn();//调用

var add = function(a,b){
    console.log(a + b);
}
add(3,5);
```

#### 自执行函数

```javascript
//声明后立马调用
//好处:声明重复的变量 单独成立一作用域 在内部声明的变量 局部变量 变量名重复不影响
//防止同名变量被污染	下面变量的值覆盖上面变量的值
(function (){
    console.log('自执行函数');
})();

(function (){
    console.log('自执行函数');
}());
```

#### 显示学员信息

```javascript
<button onclick="add(prompt('请输入学员姓名'))">添加学员信息</button>
<br>
<button>显示学员信息</button>


<script>
var students = [];
function add(name){
    if(name.length == 0){
       alert('用户名不能为空，添加失败');
       }else{
           students.push(name);
           alert('添加成功');
       }
}


var show = function (){
    if(students.length == 0){
       aleret('暂时没有学员信息，无法正常显示');
       }else{
           for(var item of students){
               document.write(item+'<br>')
           }
       }
}
</script>
```

#### 函数返回值

```javascript
//return	调用函数的返回值
//函数作用域内 return 后面的内容不再执行
//函数执行到return就结束了
function fn(){
    return 5;
}
var num = fn();
console.log(num);



function bigest(a,b,c){
    //var big = (a > b ? a : b) > c ? (a > b ? a : b) : c;
    //return big
    return (a > b ? a : b) > c ? (a > b ? a : b) : c;
}
var da = bigest(3,2,8);
console.log(da);
```

调用函数加不加括号的区别

```javascript
//加括号 得到函数的返回值	才是调用函数
//不加括号 得到的是函数本身
var fn = function(){
    return 5;
}
console.log(fn);	//函数执行体本身
console.log(fn());	//5	
```

