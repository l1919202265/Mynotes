watch事件监听

默认浅度监听

只要(data)数据变化就会执行监听,不论是否调用

开启深监听加入deep:true

页面加载完成就监听,设置immediate:true



第一种写法

num(newVal,oldVal){

}



第二种写法

num:{

handler(newVal,oldVal){

​	}

}



computed计算属性

只有调用的时候才会执行

有缓存,相同的结果只执行一次

默认深度监听

一对多监听





methods方法

没有缓存

调用几次执行几次