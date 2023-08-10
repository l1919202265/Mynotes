### 逻辑运算符

```javascript
&		//and 多个条件同时满足 结果为true 结果是 0 false或者1 非零 true
&&		//短路and 判断 只有出现false不在向后比较 直接给结果 false
|		//依次比较直到 满足条件
||		//短路或
！		//取反
```

### if else

```javascript
if(条件){
    //条件为true
    //执行的代码
}
if(条件){
    //条件为true 执行的内容
}else{
    //条件为false 执行的内容
}


var scrore = prompt;
if(scoore > 600){
    conlsole.log("你可以上211");
}else{
    console.log("没学上")
}


var scrore = prompt('请输入您的高考成绩')-0;
if(scrore <=750 && scrore >0){
    alert('输入正确');
    if(scrore > 600){
    cnsole.log('您可以上985大学')
}else if(scrore > 550){
    cnosole.log('您可以上211大学')
}else if(scrore > 450){
    console.log('您可以上普通本科')
}else if(scrore > 200){
    console.log('您可以上专科学校')
}else{
    console.log('您听说过富士康吗？')
}

}else{
    alert('请输入正确的分数')
}
```

### if else加油案例

```javascript
var oilType = prompt('请输入您家汽油的型号：92或95');
    if (oilType == 92) {
        console.log('加的92汽油')
        var oilL = prompt('请输入92号汽油的升数');
        if (oilL >= 20) {
            var money = oilL * 5.9;
            console.log('您加的' + oilType + '号汽油,加了' + oilL + '升，一共' + money + '元');
        }
    } else if (oilType == 95) {
        console.log('加的95汽油')
    } else {
        console.log('请输入正确的汽油型号：92或95');
    }
```



### 变量名命名法则

```javascript
字母	数字	_	美元符号
驼峰命名法则	第一个单词字母小写 第二个单词字母大写 首字母大写

！不能以关键字声明变量
不能以数字开头
可以以下划线开头
可以以美元符号开头
```

### switch

```javascript
!important; 	没有break会导致case击穿，所有case都执行
switch(判断的值){
    case 选项1:
        满足选项1执行的代码;
        break;
    case 选项2:
        满足选项2执行的代码;
        break;
    case 选项3:
        满足选项3执行的代码;
        break;
    default:
        执行默认
}



var day = prompt('请输入周几(1-7)');
switch (day){
    case 1:
        console.log('今天才周一，好好工作');
        break;
    case 2:
        console.log('今天周二，好好工作');
    case 3:
        console.log('今天周三，好好工作');
    case 4:
        console.log('今天周四，好好工作');
    case 5:
        console.log('今天周五，好好工作');
    case 6:
        console.log('今天周六，好好工作');
    case 7:
        console.log('今天周日，好好工作');
}
```

### 三目运算符

```javascript
?	表达式true的结果
:	表达是false的结果
var day = 2;
//			  true/false
day = day > 7 ? 1 : day
```

