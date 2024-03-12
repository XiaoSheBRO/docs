# Coding

## 日常踩坑

### (Vue3) Vant4 Toast 样式丢失的问题

::: tabs
@tab solution

```js
import 'vant/es/toast/style/index' // 在组件或 main.js 中引入相关样式
```

@tab cause
无法自动引用样式，具体原因未知
:::

### (Vue3) element-plus 分页器新写法

::: tabs
@tab solution

```html
<el-pagination
  background
  :current-page="meta.currentPage"
  layout="->, total, sizes, prev, pager, next, jumper"
  :page-size="meta.perPage"
  :total="meta.totalCount"
  @update:current-page="handleCurrentChange"
  @update:page-size="handleSizeChange" />
```

```ts
const meta = ref({
  currentPage: 1,
  perPage: 10,
  totalCount: 0
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
    totalCount: 0
  }
  fetchTable()
}

const handleReset = () => {
  // searchForm.value = {...}
  meta.value = {
    currentPage: 1,
    perPage: 10,
    totalCount: 0
  }
  fetchTable()
}
```

:::

### (Vue3) element/element-plus `el-button` .focus 颜色问题

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

### (Vue3) element-plus `el-table` 中使用 `el-image` 预览图片样式问题

::: tabs
@tab solution

加上以下样式

```css
:deep(.el-table__cell) {
  position: static !important;
}
```

:::

### (Vue3) :v-deep 弃用

新写法

```css
:deep(.class-name) {
  //...
}
```

### (Css3) `flex-warp: warp;` 下元素间距优雅方案

```css
.flex-box {
  gap: 20px;
  gap: 20px 10px; /* row column */
}
```

### (Css3) `flex-box` 宽度自适应下 `text-overflow: ellipsis` 失效解决方法(单行)

::: tabs
@tab solution

```css
.container {
  display: flex;

  .left {
    flex: 1;
    width: 0;
    white-space: nowrap;
    overflow: hidden;
    word-break: break-all;
    text-overflow: ellipsis;
  }

  .right {
    text-align: right;
    flex-shrink: 0;
  }
}
```

@tab cause
待补充
:::

### (Css3) `flex-warp: warp;` 下 warp 行间距会自适应，定宽方案

```css
.flex-box {
  gap: 10px 10px; /* row column */
  align-content: flex-start;
}
```

### (Css3) ios Safari/webview 页面上下左右边缘`margin`会失效

改用 `padding`

### (Css3) 移动端单行文字，多行文字超出显示省略号

#### 单行

```css
.box {
  width: 100px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```

```css
.box {
  width: 100px;
  height: 100px;
  overflow: hidden;
  text-overflow: ellipsis;
  word-break: break-all;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
}
```

### (Css3) 滚动条隐藏

```scss
.overflow-x-hide-scroll {
  overflow-x: scroll;
  scrollbar-width: none; /* firefox */
  -ms-overflow-style: none; /* IE 10+ */
  &::-webkit-scrollbar {
    display: none; /* Chrome Safari */
  }
}
```

### (Css3) ios 版本过低(小于 14.5)不支持 flex 下的 gap 属性时，flex-warp 动态布局方案

```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
  /* 这意味着每列的最小宽度是100px，并自动换行到下一行，1fr表示剩余空间的等分，如果某个项目的宽度超过了100px，它将占据更多的列以适应自身宽度。 */
  gap: 10px;
}
```

### `line-height = height` 的使用场景

height一定是内容盒的高度，即在box-sizing:content-box的情况下，若为border-box时，此时的height为整个盒子的高度，需要减去padding,border、的尺寸才为真实的内容盒的height。
