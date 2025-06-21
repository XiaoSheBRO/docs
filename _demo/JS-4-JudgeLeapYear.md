# 判断闰年

<!-- #region demo -->

::: details 📝 练习：判断闰年

在变量中存放年份；使用逻辑判断该年是否为闰年。
闰年规则：四年一闰，百年不闰，四百年再闰。

```js
var year = 2009
var result = year % 4 === 0 && (year % 100 !== 0 || year % 400 === 0)
console.log((result && '是闰年') || '不是闰年')
```

:::

<!-- #endregion demo -->
