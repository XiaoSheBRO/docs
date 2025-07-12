# 函数练习

<!-- #region demo -->

::: details 📝 练习：函数练习

```js
/**
 * 判断一个数组是否是稀松数组
 * @param {Array} arr 数组
 * @return {Boolean} 是否是稀松数组
 */
function isSparseArray(arr) {
  for (let i = 0; i < arr.length; i++) {
    if (!(i in arr)) {
      return true
    }
  }
  return false
}
```

:::

<!-- #endregion demo -->
