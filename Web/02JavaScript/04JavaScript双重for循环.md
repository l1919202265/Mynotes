## 双重for循环

#### 时钟示例循环

```javascript
for(var i = 1;i<=12;i++){
    console.log(i+'时');
    for(j=0;j<=59;j++){
        console.log(i+'时'+ j + '分');
    }
}
```

#### 九九乘法表(正序)

```javascript
    for (i = 1; i <= 9; i++) {
        for (j = 1; j <= i; j++) {
            document.write(i + '*' + j + '=' + (i * j));
            document.write('&nbsp;&nbsp;&nbsp;');
        }

        document.write('<br>');
    }
```

#### 九九乘法表(倒序)

```javascript
    for (i = 9; i >= 1; i--) {
        for (j = 1; j <= i; j++) {
            document.write(i + '*' + j + '=' + (i * j));
            document.write('&nbsp;&nbsp;&nbsp;');
        }
        document.write('<br>');
    }
```

#### 判断一个整数是几位数

```javascript
var num = 19800;
for(var i = 1;i>0;i++){
    //取整
    num = parseInt(num / 10)
    if(num == 0){
       break
       }
}
sonsole.log('是' + i + '位数');
```

#### 判断一千以内的质数

```javascript
    for (i = 2; i < 1000; i++) {
        for (j = 2; j < 1000; j++) {
            if (i % j == 0) {
                break;
            }
        }
        if (i == j) {
            document.write(i + '是质数');
            document.write('<br>');
            console.log(i + '是质数');
        }

    }
```

## 数组

#### 数组去重

```javascript
    var arr = [91, 346, 4, 5, 7, 59, 7, 0, 34, 34, 5, 327, 348, 2, 346, 324, 2, 5, 5, 64, 6, , 5324, 2, 4114, 31, 5,];
    for (i = 0; i < arr.length; i++) {
        for (j = i + 1; j < arr.length; j++) {
            if (arr[i] == arr[j]) {
                arr.splice(j, 1);
                i--;
            }
        }
    }
    arr.sort(function (a, b) {
        return a - b;
    })
    document.write(arr);
```



#### for in和for of

```javascript
for in	//数组的下标
for(var i in arry){
    console.log(i);
    console.log(arry[i]);
}


for of//数组中的每一项
for(var item of arry){
    console.log(item);
}
```

#### 去除每一项放入新数组

```javascript
var arry = [1,2,[99,88]];
//undefined
console.log(arry[0].length);
//undefined
console.log(arry[1].length);
//2
console.log(arry[2].length);


var newArry = [];
for(var item of arry){
    if(item.length != undefined){
       console.log(item,'是一个数组');
        for(var item2 of item){
            console.log(item2);
            newArry.push(item2);
        }
        continue;
       }
}





for(var i=0){
    
}
```

#### `toFixed()`

 方法将字符串四舍五入为指定的小数位数。

```javascript
let num = 5.56789;
let n = num.toFixed();

```