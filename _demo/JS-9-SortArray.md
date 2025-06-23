# 数组排序

<!-- #region demo -->

::: details 📝 练习：数组排序

```js
var arr = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]

// 1. 冒泡排序
for (var i = 0; i < arr.length; i++) {
  for (var j = 0; j < arr.length - i; j++) {
    if (arr[j] > arr[j + 1]) {
      var temp = arr[j]
      arr[j] = arr[j + 1]
      arr[j + 1] = temp
    }
  }
}
```

:::

<!-- #endregion demo -->
