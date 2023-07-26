### 运算符

##### 1、如果+号两边的内容都是number类型 则执行数学运算

##### 2、如果有任意一边是string类型 左右拼接

示例：

```javascript
var num1 = 5;
var num2 = 7;
var sum = num1 + num2;
console.log(sum);
console.log(typeof sum);

打印结果：
12
number
```

```javascript
var num1 = '5';
var num2 = 7;
var sum = num1 + num2;
console.log(sum);
console.log(typeof sum);

打印结果：
57
string
```

##### 3、执行数学运算的时候 false 0	非零的是true 1

```javascript
var num1 = true;
var num2 = 7;
var sum = num1 + num2;
console.log(sum);
console.log(typeof sum);

打印结果：
8
number
```

```javascript
var num1 = false;
var num2 = 7;
var sum = num1 + num2;
console.log(sum);
console.log(typeof sum);

打印结果：
7
number
```

##### 强制类型转换

```javascript
var num = '5.66';
num = parseInt(num);	//转换整数型
console.log(num);
console.log(typeof num);

num = parseFloat(num);	//转换小数


num = parseFloat(num).toFixed(2);	//保留小数点后两位	但类型会转换为string类型
num = parseFloat(num).toFixed(2)-0;	//减0后转换为number类型	隐式类型转换


console.log(num);
console.log(typeof num);


```

##### 隐式类型转换

减法

左右两边都是number 进行数学的减法

有任意一个不是number 隐式类型转换 自动的转为number('5') 然后进行运算 如果不能转为例如number('哈哈') 结果为NaN(not a number)	类型为number

```javascript
var num1 = 10;
var num2 = '3';
var sum = num1 - num2;
console.log(sum);
console.log(typeof sum);


打印结果:
7
number
```

```javascript
prompt	//接受的内容 全部都是string类型
var = prompmt("请输入数字");
var = prompmt("请输入数字")-0;	//转换为number类型
var = parseInt(prompmt("请输入数字"));	//转换为整数类型
```
