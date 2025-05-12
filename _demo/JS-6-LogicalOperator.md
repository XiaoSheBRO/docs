# 逻辑运算符

<!-- #region demo -->

::: details 📝 练习：逻辑运算符

```js
console.log(true && 100) // 100
console.log(0 && 2) // 0
console.log(1 && 2 && 3 && 4 && 0) // 0
```

```js
var x = 1
console.log(x > 2 && x++ > 0) // false
console.log(x) // 1

var age = -1
age < 0 && (age = 0)
console.log(age) // 0

var y = 1
console.log(y++ >= 1 && y++ >= 2 && y++ >= 4 && y++ >= 4) // false
console.log(y) // 4
```

```js
console.log(1 > 3 || 10) // 10
console.log(undefined || 'abc') // 'abc'
console.log(0 || null || undefined || 1 || NaN) // 1

var user = {
  name: '小明'
}
user.age = user.age || 18
// user.age === undefined && user.age = 18
```

:::

<!-- #endregion demo -->
