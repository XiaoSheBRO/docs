# 删除列表

<!-- #region demo -->

::: normal-demo 删除列表

```html
<div class="container">
  <div><button id="clear-btn">清空</button></div>
  <ul class="list">
    <li>1<button>删除</button></li>
    <li>2<button>删除</button></li>
    <li>3<button>删除</button></li>
  </ul>
</div>
<script>
  var clearBtn = document.getElementById('clear-btn')
  var list = document.querySelector('.list')
  clearBtn.onclick = function () {
    list.innerHTML = ''
  }

  var btns = list.querySelectorAll('button')
  for (var i = 0; i < btns.length; i++) {
    var btn = btns[i]
    btn.onclick = function () {
      /* 使用 this，而不是使用 btn，因为 btn 存在声明提升，当点击时，btn 已经变化 */
      var li = this.parentNode
      list.removeChild(li)
    }
  }

  /* 方法二 */
  for (var i = 0; i < btns.length; i++) {
    var btn = btns[i]
    deleteEvent(btn)
  }
  function deleteEvent(btn) {
    /* 固定变量值 */
    btn.onclick = function () {
      var li = this.parentNode
      list.removeChild(li)
    }
  }

  /* 简写 */
  for (var i = 0; i < btns.length; i++) {
    var btn = btns[i]
    /* 立即执行函数 */
    ;(function (btn) {
      btn.onclick = function () {
        var li = this.parentNode
        list.removeChild(li)
      }
    })(btn)
  }
</script>
```

:::

<!-- #endregion demo -->
