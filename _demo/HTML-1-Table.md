# 表格元素示例

<!-- #region demo -->

::: normal-demo 表格元素示例

```html
<style>
  table {
    border-collapse: collapse; /* 合并边框 */
  }
  th,
  td {
    padding: 5px;
    border: 1px solid #ddd;
  }
</style>
<table>
  <caption>
    表格标题
  </caption>
  <!-- thead 表头 -->
  <thead>
    <tr>
      <!-- th 可出现在表格的任何位置，默认样式为文字加粗居中 -->
      <th>标题单元格</th>
      <th>标题单元格</th>
      <th>标题单元格</th>
    </tr>
  </thead>
  <!-- tbody 表格主体 -->
  <tbody>
    <!-- tr 行 table row -->
    <tr>
      <!-- colspan 跨列合并单元格 -->
      <td colspan="2">单元格</td>
      <!-- rowspan 跨行合并单元格 -->
      <td rowspan="2">单元格</td>
    </tr>
    <tr>
      <td>单元格</td>
      <td>单元格</td>
    </tr>
  </tbody>
  <!-- tfoot 表尾 -->
  <tfoot>
    <tr>
      <td>单元格</td>
      <td>单元格</td>
      <th>标题单元格</th>
    </tr>
  </tfoot>
</table>
```

:::

<!-- #endregion demo -->
