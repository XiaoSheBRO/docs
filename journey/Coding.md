# Coding

## 日常踩坑

### _20230824_

#### (Vue3) Vant4 Toast 样式丢失的问题

::: tabs
@tab solution

```js
import 'vant/es/toast/style/index' // 在组件或 main.js 中引入相关样式
```

@tab cause
无法自动引用样式，具体原因未知
:::
