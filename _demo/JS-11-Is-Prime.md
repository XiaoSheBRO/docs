# 判断素数

<!-- #region demo -->

::: details 📝 练习：判断素数

判断一个数是否是素数

```js
function isPrime(num) {
  if (num < 2) {
    return false
  }
  for (let i = 2; i < num - 1; i++) {
    if (num % i === 0) {
      return false
    }
  }
  return true
}
```

:::

<!-- #endregion demo -->
