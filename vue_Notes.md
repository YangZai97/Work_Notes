# Vue笔记
## 数据与方法
* `Object.freeze()` 这会阻止修改现有的属性，也意味着响应系统**无法再追踪变**。
## 条件与渲染
* 当 `v-if` 与 `v-for` 一起使用时，`v-for` 具有比 `v-if` **更高** 的优先级
## 父子组件通信
- 一、父组件往子组件中传值    
---
1、首先先在父组件的html上的 子组件标签上 绑定一个变量 ` ":fatherData" ` 然后找到你需要父组件中的data值`msg1`

```html
<child :fatherData="msg1"></child>
data () {
    return {
      msg1: 'this is fatherData'
    }
  },
```
2、然后在子组件中进行调用，不过在调用之前要定义一个`props: [ ]`,
在props里面填写之前绑定的变量` :fatherData  `。
```js
 props: ['fatherData'],
 ```
 3、然后就可以在子组件中访问到父组件的数据了！
 ```js
  console.log(this.fatherData)
  ```
  ---
  - 二、父组件方法传方法给子组件    

  第一种方法   
  是直接在子组件中通过`this.$parent.xxx`来调用父组件的方法、数据（但是不是提倡用）   

  第二方法   
  1、在父组件里找到子组件标签并定义一个`@Fun1`，参数写子组件需要父组件的方法`Fun2`    
  ```js
  父组件.vue
      <child @fun1="fun2"></child>
```
```js
child.vue
this.$emit('fun1');
```
---
- 三、父组件获取子组件数据、方法

