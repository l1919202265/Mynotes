【本次试题，分上机题和简答题两大部分。上机题22道，每题4分，合计88分。简单3道，每题4分，合计12分。共100分】



## 一、上机题（每题4分，共88分）



#### 1. 新建一个数组，里面存放10个随机整数（ 100~1000）

```js
 // 写法1：if判断小于10的数字

    var arry = [];
    for (var i = 0; i < 10; i++) {
        var num = Math.round(Math.random() * 1000);
        if (num < 100) {
            num += 100;
        }
        arry.push(num);
    }
    console.log(arry);

```

```js
 //写法2：三目运算符

    var arry = [];
    for (var i = 0; i < 10; i++) {
        var num = Math.round(Math.random() * 1000);
        num = num < 100 ? num + 100 : num;
        arry.push(num);
    }
    console.log(arry);
```



#### 2. 将数组 [2, 0, 6, 1, 77, 0, 52, 0, 25, 7] 中大于等于 10 的元素选出来，放入新数组。

```js
		//写法1：普通for循环
    var arry = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
    var newArry = [];//新数组  存放大于等于10的元素

    for (var i = 0; i < arry.length; i++) {
        if (arry[i] >= 10) {
            newArry.push(arry[i]);
        }
    }
    console.log(newArry);//[77, 52, 25]
```

```js
    //写法2： for in
    var arry = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
    var newArry = [];//新数组  存放大于等于10的元素

    for (var i in arry) {
        if (arry[i] >= 10) {
            newArry.push(arry[i]);
        }
    }
    console.log(newArry);//[77, 52, 25]
```

```js
   //写法3： for of
    var arry = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
    var newArry = [];//新数组  存放大于等于10的元素

    for (var item of arry) {
        if (item >= 10) {
            newArry.push(item);
        }
    }
    console.log(newArry);//[77, 52, 25]
```

```js
   //写法4  filter 过滤器
    var arry = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
    var newArry = arry.filter(function (item) {
        return item >= 10;
    })

    console.log(newArry);
```



​		 

#### 3. 数组[0, 6, 1, 77, 0, 52, 0, 25]中0出现几次

```js
   // 写法1：普通for
    var arry = [0, 6, 1, 77, 0, 52, 0, 25];
    var index = 0;//计数器
    for (var i = 0; i < arry.length; i++) {
        if (arry[i] == 0) {
            index++;
        }
    }
    console.log(index);//3
```

```js
 // 写法2：for in
    var arry = [0, 6, 1, 77, 0, 52, 0, 25];
    var index = 0;//计数器
    for (var i in arry) {
        if (arry[i] == 0) {
            index++;
        }
    }
    console.log(index);//3
```

```js
 // 写法3：for of
    var arry = [0, 6, 1, 77, 0, 52, 0, 25];
    var index = 0;//计数器
    for (var item of arry) {
        if (item == 0) {
            index++;
        }
    }
    console.log(index);//3
```

```js
 // 写法4：通过过滤器 过滤出满足条件的内容 然后判断过滤器数组的长度
    var arry = [0, 6, 1, 77, 0, 52, 0, 25];
    var newArry = arry.filter(function (item) {
        return item == 0;
    })

    console.log(newArry.length);//3
```



​		**综上，大家要善于运用过滤器，for of等方式，简化了代码的书写**



#### 4. 定义数组[2, 0, 6, 1, 77, 0, 52, 0, 25, 7] ：求数组的和，最大值，最小值，平均数

```js
    var arry = [2, 0, 6, 1, 77, 0, 52, 0, 25, 7];
    var sum = 0;//和

    for (var i = 0; i < arry.length; i++) {
        sum += arry[i];
    }

    // 1.求和
    console.log('数组的和为：' + sum);//170

    // 2. 求平均数
    var avg = sum / arry.length;//平均数
    console.log('数组的平均数：' + avg); //17

    // 3.求最大值
    //   思路：利用数组排序  从大到小  然后取数组的下标为0 的值
    arry.sort(function (a, b) {
        return b - a;
    })[0];

    var max = arry[0];//最大值

    console.log('最大值' + max);

    // 4.最小值  求数组的最后一个 即 数组.length - 1;
    var min = arry[arry.length - 1];
    console.log(min);//0
```



