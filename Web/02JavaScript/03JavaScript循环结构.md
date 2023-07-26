## 循环结构

### 循环的特点

##### 循环结构的组成：

循环的起始值 1

循环条件 < <= > >= = ==

自增量 ++

```javascript
//1、循环起始值 (循环的时候 从哪开始)
//2、循环条件 (判断循环的起始值 是否满足条件 满足就执行 不满足 终止循环)
//3、循环体 循环操作什么
//4、循环迭代 (循环的起始值 要变化)
for(var i = 1;i<=5; i++){
    console.log('跑' + i + '圈');
}
console.log(i)	// i = 6;
```

循环10以内偶数和

```javascript
var sum = 0;	//全局变量 总的和
for(var i = 2;i <= 10;i += 2){
    console.log(i);
    sum += i;
}
console.log(sum);
```

10以内奇数和

```javascript
var sum = 0;
for(var i = 1;i<=10;i += 2){
    console.log(i);
    sum += i;
}
console.log(sum);



var sum = 0;
for(var )
```

continue和break

```javascript
//continue	跳出本次循环继续下次循环
//break	终止整个循环
    for (var i = 1; i <= 5; i++) {
        if (i == 3) {
            continue;
        }
        console.log(i);
    }
```

折纸珠峰

```javascript
var paper = 0.0001;
var peek = 8848;
for(var i = 1;i > 0; i++){
    paper *= 2;
    console.log(paper);
    if(paper > peek ){
        console.log('对折' + i + '次超过珠峰')
        break;
    }
}
```

#### while

```javascript
//循环起始值
//循环条件
//循环体
//循环迭代

while(循环条件){
    //循环操作
    //迭代部分
}
```

