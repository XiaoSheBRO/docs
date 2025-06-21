# CSS 实现自定义单选 / 多选

<!-- #region demo -->

::: normal-demo CSS 实现自定义单选 / 多选

```html
<style>
  .radio-item .radio {
    display: inline-block;
    width: 12px;
    height: 12px;
    border-radius: 50%;
    border: 1px solid #ccc;
    cursor: pointer;
  }
  .radio-item input:checked + .radio {
    border-color: #007bff;
  }
  .radio-item input:checked + .radio::after {
    display: block;
    content: '';
    width: 4px;
    height: 4px;
    margin-top: 4px;
    margin-left: 4px;
    border-radius: 50%;
    background-color: #007bff;
  }
  .radio-item input:checked ~ span {
    color: #007bff;
  }
  .radio-item input[type='radio'] {
    display: none;
  }
</style>
<div>
  性别：
  <label class="radio-item">
    <input type="radio" name="gender" value="男" />
    <span class="radio"></span>
    <span>男</span>
  </label>
  <label class="radio-item">
    <input type="radio" name="gender" value="女" />
    <span class="radio"></span>
    <span>女</span>
  </label>
</div>
```

:::

<!-- #endregion demo -->
