# Coding

## (element/element-plus) `el-button` 的 `.focus` 颜色混淆

::: tabs
@tab solution

阻止以下事件

```vue
<!-- vue3+js -->
<el-button @mousedown="($event) => $event.preventDefault()"></el-button>
<!-- vue3+ts -->
<el-button @mousedown.prevent></el-button>
```

@tab cause
element 无障碍样式 使点击按钮 focus 无法自动失焦，与禁用效果易混淆
:::

## (Vant4) 函数式组件样式丢失

```js
// 在组件或 main.js 中引入相关样式
import 'vant/es/toast/style/index'
```

## (element-plus) 表格分页新写法

```html
<el-pagination
  v-model:page-size="meta.perPage"
  v-model:current-page="meta.currentPage"
  :total="meta.totalCount"
  :page-sizes="[meta.perPage, 20, 50, 100, 200]"
  background
  layout="->, total, sizes, prev, pager, next, jumper"
  @update:current-page="fetchTable"
  @update:page-size="fetchTable"
/>
```

```js
const searchForm = ref({})
const searchFormDefault = JSON.stringify(searchForm.value)
const meta = ref({
  currentPage: 1,
  perPage: 10,
  totalCount: 0,
  pageCount: 0
})
const metaDefault = JSON.stringify(meta.value)
// list
const tableData = ref([])
const fetchTable = () => {
  const params = {
    ...searchForm.value,
    currentPage: meta.value.currentPage,
    perPage: meta.value.perPage
  }
  getTableList(params).then((res) => {
    tableData.value = res.data.list
    meta.value.totalCount = res.data.totalCount
    meta.value.pageCount = res.data.pageCount
  })
}
// search
const handleSearch = () => {
  meta.value.currentPage = 1
  fetchTable()
}
const handleReset = () => {
  searchForm.value = JSON.parse(searchFormDefault)
  meta.value = JSON.parse(metaDefault)
  fetchTable()
}
```

## (element-plus) `el-table` 中 `el-image` 预览样式错乱

```css
/* 添加以下样式 */
:deep(.el-table__cell) {
  position: static !important;
}
```

## (CSS) `flex-warp: warp;` 下元素间距优雅方案

```css
/* 注意兼容性 */
.flex-box {
  gap: 20px;
  gap: 20px 10px; /* row column */
}
```

## (CSS) ios 版本过低(_小于 14.5_)不支持 `flex` 下的 `gap` 属性时，`flex-warp` 替代方案

```css
.container {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(100px, 1fr));
  /* 这意味着每列的最小宽度是100px，并自动换行到下一行，1fr表示剩余空间的等分，如果某个项目的宽度超过了100px，它将占据更多的列以适应自身宽度。 */
  /* 也可定宽 */
  gap: 10px;
}
```

## (CSS) `flex-box` 宽度自适应下单行文本 `text-overflow: ellipsis` 失效解决方法

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
// TODO
:::

## (CSS) `flex-warp: warp;` 下 `warp` 行间距会自适应，定宽方案

```css
.flex-box {
  gap: 10px 10px; /* row column */
  align-content: flex-start;
}
```

## (CSS) 移动端单行文字，多行文字超出显示省略号

### 单行

```css
.box {
  width: 100px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}
```

### 多行

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

## (CSS) 滚动条隐藏

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

## (CSS) 父元素 `flex: 1` 的条件下，子元素宽度与父元素保持一致且不撑开父元素，使文字自动超出隐藏

```css
.icon-banner {
  box-sizing: border-box;
  overflow-x: scroll;
  display: flex;
  margin: 0 24px;
  padding: 32px 10px;
  min-width: 702px;
  height: 180px;
  background-color: red;
  border-radius: 16px 16px 16px 16px;
  gap: 20px;
}

.banner-item {
  position: relative;
  flex-grow: 1;
  flex-shrink: 0;
  display: flex;
  flex-direction: column;
  align-items: center;
  min-width: 148px;
  background-color: #fff;
}

.banner-item .item-icon {
  width: 72px;
  height: 72px;
  margin-bottom: 8px;
}

.banner-item .item-title {
  position: absolute;
  bottom: 0;
  left: 0;
  max-width: 100%;
  min-width: 100%;
  height: 36px;
  font-weight: 400;
  font-size: 26px;
  color: #646466;
  line-height: 36px;
  text-align: center;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
}
```

> 普通文字显示直接在父级加上 `overflow: hidden; text-overflow: ellipsis;` 即可

## (CSS) 多背景图垂直拼接

```css
.container {
  width: 600px;
  min-height: 400px;
  background-image: url('header.png'), url('body.png'), url('footer.png');
  background-repeat: no-repeat;
  background-position:
    left top,
    left 100px,
    left bottom;
  background-size:
    100% 100px,
    100% calc(100% - 100px - 200px),
    100% 200px;
}
```

## (CSS) 标签页效果

```html
<style>
  .container {
    padding: 200px;
    background-color: blue;
  }

  .tab {
    position: relative;
    width: 200px;
    height: 88px;
    border-radius: 18px 18px 0 0;
    background: linear-gradient(180deg, #ffe9ec 0%, #ffffff 100%);
  }

  .tab::before {
    position: absolute;
    left: -75px;
    top: 12px;
    content: '';
    display: block;
    width: 76px;
    height: 76px;
    background: linear-gradient(180deg, #ffe9ec 0%, #ffffff 100%);
    clip-path: polygon(100% 0, 55% 100%, 100% 100%);
  }

  .tab::after {
    position: absolute;
    right: -75px;
    top: 12px;
    content: '';
    display: block;
    width: 76px;
    height: 76px;
    background: linear-gradient(180deg, #ffe9ec 0%, #ffffff 100%);
    clip-path: polygon(0 0, 0 100%, 45% 100%);
  }
</style>
<div class="container">
  <div class="tab"></div>
</div>
```
