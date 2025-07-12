# 二维数组对角线元素之和

<!-- #region demo -->

::: details 📝 练习：二维数组对角线元素之和

计算 5x5 二维数组的对角线元素之和

```js
var arr = [
  [1, 2, 3, 4, 5],
  [6, 7, 8, 9, 10],
  [11, 12, 13, 14, 15],
  [16, 17, 18, 19, 20],
  [21, 22, 23, 24, 25]
]
var sum = 0
for (var i = 0; i < arr.length; i++) {
  for (var j = 0; j < arr[i].length; j++) {
    if (i === j || i + j === arr.length - 1) {
      if (i === 3) {
        continue
      }
      sum += arr[i][j]
    }
  }
}
console.log(sum)
```

:::

<!-- #endregion demo -->
