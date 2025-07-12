# 数组统计

<!-- #region demo -->

::: details 📝 练习：数组统计

统计数组中出现次数最多的元素及其出现次数

```js
var arr = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]

var count = {}
var maxCount = null
var maxNum = 0

for (var i = 0; i < arr.length; i++) {
  if (count[arr[i]]) {
    count[arr[i]]++
  } else {
    count[arr[i]] = 1
  }
}
for (var key in count) {
  if (count[key] > maxNum) {
    maxCount = key
    maxNum = count[key]
  }
}
```

:::

<!-- #endregion demo -->
