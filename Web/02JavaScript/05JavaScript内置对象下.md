0.1+0.2==0.3?

答案是不等的

结果为：0.30000000000000004

为什么?

```javascript
因为JavaScript的number类型为双精准度IEEE 754 64位浮点类型
第0位：符号位，0表示正数，1表示负数(s)
第1位到第11位：储存指数部分(e)
第12位到63位：储存小数部分(既有效数字)
即小数后面储存52位

十进制的0.1转换
为二进制数据的时候，是无限循环的，但是s都number类型只能保存小数点后面52位，不能无限的存储所以剩下的内容会采取类似四舍五入的方式丢弃，即0舍1入所以就造成了精度的丢失
```

## String对象的方法

```javascript
var str = 'nihaolaochen'
console.log(str)//string

var str1 = new String('nihaoxiaochen');
console.log(str1);//object
```



### length

```javascript
length	//字符串的长度【属性】
console.log(str.length);
```

### charAt(a)

```javascript
charAt(a);	//返回在指定位置的字符（注：字符串中的第一个字符的下标是0，a代表下标,可以根据字符串的下标 返回对应的字符） 取不到的时候输出空字符串
//使用数组方法下标取值	没有的下标返回undefined
console.log(charAt(a));
```



### concat(b)

```javascript
concat(b)	//连接字符串，b:被合并对象名，和+的作用一样，不改变原字符串
str.concat(str2);
str = str.concat(str2);
concat(b) = str
```



### replace()

```javascript
//replace 不改变原字符串
replace(/a/,'b');	//把匹配到的第一个a 替换成b
replace('a','b');	//把匹配到的第一个a 替换成b
replace(/a/g,'b');	//把匹配到的所有的a 全部替换成b
//g		global 全局
var str = 'nihaolaochen';
var str = '你是个sb吗，会不会玩，cnm'
str = str.replce(/o/,'*');
str = str.replace('o','*');
str = str.replace(/o/g,'*');
str = str.replace(/sb/g,'**');
str = str.replace(/cnm/g,'***');
```



### split()

```javascript
split('')		//把对象根据引号内的规则分割成数组
var str = 'ni-hao-shi-jie';
var arry = str.split('-');
console.log(str);
```

### indexOf('字符')

```javascript
indexOf('字符')	//根据字符找到所在的下标位置(只返回第一个下标)；如果找不到，返回-1；
var str = 'nihaolaochen';	//str.indexOf('字符') 根据字符 返回第一个匹配到的下标
console.log('str.indexOf('o')');	//	4
console.log('str.indexOf('w')');	//	-1	-1说明当前字符串 没有要查找的内容
```

### lastIndexOf()

```javascript
lastIndexOf()	//返回一个指定的字符串值最后出现的下标位置
var str = '123.haha.aa.jpg'
console.log(str.lastIndexOf('.'));
```

### 查看字符c在字符串中的所有下标

```javascript
var str = 'abcdcfcc';
var indexArry = [];
for(var i = 0;i < str1.length;i++){
    console.log(str1.charAt(i));
    if('c' == str1.charAt(i)){
        indexArry.push(i)
    }
}
console.log(indexArry);



var str = 'abcdcfcc';
var arry = str1.split();
console.log(arry);
var indexArry = [];
for(var i = 0;i<arry.length;i++){
    if('c' == arry[i]){
        indexArry.push(i)
    }
}
console.log(indexArry);
```

### toLowerCase();

```javascript
toLowerCase();	//将字符串字母转为小写 LAOCHEN → laochen
var str = 'laoChEn'
str = str.toLowerCase();
console.log(str);
```

### toUpperCase();

```javascript
toUpperCase();	//不改变原数组 将字符串字母转为大写 laochen → LAOCHEN		LAOchen → LAOCHEN
var str = 'laochen'
str = str.toUpperCase();
console.log(str);
```

### 截取字符串的三种方法

```javascript
//对象名.substr(a,b);第一个值开始的下标位置，第二个值截取的长度	包含开始的下标	//只写一个截取到最后
var str = '你好世界我爱你';
console.log(str.substr(2));	//世界我爱你
console.log(str.substr(2,4));	//世界我爱
```

```javascript
//对象名.substring(a,b);第一个值开始的下标位置，第二个结束的下标(不包含b);	//只写一个值截取到最后
var str = '你好世界我爱你';
//	2开始的下标
//	4结束的下标 不包含结束的这一个位置
console.log(str.substring(2,4));	//世界
```

```javascript
//对象名.slice(a,b);第一个值:最开始的下标位置，第二个结束的下标(不含b)	只写一个a的时候，从a开始，一直代截取最后(使用于上面三个)
var str = '你好世界我爱你'；
//	2开始的下标
//	4结束的下标 不包含结束的这一个位置
console.log(str.slice(2,4));//世界
```

##### 数组中包含a或者A的个数

```javascript
var arr = ['America','Greece','Britain','Canada','China','Egypt'];
var num = 0;	//计数器
for(var i = 0;i < arr.length;i++){
    if(arr[i].indexOf('a') != -1 || arr[i].indexOf('A') != -1){
        num++
    }
}
console.log(num);
```

##### 练习单词首字母变大写

