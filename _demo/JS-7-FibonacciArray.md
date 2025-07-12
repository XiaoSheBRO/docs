# 斐波那契数组

<!-- #region demo -->

::: details 📝 练习：斐波那契数组

生成给定长度的斐波那契数组

```js
var len = +prompt('请输入斐波那契数组长度：')
if (isNaN(len) || len < 0) {
  alert('请输入正整数！')
} else {
  var arr = []
  for (var i = 0; i < len; i++) {
    if (i === 0 || i === 1) {
      arr[i] = 1
    } else {
      arr[i] = arr[i - 1] + arr[i - 2]
    }
  }
  console.log(arr)
}
```

:::

<!-- #endregion demo -->
