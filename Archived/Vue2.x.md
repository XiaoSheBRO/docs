# VUE 基础教程

## Vue

以 vue 为后缀的文件是 vue 的单文件组件
可以把组件理解成一个，可以自定义的，有更强大功能的标签
链接：html 的 a 标签
登录：.vue 组件，登录
轮播图·.vue 组件，轮播图
这样用组件拆分的方式开发项目，思路清晰，简洁高效，而且还可以复用相同的组件

### 引入方式

- 直接引入 vue.js 文件
  - Vue2.x cdn:`<script src="https://cdn.jsdelivr.net/npm/vue@2.7.8/dist/vue.js"></script>`
- 基于 Node 环境创建 Vue 项目（使用 vue/cli 创建初始化一个 Vue 项目）

### hello world

创建 Vue 实例：

```html
<script>
  new Vue({
    el: '...', // 绑定网页元素(包含所有子集)，相当于获取DOM节点
    data: {
      // 绑定数据
    },
    methods: {
      // 绑定函数
    }
  })
</script>
```

绑定文本：`{{文本表达式}}` (_可写 js 表达式_)
绑定属性：`v-bind:属性="..."` **简写**：`:属性="..."`
绑定事件：`v-on:事件类型="方法"` **简写**：`@事件类型="方法"`

> `事件类型.stop` 阻止事件冒泡

## 环境搭建

安装 vue 命令行工具： `npm install -g @vue/cli`
创建项目：`vue create 项目名`
启动项目：`npm run serve`

## 项目结构

《\*.vue》：vue 的单文件组件

> 组件化开发：用组件拆分的方式开发项目，思路清晰，简洁高效，还可以复用相的组件，降低了功能的耦合，但是增加了数据传输的难度

```js
// main.js
/* import 引入模块 */
Vue.config.productionTip = false
//配置开发选项，false:友好的错误提示 true:无错误提示
new Vue({
  render: (h) => h(App) //箭头函数，传入组件并渲染
}).$mount('#app') //挂载到#app
```

```vue
/* App.vue */
<template>
  <!-- 网页模板 -->
  <div id="app">
    <!-- 最外层只能暴露一个标签 -->
  </div>
</template>

<script>
// js代码
/* import 引入模块 */
export default {
  // 暴露接口
  components: {
    // 注册组件
  },
  name: 'App',
  data() {
    // node下 data 为函数形式
    return {}
  },
  methods: {}
}
</script>

<style>
/* css代码 */
#app {
}
</style>
```

> `<style scoped></style>` scoped-只有当前组件能用

## 模板语法

### 元素可见性

`v-if="false"` 不渲染 DOM
`v-show="false"` 渲染 DOM，将元素隐藏

根据列表项动态生成：
`v-for="(元素, 序号) of list" :key="序号"`
定义后可直接调用该列表属性

## 组件嵌套

组件命名规则：首字母大写，驼峰，不要与 html 标签重名
网页内引入标签时不区分大小写，若为驼峰命名还可以在单词中间加`-`

### 组件传值

**父级向子级传递数据**：App.vue => \*.vue (_使用属性传递_)

```html
<!-- 父级 -->
<child-app :msg="message"></child-app>
<!-- 将数据绑定到子级 -->
<script>
  data() {
    return {
      message: "child", // 在data中定义数据
    };
  }
  /* 子级 */
  export default {
    props: ["msg"], // 继承数据
  };
</script>
```

**子级向父级传递数据**：\*.vue => App.vue (_自定义事件_)
`this.$emit("事件名", 待传输数据);`

```html
<script>
  <!-- 子级 -->
    data() {
      return {
        myData: "hi, i'm child",
      };
    },
    methods: {
      sendData() {
        this.$emit("event", this.myData);
      },
    }
</script>
<child-app @event="getData"></child-app>
<script>
  <!-- 父级 -->
    data() {
      return {
        childData: ""
      }
    }
    methods: {
      getData(Data) {
        this.childData = Data;
      }
    }
</script>
```

**非父子级数据共享**：《store.js》

```js
export default {
  state: {
    message: 'hello vue' // 共享的数据
  },
  setStateMessage(str) {
    this.state.message = str // set方法
  }
}
```

## 计算属性

多个值改变，影响一个结果时使用

```js
computed: {
  // 进行？纯计算？的属性
}
```

## 侦听器

一个值变化影响多个值时，使用侦听器

```js
watch:{
  x(val){
    // 绑定data中的值，当x的值发生变化时执行的函数
  }
}
```

## 生命周期钩子

> 不能使用箭头函数
> 为了避免杂乱，可以先在 methods 里写好方法，然后再在生命周期函数里调用

在页面加载时主动执行程序
![1659278793981](../../assets/images/1659278793981.png)
![生命周期](../../assets/images/20200204152241.png)

```js
created(){
  // 一般用于初始化数据
}
// 加载 html 模板
mounted(){
  // 一般用于操作 html 元素
}
```

## 插槽

实现子级组件标签内自定义
让我们更灵活地使用自定义组件，增强组件的扩展性，组件库基本基于插槽

- 子级自定义组件：`<slot>待自定义部分</slot>`
- 父级 App.vue：`<...>自定义文本</...>`

**具名插槽**：

- 父级：`<app><template v-slot:1></template></app>`
- 子级：`<slot name="1"></slot>`

## 获取真实 DOM

`window.getComputedStyle(dom节点).样式属性`

- 用原生 js 获取 dom(_注意获取 dom 的时间节点_)
  属性：`ref="*"` 其 dom 节点为：`this.$refs.*`

> Vue 应用开发的过程中，大部分情况是不需要获取真实 DOM 的
> Vue 中的数据变化，并不是直接改变 DOM，而是通过改变虚拟 DOM，并计算变更差异，进而修改 DOM 中有变化的内容，提升性能
> ![1659338915119](../../assets/images/1659338915119.png)

## 过滤器

通过固定算法重新组织数据

```js:no-v-pre
<div>{ { str | split } }</div>
filters:{
  split(str){
    return str.split("").join();
  }
}
```

## 表单

`@submit.prevent` 取消表单提交默认刷新页面

### 数据双向绑定

`v-model="数据名"`

#### 修饰符

- `.number` 自动转为 Number 类型(_如果原值的转换结果为 NaN 则返回原值_)
- `.trim` 自动过滤用户输入的首尾空格
- `.lazy` 将 v-model 在 input 事件中同步输入框的数据转变为在 change 事件中同步数据

### 数据交互

http 协议：前端（浏览器）发送请求，服务器给予响应。
请求方法：get（查询）、post（添加）、put（修改）、delete（删除）
ajax：不刷新页面与后台交互数据。
axios：封装好的 aja× 模块。

### 路由

`<router-link to="url"><router-link>`
`<router-view/>`

```js
import { createRouter, createWebHistory } from 'vue-router'
import HomeView from '../views/HomeView.vue'

const router = createRouter({
  history: createWebHistory(import.meta.env.BASE_URL),
  routes: [
    {
      path: '/',
      name: 'home',
      component: HomeView
    },
    {
      path: '/about',
      name: 'about',
      // lazy-loaded
      component: () => import('../views/AboutView.vue')
    }
  ]
})

export default router
```

#### 路由传参

`v-for`
`/url/:param`

### 本地存储

### 导航守卫

```js
router.beforeEach((to, from, next) => {})‘
// 去向
// 来源
// 跳转操作
```

option
setup
