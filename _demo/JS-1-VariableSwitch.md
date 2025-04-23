# 变量交换

<!-- #region demo -->

::: details 📝 练习：变量交换

```html
<script>
  var a = 1
  var b = 2
  var temp = a
  a = b
  b = temp
  console.log(a, b) // 2 1
</script>
<script>
  // 交换 parent 和 child 属性，但不创建新的对象
  var item = {
    name: '123',
    parent: {
      name: '456'
    },
    child: {
      name: '789'
    }
  }
  var temp = item.parent
  item.parent = item.child
  item.child = temp
</script>
```

:::

<!-- #endregion demo -->