#### 5. 将数组 ['red', 'green', 'blue', 'pink'] 转换为字符串，并且用 | 分割

希望得到的结果：red|green|blue|pink

```js
    var arry = ['red', 'green', 'blue', 'pink'];
    var str = arry.join('|');
    console.log(str);//red|green|blue|pink
```



#### 6.从键盘上输出10个整数，合法值为1,2或3，其余为不合法，并且统计合法及不合法的个数（使用switch）

```js
    var index = 0;//输入合法计数器
    var wrong = 0;//输入不合法的计数器
    for (var i = 1; i <= 10; i++) {
        var num = prompt('请输入第' + i + '个整数') - 0;
        switch (num) {
            case 1:
            case 2:
            case 3:
                index++;
                break;
            default:
                wrong++;
        }
    }

    console.log(index);
    console.log(wrong);
```



#### 7. 有一个数组，长度为5，[1,3,-1,5,-2];

需要生成个新数组；要求新数组的存放顺序与原数组的元素逆序，并且如果原数组中的元素值小于0，在新数组中按0存储

```js
    var arry = [1, 3, -1, 5, -2];
    
    //1.首先数组反转
    var newArry = arry.reverse();
    // console.log(newArry);//[-2, 5, -1, 3, 1]

    //2.对反转后的新数组 进行遍历判断
    for (var i in newArry) {
        if (newArry[i] < 0) {
            newArry[i] = 0
        }
    }

    console.log(newArry);//[0, 5, 0, 3, 1]
```



#### 8. 当前数组：[10,11,5,7,9,23,18,4,6],求该数组中奇数的个数，偶数的个数



```js
    var arry = [10, 11, 5, 7, 9, 23, 18, 4, 6];

    var odd = 0; //奇数
    var even = 0; //偶数
    for (var item of arry) {
        if (item % 2 == 0) {
            even++;
        } else {
            odd++;
        }
    }

    console.log('奇数的个数：' + odd);//5

    console.log('偶数的个数：' + even);//4

```





#### 9. 把数组[1,0,2,3] 变为 ['1', '|', '0', '|', '2', '|', '3']



```js
		var arry = [1, 0, 2, 3];
    var str = arry.join('|');
   
    console.log(str);//1|0|2|3

    var newArry = str.split('');

    console.log(newArry);
```





#### 10. 删除数组的第一个元素，不改变原数组

```js
    var arry = [1, 2, 3, 4];
    var newArry = arry.slice(1);

    console.log(arry);//[1, 2, 3, 4]
    console.log(newArry);//[2, 3, 4]
```



#### 11. 分数数组[56, 78, 77, 32, 99]，要求把数组中不及格的删除，剩余的放到新数组里面

```js
    var arry = [56, 78, 77, 32, 99];
    var newArry = arry.filter(function (item) {
        return item >= 60
    })

    console.log(newArry);//[78, 77, 99]
```



#### 12. 反转数组['red', 'green', 'blue', 'pink'] 

```js
    var colors = ['red', 'green', 'blue', 'pink'];
    colors.reverse();
    console.log(colors);
```





#### 13. [13, 4, 77, 1, 7]数组排序，倒序排列

```js
    var arry = [13, 4, 77, 1, 7];
    arry.sort(function (a, b) {
        return b - a;
    })
    console.log(arry);// [77, 13, 7, 4, 1]
```



#### 14. ['c', 'a', 'z', 'a', 'x', 'a', 'x', 'c', 'b']去重并排序

```js
    var arry = ['c', 'a', 'z', 'a', 'x', 'a', 'x', 'c', 'b'];
    for (var i = 0; i < arry.length; i++) {
        for (var j = i + 1; j < arry.length; j++) {
            if (arry[i] === arry[j]) {
                arry.splice(j, 1);
                j--;
            }
        }
    }

```



#### 15. 一个含有字符串的数组 ['a','b','c','a','g','c','g'],需要得到一个新数组

  ['a1', 'b', 'c1', 'a2', 'g1', 'c2', 'g2']
  要求：未重复出现的元素不处理 
              重复出现的元素加编号
             不影响正常数组元素的顺序

