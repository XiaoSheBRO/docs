# JS 执行栈

<!-- #region demo -->

::: details 📍 JS 执行栈

```js
function a() {
  console.log('a start')
  b()
  console.log('a end')
}
function b() {
  console.log('b start')
  console.log('b end')
}
console.log('start')
a()
console.log('end')
```

```mermaid
block-beta
  block:S1
    columns 1
    a["global"]
  end
  space
  block:S2
    columns 1
    c["console.log()"]
    b["global"]
  end
  space
  block:S3
    columns 1
    d["global"]
  end
  space
  block:S4
    columns 1
    f["a()"]
    e["global"]
  end
  space
  block:S5
    columns 1
    i["console.log()"]
    h["a()"]
    g["global"]
  end
  arr1<["..."]>(right)
  block:S6
    columns 1
    l["b()"]
    k["a()"]
    j["global"]
  end
  arr2<["..."]>(right)
  block:S7
    columns 1
    p["console.log()"]
    o["global"]
  end
  space
  block:S8
    columns 1
    q["global"]
  end

  S1 --> S2
  S2 --> S3
  S3 --> S4
  S4 --> S5
  S7 --> S8
```

:::

<!-- #endregion demo -->
