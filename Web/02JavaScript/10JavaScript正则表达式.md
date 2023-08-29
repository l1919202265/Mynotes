## 正则表达式

语法：

```javascript
//构造函数：
var reg=new RegExp(pattern),modifiers;
如：
				 //校验规则//修饰符
var reg=new RegExp('[a-z]*','g');
var str='hello';
console.log(reg.test(str));



//字面量：
var reg=/pattern/modifiers;

如：
var str='hello';
var reg=/[a-z]/i;
console.log(reg.test(str));
```

#### 修饰符：

| 修饰符 | 描述                                                   |
| ------ | ------------------------------------------------------ |
| i      | 执行对大小写不敏感的匹配                               |
| g      | 执行全局匹配(查找所有匹配而非在找到第一个匹配后停止)。 |
| m      | 执行多行匹配                                           |

#### 常用的表达式

| 表达式 | 描述                                                         |
| ------ | ------------------------------------------------------------ |
| [a-z]  | 查找任何从小写a到小写z的字符 -表示区间                       |
| [A-Z]  | 查找任何从大写A到大写Z的字符                                 |
| [0-9]  | 查找任何从0至9的数字                                         |
| [abc]  | 查找括号内的任意一个字符                                     |
| [^abc] | 查找除了括号内的任意字符。除了abc如果还有其他任意字符为true，否则false |

#### 常用的元字符(特殊字符)

| 字符 | 描述                     |
| ---- | ------------------------ |
| \w   | 匹配数字、字母、下划线   |
| \W   | 匹配非数字、字母、下划线 |
| \d   | 匹配数字                 |
| \D   | 匹配非数字               |
| \s   | 匹配空白字符(空格、换行) |
| \S   | 匹配非空白字符           |
| \n   | 匹配换行符               |

#### 常用的限定字符

| 字符  | 描述                         |
| ----- | ---------------------------- |
| *     | 匹配前面的子表达式零次或多次 |
| +     | 匹配前面的子表达式一次或多次 |
| ?     | 匹配前面的子表达式零次或一次 |
| {n}   | 匹配确定的n次                |
| {n,}  | 至少匹配n次                  |
| {n,m} | 最少匹配n次且最多匹配m次     |
| ^     | 以某某开头                   |
| $     | 以某某结尾                   |
| \     | 转义字符                     |

*零次或者多次

```js
var str = 'abcd';

//var reg = /[a-z]*/;// a-z 出现0 次 或者多次
var reg = /\w*/;// 字母｜数字｜下划线 出现0 次 或者多次
console.log(reg.test(str));  //true
```
 +	一次或者多次

```js
var str = 'abcd';
// var reg = /[0-9]+/;// 0-9 出现1次 或者多次
var reg = /\d+/;// 数字出现 1次 或者多次
console.log(reg.test(str));  //false
```
？0次或者1次




```js
   var str = '12';
   var reg = /^\d?$/;// 以数字开始结束  数字出先0次或者1次
   console.log(reg.test(str));  //false
var str = '1';

var reg = /^\d?$/;// 以数字开始结束  数字出先0次或者1次
console.log(reg.test(str));  //true
```
{n},固定的n次 ，要和开始结束结合使用



```js
  // var str = 'a';//false
    var str = 'ab';//true
    var str = 'abc';//false

    var reg = /^\w{2}$/;//字母数字下划线 从开始到结束 只能出现2次
    console.log(reg.test(str));
```
{n,}  至少匹配n 次

```js
var str = 'a';//false
// var str = 'ab';//true
// var str = 'abc';//true

// var reg = /^\w{2,}$/;//至少出现两次
var reg = /\w{2,}/;//至少出现两次
console.log(reg.test(str));
```
{n,m}  最少匹配 n 次且最多匹配 m 次



```js
 var str = 'a';//false
    // var str = 'ab';//true
    // var str = 'abc';//true
    // var str = 'abcd';//false
var reg = /^\w{2,3}$/;//至少出现两次，最多出现3次
console.log(reg.test(str));
```
\  转义字符

```js
// var str = 'a.com';//true
var str = 'acom';//false
var reg = /\./;// 转义 判断是否包含 .
console.log(reg.test(str));
```
```js
  var phone =13140172111;
    // var reg = /^1[3-9][0-9]{9}$/;
    var reg = /^1[3-9][0-9]{9}$/;
    console.log(reg.test(phone));
```

匹配以a开头，以d结尾：