```js
 var arry = ['a', 'b', 'c', 'a', 'a', 'a', 'g', 'c', 'g', 'g', 'g'];

    for (var i = 0; i < arry.length; i++) {
        var num = 1;
        var c = arry[i];

        for (var j = i + 1; j < arry.length; j++) {

            if (arry[i] == arry[j]) {
                arry[i] += 1;
            }

            if (c == arry[j]) {
                num++;
                console.log(num);
                // arry[i] = arry[i] + 1;
                arry[j] += num;
            }
        }
    }

    console.log(arry);
```



#### 16. 判断一个数组中有几个回文字符串: ['level', 'haha', 'hello', 'abcdcba', 'green', 'nan', 'naan']

  回文字符串：倒过来，正过去都是一样的

  回文字符串 示例： 'level'  'abcdcba'  'nan'  'naan'

​	

```js
var arry = ['level', 'haha', 'hello', 'abcdcba', 'green', 'nan', 'naan'];
    var index = 0;//计数器
    for (var item of arry) {
        if (item == item.split('').reverse('').join('')) {
            console.log(item);
            index++;
        }
    }
    console.log(index);
```



#### 17. 打乱数组 [1, 2, 3, 4, 5, 6, 7, 8] => [4, 3, 8, 2, 6, 1, 5, 7

​		(随机打乱) 使用到随机数

```js
	  var arry = [1, 2, 3, 4, 5, 6, 7, 8];
    arry.sort(function (a, b) {
        console.log(Math.random());
        return Math.random() > 0.5 ? b - a : a - b;
    })

    console.log(arry);// [6, 8, 5, 4, 3, 7, 1, 2]
```



#### 18. 查找字符串"abcoefoxyozzopp"中所有o出现的位置（位置下标用数组保存）以及次数

​	

```js
 //  查找字符串"abcoefoxyozzopp"中所有o出现的位置以及次数

    var str = 'abcoefoxyozzopp';
    var arry = str.split('');
    console.log(arry);

    var index = 0;//计数出现的次数
    var indexArry = []; //存储出现的位置
    for (var i in arry) {
        if (arry[i] == 'o') {
            index++;
            indexArry.push(i);
        }
    }

    console.log(index);
    console.log(indexArry);
```



#### 19. 加横线

  把字符串：'123456789101112'
  变为：'123-456-789-101-112'

```js
    var str = '123456789101112';
    var arry = [];
    for (var i = 0; i < str.length; i += 3) {
        var newStr = str.substr(i, 3);
        arry.push(newStr);
    }

    console.log(arry.join('-'));

```



#### 20.截取字符串"我爱你中国，我亲爱的母亲"，中的"中国，我亲爱的"；

```js
	  var str = "我爱你中国，我亲爱的母亲";
    //方法1：
    // var newStr = str.slice(3, 10);
    // console.log(newStr);
    //方法2：
    // var newStr = str.substr(3, 7);
    // console.log(newStr);
    //方法3：
    var newStr = str.substring(3, 10);
    console.log(newStr);
```



#### 21. 拔尖：

  已知数组 ：
  [4, 5, 1, 3], 
  [13, 27, 18, 26], 
  [32, 35, 37, 39], 
  [1000, 1001, 857, 1]
  分别找到每个小数组中的最大值，然后把它们串联起来，形成一个新数组。

```js
    //方法1：
    var arry1 = [4, 5, 1, 3];
    var arry2 = [13, 27, 18, 26];
    var arry3 = [32, 35, 37, 39];
    var arry4 = [1000, 1001, 857, 1];

    var maxArry = [];// 所有最大值的数组

    arry1.sort(function (a, b) {
        return b - a;
    })
    var max1 = arry1[0];
    console.log(max1);

    var max2 = arry2.sort(function (a, b) {
        return b - a;
    })[0];

    console.log(max2);

    var max3 = arry3.sort(function (a, b) {
        return b - a;
    })[0];

    console.log(max3);
    var max4 = arry4.sort(function (a, b) {
        return b - a;
    })[0];

    console.log(max4);

    //向最大数组添加值
    maxArry.push(max1, max2, max3, max4);
    console.log(maxArry);//[5, 27, 39, 1001]
```



