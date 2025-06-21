# Chrome 滚动条样式定义

<!-- #region demo -->

::: normal-demo Chrome 滚动条样式定义（FireFox 不兼容）

```html
<style>
  .scroll-view {
    margin: 0 auto;
    width: 400px;
    height: 150px;
    overflow: auto;
    background-color: #f5f5f5;
  }
  .scroll-view::-webkit-scrollbar {
    /* 总体样式，设置后不在使用默认样式 */
    width: 10px;
    background-color: lightblue;
  }
  .scroll-view::-webkit-scrollbar-track {
    /* 轨道样式 */
    background-color: red;
  }
  .scroll-view::-webkit-scrollbar-thumb {
    /* 滑块样式 */
    background-color: green;
    border-radius: 15px;
  }
  .scroll-view::-webkit-scrollbar-button {
    /* 按钮样式 */
    background-color: blue;
  }
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
