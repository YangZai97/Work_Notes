# Vue笔记
## 数据与方法
* `Object.freeze()` 这会阻止修改现有的属性，也意味着响应系统**无法再追踪变**。
## 条件与渲染
* 当 `v-if` 与 `v-for` 一起使用时，`v-for` 具有比 `v-if` **更高** 的优先级
## 父子组件通信
- 一、子组件获取父组件数据    
---
1、首先先在父组件的html上的 子组件标签上 绑定一个变量 ` ":fatherData" ` 然后找到你需要父组件中的data值`msg1`

```js
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
  - 二、子组件获取父组件方法    

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
```js 
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
