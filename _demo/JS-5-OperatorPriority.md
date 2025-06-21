# 运算符优先级

<!-- #region demo -->

::: details 📝 练习：运算符优先级

```js
var x = 1
var y = x++ + 1 // 1 + 1
console.log(y) // 2
console.log(x) // 2
```

```js
typeof 1 / 0 // typeof 优先级高于 /
// "number" / 0
// NaN / 0
// NaN
```

```js
var x = 1
var y = x + x++ * ++x + x
// 1 + x++ * ++x + x
// 1 + 1 * ++x + x // x ==> 2
// 1 + 1 * 3 + x // x ==> 3
// 1 + 3 + x
// 4 + x
// 7
```

```js
var x = 1
var y = x + x++ * (x = x + x++ * ++x) + x
// 1 + x++ * (x = x + x++ * ++x) + x
// 1 + 1 * (x = x + x++ * ++x) + x // x ==> 2
// 1 + 1 * (x = 2 + x++ * ++x) + x
// 1 + 1 * (x = 2 + 2 * ++x) + x // x ==> 3
// 1 + 1 * (x = 2 + 2 * 4) + x // x ==> 4
// 1 + 1 * (x = 2 + 8) + x
// 1 + 1 * (x = 10) + x
// 1 + 10 + x // x ==> 10
// 11 + x
// 21
```

:::

<!-- #endregion demo -->