```javascript
var str = 'border-left-color';
var strArry = str.split('-');
console.log(strArry);
for(var i = 0;i < strArry.length;i++){
    //console.log(strArry[i]);
    //strArry[i].substr(0,1).toUpperCase()
  //console.log(strArry[i].substr(0,1).toUpperCase());
    strArry[i] = strArry[i].substr(0,1).toUpperCase() + strArry[i].substr(1);
}
console.log(strArry);
str = strArry.join('');
console.log(str);
```

##### 找文件类型

```javascript
var str ='aa.bb.cc.avi';
//找到最后一个	下标
//截取	最后一个下标 +1 截取
var index = str.lastIndexOf('.');
console.log(index);
var type = str.slice(index + 1);
console.log(type);



var str ='aa.bb.cc.avi';
str1 = str.lastIndexOf('.')
str2 = str1.substring(str1+1);
console.log(str2);
```

### Math对象

```javascript
ceil()	//对数进行上舍入	不改变原数据	数轴上最靠近右边的整数
Math.ceil(25.6);返回 26
Math.ceil(-25.5);返回-25
var num = -8.1;
num = Math.ceil(num);
console.log(num);	//-8

floor()	//对数进行下舍入	向下取值	取数轴上最靠近当前数左边的整数	不改变原始数据
Math.floor(25.5);返回 25
Math.floor(-26);返回 -26
var num = -8.9；
num = Math.floor(num);
console.log(num);	//-9

round()	//把数四舍五入为最接近的数
//正数:四舍五入
//负数：小数部分<=0.5时，相近整数更靠近右侧，所以取值右侧的整数，即原负数的整数部分不变。
//网上有人称五舍六入是不准确的！！！
Math.round(25.5);返回 26
Math.round(-25.5);返回 -26
var num = 23.2;
num = Math.round(num);
console.log(num);	//23

var num = 23.51;
num = Math.round(num);
console.log(num);	//24


Math.abs();	//求绝对值
var num = -23;
num = Math.abs(num);
console.log(num);


andom()	//返回0.0-0.1之间的随机数
Math.random();	//例如0.6273608814137365
var num = Math.random();
console.log(num);


//生成5个1=10之间的随机数
var arry = [];
for(var i = 0;i<5;i++){
    var num = Math.random()*10;
    num = Math.round(num);
    if(num < 1){
       num +=1;
       }
    arry.push(num);
}
console.log(arry);
```

#### 判断用户名输入是否正确

```html
用户名：<input type="text">
    <br>
    <button onclick="register()">注册</button>



<script>
    //函数	不会自动执行 调用的时候 才执行
    function register(){
        alert('点击注册了');
        //1、找到input框
        //2、当前input.value
        var ipt = document.getElementsByTagName('inpupt')[0];
        var name = ipt.value;
        console.log(name);
        if(name.length == 0){
           alert('用户名不能为空');
           }else if(name.length > 6){
                    alert('用户名不能大于6位数');
                    }else{
                        alert('注册成功');
                        ipt.value = '';
                    }
    }
</script>
```

#### filter过滤器

```javascript
//arry要过滤的数组
//item要过滤数组中的每一项
//return后面跟要过滤满足的条件 即满足条件的内容过滤出来 生成一个新的数组
//newArry代表过滤后生成新的数组
var newArry = arry.filter(function(item){
                          return item < 30;
                          });
```

```javascript
var arry = [17,22,35,28,29,45,50];
var ages = arry.filter(function(){
    return item < 30;
});
console.log(ages);
```

```javascript
//去假值
//只要使用Boolean() 强转 结果为false的都是假值
//null undefined '' 0 NaN false	都是假值
//var bool = Boolean(udefined);
//console.log(bool);


var arry = [null,undefined,true,false,NaN'haha','nihao',0,18];
var val = arry.filter(function(item){
    return Boolean(item);
})
console.log(val);
```

#### find

```javascript
//查找符合条件的第一个值
数组名.find(function(item){
    return item>条件
})
得到的结果，是满足条件的第一个值，如果数组种的没有任何值满足条件，则返回undefined


var num = arr.find
```

#### findIndex 返回第一个满足条件元素的下标

如果数组中的某一个元素满足条件，则返回第一个满足条件元素的下标，如果任意元素都不满足条件，则返回-1

```javascript
    var arry = [55, 66, 77];
    var val = arry.findIndex(function (item) {
        return item > 60;
    })

    console.log(val);  //1  因为66是第一个满足条件的元素 下标1 

-------------------------------------------------------------------

    var arry = [55, 66, 77];
    var val = arry.findIndex(function (item) {
        return item > 80;
    })

    console.log(val);//-1 因为没有任何一个元素满足大于80的条件
```

#### includes 判断是否包含元素

结果是true 和false

```javascript
    var arry = [55, 66, 77, 88, 99];
    var result = arry.includes(66);
    console.log(result);//true  数组中有包含的66的元素
		
		---------------------------------------------------------------------------
      
    var arry = [55, 66, 77, 88, 99];
    var result = arry.includes(55, 1); //从arry数组的查找55 从下标为1的位置向后查
    console.log(result);//false
```

### every

判断数组中的元素是否都满足函数规则

```javascript
   let numbers = [100, 200, 300, 400];

   let result = numbers.every(function (item) {
        return item > 100;
    });

   console.log(result); // false 因为 数组中的第一项不满足  >100
	-----------------------------------------------------------------------
     
    let numbers = [100, 200, 300, 400];

    let result = numbers.every(function (item) {
        return item >= 100;
    });

    console.log(result); //true  全部满足
```