```js
var str = 'abcd';
var reg = /^[a]\w*[d]$/;
console.log(reg.test(str));
```


## 正则表达式方法

检测一个字符串是否与正则相匹配
reg.test(string)           返回值为布尔值 true匹配，false不匹配
reg.exec(string)          匹配成功返回数组，并确定其位置，否则返回null 

​                                      只返回匹配到的第一个内容  包含 查找的值 对应的下标



示例：

```js
var str="abc";
var reg=/[a-z]/;   var reg=/[A-Z]/;
console.log(reg.test(str));  
console.log(reg.exec(str));

```




### String对象中可以支持正则表达式的方法

| 方法    | 描述                                                         |
| :------ | ------------------------------------------------------------ |
| search  | 检索与正则表达式相匹配的值。查找不到返回-1，查到返回第一个匹配到的下标 |
| match   | 检索一个或多个正则表达式的匹配，如果没有找到任何匹配的文本，返回null。否则它将返回一个数组(依赖于是否有全局标识 g) |
| replace | 替换与正则表达式匹配的子串 返回一个新的字符串                |
| split   | 把字符串分割为字符串，返回一个字符串数组                     |

```js
 var str = 'hello WorLd';
    var reg = /[A-Z]/;
    console.log(str.search(reg));//6 下标
```

```js
 var str = 'hello WorLd';
    var reg = /[A-Z]/g;
    console.log(str.match(reg));//[W,L] 是否返回数组 取决于正则是否加了g
```

```JS
 var str = 'helloWorLd';
    var reg = /[A-Z]/;
    console.log(str.split(reg));//["hello", "or", "d"]
```

```js
  var str = 'helloWorLd';
    var reg = /[A-Z]/;

    console.log(str.replace(reg,'*'));//hello*orLd
```


## 正则验证



验证26个英文字母组成的字符串
验证由数字和26个英文字母组成的字符串
验证由数字、字母、下划线组成的字符串
验证汉字   var reg=/^[\u4e00-\u9fa5]+$/



```js
  // 验证26个英文字母组成的字符串
    var str = 'jdjEEdjowdl';
    var reg = /^[a-zA-Z]+$/g
    console.log(reg.test(str));

    // 验证由数字和26个英文字母组成的字符串
    var str1 = 'jdjd98765EEdjowdl';
    var reg1 = /^[0-9a-zA-Z]+$/
    console.log(reg1.test(str1));

    // 验证由数字、字母、下划线组成的字符串
    var str2 = 'jd_jEEdjo_wdl';
    var reg2 = /\w/
    console.log(reg2.test(str2));

    // 验证汉字    var reg = /^[\u4e00-\u9fa5]+$/
    var str3 = '老陈你好';
    var reg3 = /^[\u4e00-\u9fa5]+$/g;
    console.log(reg3.test(str3));
```



## 使用正则验证空格、手机号及邮箱

**需求说明:**
使用正则验证如下需求
首尾有空格的字符串（分别验证清除前面、后面、前后以及所有空格的方法）
验证手机号码
验证邮箱



清除空格：

```js
  // 首尾有空格的字符串（分别验证清除前面、后面、前后以及所有空格的方法）
    //为了演示看起来直观，我们把清除替换成*

    var  str = '  nihao  hehe  shijie  llala  ';

    // 清除前面
    // var reg = /^\s+/;

    //清除后面
    // var reg = /\s+$/;

    //清除前面和后面
    // var reg = /^\s|\s$/g;

    //清除全部
    var reg = /\s+/g;
    
    console.log(str);
    console.log(str.replace(reg,'*'));
```



验证手机号码:

```js
  //验证手机号
    var phone = 13140172555;
    var reg = /^1[3-9][0-9]{9}$/;  //此时的{9}限制的是前面[0-9]这个字表达式
    console.log(reg.test(phone));
```

邮箱正则：

```js
 //验证邮箱
    var email = '4732chenfuuo_@qq.com';
    // var email = '4732chenfuuo_@qq.com.cn';
    var reg = /^\w+@\w+(\.[a-z]{2,3}){1,2}$/

```



## 符串中的数字加上中括号

需求说明
使用正则给如下字符串中的数字加上中括号
var str='abc345efg';


```js
  var str='abc345efg';
  document.write(str.replace(/(\d)/g,'[$1]'));
```





正则在线测试工具: https://regexr-cn.com/

正则练习: https://codejiaonang.com/