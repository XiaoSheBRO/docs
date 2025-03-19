# 不同厂商的滚动条样式定义

<!-- #region demo -->

::: normal-demo 不同厂商的滚动条样式定义

```html
<style>
  .scroll-view {
    margin: 0 auto;
    width: 200px;
    height: 100px;
    overflow: auto;
  }
  /* chrome, safari */
  .scroll-view::-webkit-scrollbar {
    width: 10px;
    height: 10px;
  }
  /* firefox */
  /* todo */
  .content {
    height: 1000px;
  }
</style>
<div>
  <div class="scroll-view">
    <div class="content"></div>
  </div>
</div>
```

:::

<!-- #endregion demo -->
