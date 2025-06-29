# 回调函数

<!-- #region demo -->

::: details 📝 练习：回调函数

```js
/**
 * 自定义数组排序
 * @param {Array} arr 数组
 * @param {Function} compare 比较函数，接收两个参数，返回负数 / 0 / 正数
 * @returns {Array} 排序后的数组
 */
var arrSort = function (arr, compareFn) {
  if (!compareFn) {
    /* 默认比较函数 */
    compareFn = function (a, b) {
      if (a < b) {
        return -1
      } else if (a > b) {
        return 1
      } else {
        return 0
      }
    }
  }
  for (let i = 1; i < arr.length; i++) {
    for (let j = 0; j < arr.length - i; j++) {
      if (compareFn(arr[j], arr[j + 1]) > 0) {
        let temp = arr[j]
        arr[j] = arr[j + 1]
        arr[j + 1] = temp
      }
    }
  }
}

var compare = function (a, b) {}
```

:::

<!-- #endregion demo -->
