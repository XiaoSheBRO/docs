# 归档

## (Vue3) Vant4: 函数式样式

```js
// 在组件或 main.js 中引入相关样式
import 'vant/es/toast/style/index'
```

## (Vue3) element-plus 分页器新写法

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

## (Vue3) `:v-deep` 弃用后的新写法

```css
:deep(.class-name) {
  /* ... */
}
```
