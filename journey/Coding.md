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

#### (Vue3) element-plus 分页器新写法

::: tabs
@tab solution

```html
<el-pagination
  background
  :current-page="meta.currentPage"
  layout="->, total, sizes, prev, pager, next, jumper"
  :page-size="meta.perPage"
  :total="meta.totalCount"
  @update:current-page="handleCurrentChange()"
  @update:page-size="handleSizeChange()" />
```

```ts
const meta = ref({
  currentPage: 1,
  perPage: 10,
  totalCount: 0,
})
const handleSizeChange = (val: any) => {
  meta.value.perPage = val
  fetchTable()
}
const handleCurrentChange = (val: any) => {
  meta.value.currentPage = val
  fetchTable()
}

const handleSearch = () => {
  meta.value = {
    currentPage: 1,
    perPage: 10,
    totalCount: 0,
  }
  fetchTable()
}

const handleReset = () => {
  // searchForm.value = {...}
  meta.value = {
    currentPage: 1,
    perPage: 10,
    totalCount: 0,
  }
  fetchTable()
}
```

:::

#### element/element-plus `el-button` .focus 颜色问题

::: tabs
@tab solution

加上以下事件

```html
<!-- vue3+js -->
<!-- <el-button @mousedown="($event) => $event.preventDefault()"></el-button> -->
<!-- vue3+ts -->
<el-button @mousedown.prevent></el-button>
```

@tab cause
element 无障碍样式 使点击按钮 focus 无法自动失焦，与禁用效果易混淆
:::

#### element-plus `el-table` 中使用 `el-image` 预览图片样式问题

::: tabs
@tab solution

加上以下样式

```css
:deep(.el-table__cell) {
  position: static !important;
}
```

:::

#### :v-deep 弃用

新写法

```css
:deep(.class-name) {
  //...
}
```