```js

    //方法2 利用双重数组
    
    var arry = [[4, 5, 1, 3], [13, 27, 18, 26], [32, 35, 37, 39], [1000, 1001, 857, 1]];

    var maxArry = []
    for (var i = 0; i < arry.length; i++) {
        var max = arry[i].sort(function (a, b) {
            return b - a;
        })[0];

        console.log(max);
        maxArry.push(max);
    }

    console.log(maxArry);//[5, 27, 39, 1001]
```



#### 22.删除假值:删除数组中的所有假值，得到一个所有值为真值的新数组 

​		在JavaScript中，假值有`false`、`null`、`0`、`""`、`undefined` 和 `NaN`。

​		当前数组为：[null, undefined, true, false, 'hah', 'nihao', 0, 18, NaN]；

​		

```js
   var arry = [null, undefined, true, false, 'hah', 'nihao', 0, 18, NaN];
    var newArry = arry.filter(function (item) {
        return Boolean(item);
    })

    console.log(newArry);
```





## 二、简单题

##     （每题4分，共12分  简答题同样写在代码中，在html文件中直接书写）



#### 23. 回答js中的数据类型，并说出null和undefined的区别

```
js中的数据类型：

基本数据类型：Number，String，Boolean，Undefined，Null
复杂（引用）数据类型：Object
```



```
null 和undefined的区别：

1.null表示空值，undefined表示声明变量没有赋值
2.undefined派生于null，所以，undefined == null时，结果为true
3.undefined 和 null 转为boolean类型的时候，结果都为false
4.undefined在进行隐式类型转换的时候，如undefined - 0,结果为NaN
  null在进行隐式类型转换的时候，如null - 0,结果为0
5.undefined是一个全局变量，null是js中的关键字
6.进行typeof类型检测的时候，undefined控制台输出类型：undefined
                         null控制台数组类型：Object

```



#### 24.splice 和slice的区别

```js
1.splice用于删除数组的元素，会改变原数组
	splice(a,b),a表示从哪个下标开始删除，b表示删除的个数
	splice(a,b,c),a表示从哪个下标开始删除，b表示删除的个数,c表示删除元素后替换的值
	
	如：
	  var arry = [1, 2, 3, 4];
    arry.splice(0, 2, 'hahah');
    console.log(arry);// ['hahah', 3, 4]
	

2.slice是查找数组内的元素，或者说是切割数组，不会改变原数组
	slice(a,b); a表示开始查找的下标，b表示查找结束的下标，但不包含b,会返回一个新数组
	splice(0) 相当于拷贝了一个新数组
```



#### 25. 数组常用的方法有哪些