1、子组件 children.vue,我们在子组件中定义了数据`sonData`和方法`sonMethod()`   
```js
// children.vue

<template>
  <div>我是 children</div>
</template>
```
```js
<script>
export default {
  data: () => ({
    sonData: '我是子组件的数据！'
  }),
  methods: {
    sonMethod() {
      console.log('我是子组件的方法！')
    }
  }
}
```    
2、访问子组件数据    
```js
// 父组件

<template>
  <div>
    <children ref='ch'>
    </children>
    <h1 @click="onclick">父组件</h1>
  </div>
</template>
```
```js
import children from './coms/children'
export default {
  data() {
    return {}
  },
  components: {
    children
  },
  methods: {
    onclick() {
    // 或者 let chil = this.$refs['ch']
      let chil = this.$refs.ch
    // 父组件可以通过$refs拿到子组件的对象
    // 然后直接调用子组件的 methods里的方法和data里的数据
      console.log(chil) //子组件对象
      console.log(chil.sonData) // 我是子组件的数据
      console.log(chil.sonMethod()) // 我是子组件的方法
    }
  }
}
```
## 访问根实例方法/数据...
- [$root](https://cn.vuejs.org/v2/guide/components-edge-cases.html#%E8%AE%BF%E9%97%AE%E6%A0%B9%E5%AE%9E%E4%BE%8B)

## 混入（ mixins ）
- [官方文档](https://cn.vuejs.org/v2/guide/mixins.html)
- mixins中的钩子首先执行 [基本用法](https://blog.csdn.net/qq_36838191/article/details/81004590)
## 过滤器
- `|` 过滤器可串联，并且可以在创建vue实例之前定义过滤器（全局过滤器）
## 路由懒加载    
```js
export default new Router({
  routes: [
    {
      path: '/hello',
      name: 'HelloWorld',
      // 懒加载
      component: () => import('@/viem/HelloWorld.vue')
    },
```
- 在点击跳转路由的时候，再进行`import`导入。
## 动态组件注册( is )
- `<component :is="componentId"></component>`     
   - `componentId` 是在data中定义的变量 `null` 
然后需要在进行传参，传入自己需要的组件名（已经导入前提下）
- 例子:    
```html 
<component :is="componentId"></component>
    <button @click="changecomponet('newcom')">New Conponet</button>
    <button @click="changecomponet('newcom2')">New Conponet2</button>
    <button @click="changecomponet('newcom3')">New Conponet3</button>
```
```js
data () {
    return {
      componentId: null,
    }
}
```
```js
methods: {
    changecomponet (name) {
      this.componentId = name
//根据btn传入的值 赋值给componentId 
      console.log(name)
    },
//最后再把componentId传给html中 ，渲染出所需要的组件
```
## Vuex
---

### **store** ### 
- 1、首先在 vue 2.0+ 项目中安装 
 `npm install vuex --save`    
 然后 在src文件目录下新建一个名为 `store` 的文件夹，为方便引入并在 `store` 文件夹里新建一个 `index.js` ,里面的内容如下:     
 ```js
import Vue from 'vue';
import Vuex from 'vuex';
Vue.use(Vuex);
const store = new Vuex.Store();
 
export default store;
```      
- 2、接下来，在 `main.js` 里面引入 `store` ，然后再全局注入一下，这样一来就可以在任何一个组件里面使用 `this.$store` 了：

```js
import store from './store'//引入store
 
new Vue({
  el: '#app',
  router,
  store,//使用store
  template: '<App/>',
  components: { App }
})
```
 - 3、说了上面的前奏之后，接下来就是纳入正题了，就是开篇说的 `state `的玩法。回到  `store` 文件的 `index.js` 里面，我们先声明一个 `state` 变量，并赋值一个空对象给它，里面随便定义两个初始属性值；然后再在实例化的 `Vuex.Store `里面传入一个空对象，并把刚声明的变量 `state` 仍里面：
 ```js
import Vue from 'vue';
import Vuex from 'vuex';
Vue.use(Vuex);
 const state={//要设置的全局访问的state对象
     showFooter: true,
     changableNum:0
     //要设置的初始属性值
   };
 const store = new Vuex.Store({
       state
    });
 
export default store;
// 实际上做完上面的三个步骤后，你已经可以用this.$store.state.showFooter或this.$store.state.changebleNum在任何一个组件里面获取showfooter和changebleNum定义的值了

// this.$store.state.showFooter 
// this.$store.state.changebleNum
```
---
### **getters** ###
- 但这不是理想的获取方式；**Vuex** 官方API提供了一个 `getters` ，和vue计算属性`computed` 一样，来实时监听 `state` 值的变化(最新状态)，并把它也仍进 `Vuex.Store` 里面，具体看下面代码:
```js 
import Vue from 'vue';
import Vuex from 'vuex';
Vue.use(Vuex);
 const state={   //要设置的全局访问的state对象
     showFooter: true,
     changableNum:0
     //要设置的初始属性值
   };
const getters = {   //实时监听state值的变化(最新状态)
    isShow(state) {  //方法名随意,主要是来承载变化的showFooter的值
       return state.showFooter
    },
    getChangedNum(state){  //方法名随意,主要是用来承载变化的changableNum的值
       return state.changebleNum
    }
};
const store = new Vuex.Store({
       state,
       getters
});
export default store;
```
---
### **mutations** ###
- 光有定义的 `state` 的初始值，不改变它不是我们想要的需求，接下来要说的就是 `mutations` 了     
   - `mutattions` 也是一个对象，这个对象里面可以放改变 `state` 的初始值的**方法**
   - 具体的用法就是给里面的方法传入参数 `state` 或额外的参数,然后利用**vue**的双向数据驱动进行值的改变，同样的定义好之后也把这个 `mutations` 扔进 `Vuex.Store` 里面，如下： 
```js
import Vue from 'vue';
import Vuex from 'vuex';
Vue.use(Vuex);
 const state={   //要设置的全局访问的state对象
     showFooter: true,
     changableNum:0
     //要设置的初始属性值
   };
const getters = {   //实时监听state值的变化(最新状态)
    isShow(state) {  //承载变化的showFooter的值
       return state.showFooter
    },
    getChangedNum(state){  //承载变化的changebleNum的值
       return state.changableNum
    }
};
const mutations = {
    show(state) {   //自定义改变state初始值的方法，这里面的参数除了state之外还可以再传额外的参数(变量或对象);
        state.showFooter = true;
    },
    hide(state) {  //同上
        state.showFooter = false;
    },
    newNum(state,sum){ //同上，这里面的参数除了state之外还传了需要增加的值sum
       state.changableNum+=sum;
    }
};
 const store = new Vuex.Store({
       state,
       getters,
       mutations
});
export default store;
//这时候你完全可以用 this.$store.commit('show') 或 this.$store.commit('hide') 以及 this.$store.commit('newNum',6) 在别的组件里面进行改变showfooter和changebleNum的值了，
// ** 这里必须用 commit **
```
---
### **action** ###
- 但这不是理想的改变值的方式；因为在 Vuex 中，`mutations` 里面的方法 都是同步事务，意思就是说：比如这里的一个 `this.$store.commit('newNum',sum)` 方法,两个组件里用执行得到的值，每次都是一样的，这样肯定不是理想的需求。
- 好在vuex官方API还提供了一个 `actions` ，这个 `actions` 也是个对象变量，最大的作用就是里面的 `Action` 方法 可以包含任意异步操作，这里面的方法是用来异步触发 `mutations` 里面的方法，`actions` 里面自定义的函数接收一个 `context` 参数和要变化的形参，`context` 与 `store` 实例具有相同的方法和属性，所以它可以执行 `context.commit(' ')` ,然后也不要忘了把它也扔进 `Vuex.Store`里面：
```js
import Vue from 'vue';
import Vuex from 'vuex';
Vue.use(Vuex);
 const state={   //要设置的全局访问的state对象
     showFooter: true,
     changableNum:0
     //要设置的初始属性值
   };
const getters = {   //实时监听state值的变化(最新状态)
    isShow(state) {  //承载变化的showFooter的值
       return state.showFooter
    },
    getChangedNum(state){  //承载变化的changebleNum的值
       return state.changableNum
    }
};
const mutations = {
    show(state) {   //自定义改变state初始值的方法，这里面的参数除了state之外还可以再传额外的参数(变量或对象);
        state.showFooter = true;
    },
    hide(state) {  //同上
        state.showFooter = false;
    },
    newNum(state,sum){ //同上，这里面的参数除了state之外还传了需要增加的值sum
       state.changableNum+=sum;
    }
};
 const actions = {
    hideFooter(context) {  //自定义触发mutations里函数的方法，context与store 实例具有相同方法和属性
        context.commit('hide');
    },
    showFooter(context) {  //同上注释
        context.commit('show');
    },
    getNewNum(context,num){   //同上注释，num为要变化的形参
        context.commit('newNum',num)
     }
};
  const store = new Vuex.Store({
       state,
       getters,
       mutations,
       actions
});
export default store;
// 而在外部组件里进行全局执行actions里面方法的时候，你只需要用执行  dispatch

// this.$store.dispatch('hideFooter')

// 或this.$store.dispatch('showFooter')

// 以及this.$store.dispatch('getNewNum'，6) //6要变化的实参

// 这样就可以全局改变改变showfooter或changebleNum的值了。
```
---
### **modules** ###
- 因为在大多数的项目中，我们对于全局状态的管理并不仅仅一种情况的需求，有时有多方面的需求，比如写一个商城项目，你所用到的全局state可能是关于购物车这一块儿的也有可能是关于商品价格这一块儿的；像这样的情况我们就要考虑使用vuex中的 `modules` 模块化了。
- 首先，在store文件夹下面新建一个 `modules` 文件夹，然后在 `modules` 文件里面建立需要管理状态的js文件，既然要把不同部分的状态分开管理，那就要把它们给分成独立的状态文件了，如下图：    

    ![avatar](https://image-static.segmentfault.com/651/356/651356550-5b59c0b8969f4)
     - 而对应的store文件夹下面的 `index.js` 里面的内容就直接改写成：      
```js 
     import Vue from 'vue';
     import Vuex from 'vuex';
     import footerStatus from './modules/footerStatus'
     import collection from './modules/collection'
     Vue.use(Vuex);

     export default new Vuex.Store({
      modules:{
        footerStatus,
        collection
     }
    });
```
- 相应的js，其中的 `namespaced:true` 表示当你需要在别的文件里面使用( `mapGetters、mapActions` 接下来会说 )时，里面的方法需要注明来自哪一个模块的方法:
```js
//collection.js

const state={
    collects:[],  //初始化一个colects数组
};
const getters={
  renderCollects(state){ //承载变化的collects
    return state.collects;
  }
};
const mutations={
     pushCollects(state,items){ //如何变化collects,插入items
        state.collects.push(items)
     }
 };
const actions={
    invokePushItems(context,item){ //触发mutations里面的pushCollects ,传入数据形参item 对应到items
        context.commit('pushCollects',item);
    }
};
export default {
     namespaced:true,//用于在全局引用此文件里的方法时标识这一个的文件名
     state,
     getters,
     mutations,
     actions
}
//这样就有了关于两个模块的state管理文件了 footerStatus.js（省略）和collection.js
```
- 然后在组件中 `import { mapActions } from 'vuex'` 就可以使用 `collection` 里 `Actions`的 `invokePushItems` 的方法了
```js
 methods:{
      ...mapActions('collection',[ //collection是指modules文件夹下的collection.js
          'invokePushItems'  //collection.js文件中的actions里的方法，在上面的@click中执行并传入实参
      ])
  }
  // 这样一来，在这个组件里面操作的 collecttion.js 中的state的数据，在其他的任何的一个组件里面都会得到相应的更新变化了
```

