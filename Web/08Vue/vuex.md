vuex是一个专为vue.js应用程序的**状态管理模式**;采用集中式存储管理应用的所有的组件的状态,并以相应的规则保证状态以一种可预测的方式发生变化

【自己的话： vuex是vue程序中的一个状态管理模式，他可以把所有组件需要共享的数据，统一进行管理，如果想要修改的时候，需要按照vuex中定义好的规则进行修改】

数据就是状态

一个数据需要在多个组件里面共享的时候，我们可以把这个数据放在vuex中

##### vuex的安装和使用

```css
安装适配vue2的vuex
npm install vuex@3 --save
    
新建文件夹store,store目录下新建index.js文件,index内配置vuex
import Vue from 'vue',
import Vuex from 'vuex',
Vue.use(Vuex)
export default new Vuex.store({})

main.js内导入vuex
import store from './store/index.js'
new Vue({
  router,
  store,
  render: function (h) {
    return h(App)
  }
}).$mount('#app')
```

