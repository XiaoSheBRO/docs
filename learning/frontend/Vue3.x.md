# Vue3.x

## 搭建

## 模板语法

`v-text` 绑定文本  
`v-for = "item,index in list"`

## 生命周期

beforeCreate 没有数据，方法  
created 有数据，方法，没挂载-无 dom  
beforeMount 有数据，方法，没挂载-无 dom  
mounted 有数据，有 dom

## 自定义指令 `v-name`

```js
app.directive("name", {
  生命周期函数(原生dom节点) {
    ...
  }
})
```

## 组件化和模块化

组件 - 页面拆分  
模块 - 功能拆分

## 动态组件

`<component is = "*"></component>`

## option api 选项 api

## composition api 组合 api

```js
export default {
  setup() {
    // 定义数据、函数
    return {
      // 暴露数据、函数
    }
  },
}
```

### 响应式

`import {ref, reactive } from "vue"`  
`ref()` 转变字符串  
`reactive()` 转变对象

```js
import { ref, reactive } from 'vue'
let x = ref('0') // 转为响应式变量
x.value = '1' // 改变值
const y = reactive({ id: 1, name: '1' })
y.name = '2'
```

### 生命周期钩子

`import {} from "vue"`

~~`beforeCreate` `created`~~ 被`setup`代替(_setup 运行时机_)

其他加`on`前缀

```js
onMounted(() => {

}),
```

### 计算属性

`import {computed} from "vue"`

```js
const number = computed(() => {
  return number + 1
})
```

> 组合 api 的优势
>
> - 优化逻辑
> - 抽离功能模块
