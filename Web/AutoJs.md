## 基于坐标的触摸模拟

------

1. click(x,y)

   ```js
   x {number} 要点击的坐标的x值
   y {number} 要点击的坐标的y值
   模拟点击坐标(x, y), 并返回是否点击成功. 只有在点击执行完成后脚本才继续执行.
   
   一般而言, 只有点击过程(大约150毫秒)中被其他事件中断(例如用户自行点击)才会点击失败.
   
   使用该函数模拟连续点击时可能有点击速度过慢的问题, 这时可以用press()函数代替.
   ```

2. ## longClick(x, y)

   ```js
   x {number} 要长按的坐标的x值
   y {number} 要长按的坐标的y值
   模拟长按坐标(x, y), 并返回是否成功. 只有在长按执行完成（大约600毫秒）时脚本才会继续执行.
   
   一般而言, 只有长按过程中被其他事件中断(例如用户自行点击)才会长按失败.
   ```

3. ## press(x, y, duration)

   ```js
   x {number} 要按住的坐标的x值
   y {number} 要按住的坐标的y值
   duration {number} 按住时长, 单位毫秒
   模拟按住坐标(x, y), 并返回是否成功. 只有按住操作执行完成时脚本才会继续执行.
   
   如果按住时间过短, 那么会被系统认为是点击；如果时长超过500毫秒, 则认为是长按.
   
   一般而言, 只有按住过程中被其他事件中断才会操作失败.
   
   一个连点器的例子如下：
   
   //循环100次
   for(var i = 0; i < 100; i++){
     //点击位置(500, 1000), 每次用时1毫秒
     press(500, 1000, 1);
   }
   ```

4. ## swipe(x1, y1, x2, y2, duration)

   ```js
   x1 {number} 滑动的起始坐标的x值
   y1 {number} 滑动的起始坐标的y值
   x2 {number} 滑动的结束坐标的x值
   y2 {number} 滑动的结束坐标的y值
   duration {number} 滑动时长, 单位毫秒
   模拟从坐标(x1, y1)滑动到坐标(x2, y2), 并返回是否成功. 只有滑动操作执行完成时脚本才会继续执行.
   
   一般而言, 只有滑动过程中被其他事件中断才会滑动失败.
   ```

5. ## gesture(duration, [x1, y1\], [x2, y2], ...)

   ```js
   duration {number} 手势的时长
   [x, y] ... 手势滑动路径的一系列坐标
   模拟手势操作. 例如gesture(1000, [0, 0], [500, 500], [500, 1000])为模拟一个从(0, 0)到(500, 500)到(500, 100)的手势操作, 时长为2秒.
   ```

6. ## gestures([delay1, duration1, [x1, y1\], [x2, y2], ...], [delay2, duration2, [x3, y3], [x4, y4], ...], ...)

   ```js
   同时模拟多个手势. 每个手势的参数为[delay, duration, 坐标], delay为延迟多久(毫秒)才执行该手势；duration为手势执行时长；坐标为手势经过的点的坐标. 其中delay参数可以省略, 默认为0.
   
   例如手指捏合：
   
   gestures([0, 500, [800, 300], [500, 1000]],
            [0, 500, [300, 1500], [500, 1000]]);
   ```

7. # RootAutomator

   ```js
   RootAutomator是一个使用root权限来模拟触摸的对象, 用它可以完成触摸与多点触摸, 并且这些动作的执行没有延迟.
   
   一个脚本中最好只存在一个RootAutomator, 并且保证脚本结束退出他. 可以在exit事件中退出RootAutomator, 例如：
   
   var ra = new RootAutomator();
   events.on('exit', function(){
     ra.exit();
   });
   //执行一些点击操作
   ...
   ```

8. RootAutomator.tap(x, y[, id\])

```js
x {number} 横坐标
y {number} 纵坐标
id {number} 多点触摸id, 可选, 默认为1, 可以通过setDefaultId指定.
点击位置(x, y). 其中id是一个整数值, 用于区分多点触摸, 不同的id表示不同的"手指", 例如：

var ra = new RootAutomator();
//让"手指1"点击位置(100, 100)
ra.tap(100, 100, 1);
//让"手指2"点击位置(200, 200);
ra.tap(200, 200, 2);
ra.exit();

如果不需要多点触摸, 则不需要id这个参数. 多点触摸通常用于手势或游戏操作, 例如模拟双指捏合、双指上滑等.

某些情况下可能存在tap点击无反应的情况, 这时可以用RootAutomator.press()函数代替.9.9.RootAutomator.swipe(x1, x2, y1, y2[, duration, id\])
```

​	9.RootAutomator.swipe(x1, x2, y1, y2[, duration, id\])

```js
x1 {number} 滑动起点横坐标
y1 {number} 滑动起点纵坐标
x2 {number} 滑动终点横坐标
y2 {number} 滑动终点纵坐标
duration {number} 滑动时长, 单位毫秒, 默认值为300
id {number} 多点触摸id, 可选, 默认为1
模拟一次从(x1, y1)到(x2, y2)的时间为duration毫秒的滑动.
```

10.RootAutomator.press(x, y, duration[, id\])

```js
x {number} 横坐标
y {number} 纵坐标
duration {number} 按下时长
id {number} 多点触摸id, 可选, 默认为1
模拟按下位置(x, y), 时长为duration毫秒.
```