```js
1、push()

向数组的末尾添加新内容

参数：要添加的项。传递多个用逗号隔开，任何数据类型都可以

返回值：新增后数组的长度

是否改变原数组：改变


2、pop()

删除数组的最后一项

参数：无

返回值：被删除的项

是否改变原数组：改变



3、shift()

删除数组的第一项

参数：无

返回值：被删除的项

是否改变原数组：改变


4、unshift()

向数组首位添加新内容

参数：要添加的项，多项用','隔开

返回值：新数组的长度

是否改变原数组：改变





5、slice()

按照条件查找出其中的部分内容

参数：

array.slice(n, m)，从索引n开始查找到m处（不包含m）

array.slice(n) 第二个参数省略，则一直查找到末尾

array.slice(0)原样输出内容，可以实现数组克隆


返回值：返回一个新数组

是否改变原数组：不改变



6、splice()

对数组进行增删改

增加：ary.splice(n,0,m)从索引n开始删除0项，把m或者更多的内容插入到索引n的前面

返回空数组

修改：ary.splice(n,x,m)从索引n开始删除x个，m替换删除的部分

把原有内容删除掉，然后用新内容替换掉

删除：ary.splice(n,m) 从索引n开始删除m个内容

（如果第二个参数省略，则从n删除到末尾）

返回删除的新数组，原有数组改变

 

7、join()

用指定的分隔符将数组每一项拼接为字符串

参数：指定的分隔符（如果省略该参数，则使用逗号作为分隔符）

返回值：拼接好的字符串

是否改变原数组：不改变


8、concat()

用于连接两个或多个数组

参数：参数可以是具体的值，也可以是数组对象。可以是任意多个

返回值：返回连接后的新数组

是否改变原数组：不改变



9、indexOf()

检测当前值在数组中第一次出现的位置索引

参数：array.indexOf(item,start) item:查找的元素 start:字符串中开始检索的位置

返回值：第一次查到的索引，未找到返回-1

是否改变原数组：不改变




let ary9 = ['a','b','c','d','e','a','f'];   

console.log(ary9.indexOf('c'));//2

console.log(ary9.indexOf('a',3))//5


10、lastIndexOf()

检测当前值在数组中最后一次出现的位置索引

参数：array.lastIndexOf(item,start) item:查找的元素 start:字符串中开始检索的位置

返回值：第一次查到的索引，未找到返回-1

是否改变原数组：不改变




let ary10 = ['a','b','c','d','e','a','f'];   

console.log(ary10.lastIndexOf('c'));//2

console.log(ary10.lastIndexOf('f',1))//-1


11、includes()

判断一个数组是否包含一个指定的值

参数：指定的内容

返回值：布尔值

是否改变原数组：不改变


var ary13 = ['a','b','c','d']; 

console.log(ary13.includes('c'));//true

console.log(ary13.includes(2));//false


12、sort()

对数组的元素进行排序（默认是从小到大来排序 并且是根据字符串来排序的）

参数：可选(函数) 规定排序规则 默认排序顺序为按字母升序

返回值：排序后新数组

是否改变原数组：改变

sort在不传递参数情况下，只能处理10以内（个位数）数字排序



let ary11 = [32,44,23,54,90,12,9]; 

  ary11.sort(function(a,b){        // return a-b;  // 结果[9, 12, 23, 32, 44, 54, 90]

       // return b-a;  // 结果[90, 54, 44, 32, 23, 12, 9]   })  

   console.log(ary11);
   

13、reverse()

把数组倒过来排列

参数：无

返回值：倒序后新数组

是否改变原数组：改变



let ary12 = [6,8,10,12]; 

console.log(ary12.reverse());//[12, 10, 8, 6]


14、forEach()

循环遍历数组每一项

参数：函数 ary.forEach(function(item,index,ary){}) item:每一项 index:索引 ary:当前数组

返回值：无

是否改变原数组：不改变

forEach中不能使用continue和break，forEach中不能跳出，只能跳过(return跳过)

 var ary14 = ['a', 'b', 'c', 'd'];
 var item = ary14.forEach(function (item, index, ary) {
        console.log(item, index, ary);
        //item: 表示当前数组的每一项   a b c d
        //index:表示当前数组的下标：   0 1 2 3
        //arry: 表示当前数组          ['a', 'b', 'c', 'd']
    })
 
 forEache没有返回值，主要用于判断某个值出现的次数
 
 //判断有几个a
    var ary14 = ['a', 'a', 'b', 'c', 'd'];
    var index = 0;
    ary14.forEach(function (item) {
        if (item == 'a') {
            index++;
        }
    })

    console.log(index);//2
    
15、some() 数组中每一项 只要有一个满足条件就返回true

   var arry = [11, 22, 33, 44];

    var bool = arry.some(function (item) {
        return item > 44;
    })

    console.log(bool);

16、every() 数组中每一项 必须全部满足条件就才会返回true

 var arry = [11, 22, 33, 44];

    var bool = arry.every(function (item) {
        return item > 11;
    })

    console.log(bool);
    
17、map() 遍历数组中的没一项 并对数据进行二次的处理 得到一个新数组

  var arry = [11, 22, 33, 44];

    var newArry = arry.map(function (item) {
        // console.log(item);
        return item + 1;
    })

    console.log(arry);
    console.log(newArry);// 12 23 34 45
    
18、filter() 过滤数组中的每一项，把满足条件的内容返回
		
    var arry = [11, 22, 33, 44];
    var newArry = arry.filter(function (item) {
        return item > 22;
    })

    console.log(newArry);//33 44
    
19、reduce()  求和

	  var arry = [11, 22, 33, 44];
    var result = arry.reduce(function (sum, item) {
        return sum + item;
    }, 0)


    console.log(result);//110

```

