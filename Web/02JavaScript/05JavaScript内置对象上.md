## 冒泡排序

让一个数字和后面的数字进行一次的比较，如果发现前面的大于后面的，就把前面的和后面的进行位置互换，外层从0开始，内层从0+1开始

代码：

```javascript
var arr = [7,8,1,4,5,6,2,3,5];
for (var i=0 ;i<arr.length;i++){
        //8 //1
  for (var j =i+1;j<arr.length;j++){
    if (arr[i]>arr[j]){
      var c = arr[i];
      arr[i] = arr[j];
      arr[j] = c;
      // document.write(arr+'<br>');//可以看到每次的变化
    }
  }
}
document.write(arr);
```



# sort排序

二进制排序，以十位数排序，只能排序1-9，,10以内排序；

```javascript
arry.sort();
```

加强排序，a-b升序，b-a降序；a前面的数据，b后面的数据；

```javascript
arry.sort(function(a,b){

​	return a-b;

})；
```

# 内置对象

数组本身就是一个对象

数组的属性，长度 length

### join()拼接

```javascript
join();
//数组名.join('');
join('定义的规则')
//通过一个分隔符 把数组的所有元素拼接称一个字符串
join('-') //11-22-33-44

join('***') //11***22***33***44

arry.join('-') //调用方法，不会改变原数组
```

### Math.random()生成随机数

```javascript
Math.random()	//生成随机数
console.log(Math.random());


var arr = [1,2,3,4,5,6,7,8];
//打乱数组
arr.sort(function(a,b){
    return Math.random()>0.5 ? b-a : a-b;
});
console.log(arr);
```

### push()末尾元素添加内容

```javascript
push()	//向数组的最后面机添加内容 会改变原数组
var arry = [22,33,44];
arry.push(11);
console.log(arry);	//11,22,33,44
```

### unshift()首位元素添加内容

```javascript
unshift()	//向数组的最前面添加内容 会改变数组
var arry = [22,33,44];
arry.unshift(77,55);
console.log(arry);
```

### pop()删除末尾元素

```javascript
pop()	//删除数组末尾元素 改变原数组 没有参数
var arry = [22,33,44];
arry.pop();
console.log(arry);	//
```

### shift()删除首位元素

```javascript
shift()	//删除数组第一个元素(下表为0)元素  会改变数组 没有参数
var arry = [22,33,44];
arry.shift();
console.log(arry);
```

### concat()合并数组

```javascript
concat()	//合并数组
//a.concat(b);	a数组 合并b数组 不改变原数组 被合并的数组在后面
var arr1 = [11,22,33];
var arr2 = [77,88,99];
console.log(srr1);
arr1.concat(arr2);
var arr3 = arr1.concat(arr1);	//合并后赋值arr3	改变原数组
consle.log(arr1);
```

### splice()删除数组元素

```javascript
splice(a,b，c)	//开始删除的下标 b删除的个数 c删除后插入的内容 会改变原数组
var a = [0,1,2,3,4,5];
a.splice(2,2);
console.log(a);
```

### reverse()数组反转

```javascript
reverse()	//数组反转	会改变原数组
//数组名.reverse();	反过来
var a = [11,22,33,44];
console.log(a);
a.reverse();
console.log(a);
```

### slice()数组查找

```javascript
slice(a,b)	//数组查找 从下标a开始查找到下标b处，(不包含b)	得到一个新数组 不改变原数组
//数组名.slice()
var arr = [1,2,3,4,5,6,7,8];
//arr.slice(a)	从下标a开始查找一直查找到最后 不会改变原数组
//如果arr.slice(0)	从下标为0的位置 一直查到数组结尾 整个的查了一遍 相当于拷贝了一个新数组
var newArr = arr.slice(3,5);
console.log(arr);
console.log(newArr);
```

### 判断出现次数

```javascript
var arr = ['b','a','c','a','g','j','a','c','b'];
//遍历 判断 如果满足 ++
//定义一个变量 用来接收 次数
var index = 0;
for(var i = 0;i < arr.length;i++){
    if('a' == arr[i]){
        index++;
    }
}
console.log(index);
```

#### for in

```javascript
for in	//找到的是下标	增强型for循环
    for(var i in arr){
        console.log(i);
        console.log(arr[i]);
        if('a' == arr[i]){
            index++;
        }
    }
```

#### for of

```javascript
for of	//直接找到每一项
for(var item of arr){
    console.log(item);
    if('a' == item){
        index++;
}
```

### 内置对象之：Date

```javascript
//date	时间对象 可以获取当前的最新时间
//2023-06-06 16:53
//年 月 日 时 分 秒 星期几
var time = new Date();
console.log(time);

//找年
var year = time.getFullYear();
console.log(year);
//找月
var month = time.getMonth() + 1;
console.log(month);
month = month < 10 ? ('0'+ month) : month;
//找日
var date = time.getDate;
date = date < 10 ? ('0' + date) : date;
console.log(date);
//时
var hour  = time.getHours();
hour = hour < 10 ? ('0' + hour) : hour;
console.log(hour);
//分钟
var minute = time.getMinutes();
minute = minute < 10 ? ('0' + minute) : minute;
console.log(minute);
//秒
var second = time.getSeconds();
second = second < 10 ? ('0' + second) : second;
console.log(second)
//星期几	星期的下标
var weekArry = ['星期日'，'星期一'，'星期一二'，'星期三'，'星期四'，'星期五'，'星期六'];
var day = weekArry[time.getDay()];
console.log(day); 



var timeStr = year + '-' + month + '-' + date ' ' +hour + ':' + minute + ':' + second + day;
document.write(timeStr);
```

### 定时器

```javascript
//var index = 0;
setInterval(function(){
    //index++;
    //document.write(index);
},1000)//1000毫秒
```

### 简易时钟

```javascript
    //1、找到标签名、id、类名
    var div = document.getElementsByTagName('div')[0];  //0为下标
    setInterval(function () {
        var time = new Date();

        //找年
        var year = time.getFullYear();

        //找月
        var month = time.getMonth() + 1;
        month = month < 10 ? ('0' + month) : month;

        //找日
        var date = time.getDate();
        date = date < 10 ? ('0' + date) : date;

        //时
        var hour = time.getHours();
        hour = hour < 10 ? ('0' + hour) : hour;

        //分钟
        var minute = time.getMinutes();
        minute = minute < 10 ? ('0' + minute) : minute;

        //秒
        var second = time.getSeconds();
        second = second < 10 ? ('0' + second) : second;

        //星期几	星期的下标
        var weekArry = ['星期日', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六'];
        var day = weekArry[time.getDay()];


        var timeStr;
        timeStr = year + '-' + month + '-' + date +
            '-' + hour + ':' + minute + ':' + second + day;
        div.innerHTML = timeStr;

    }, 1000)

```

